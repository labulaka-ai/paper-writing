# paper-writing · 学术论文写作 Skill

一个供 AI agent（Claude Code 及兼容的 skill 运行时）使用的**学术论文分节写作与改稿 skill**：写或改 Introduction / Methodology / Results / Discussion / Abstract 任一节时，它先立「主张—证据」脊柱，再按每节的**功能模块**施工、用**语言力学**校准每一句的时态与情态，最后过**投稿前闸门**才允许报「可投」。

它不是提示词合集，而是一套带裁决规则的写作流程：多个方法来源互相冲突时听谁的、主张写多强由证据等级决定而不是由语气决定——这些都写死在流程里。

> **English summary.** A skill for AI agents to draft and revise academic papers section by section. Backbone: the "functional modules + language mechanics" method (from the *Academic Training* series by the WeChat account 小盐的世界）, reinforced by ARS (CARS model, abstract components, integrity gates), nature-writing (section cards, ML/CV variants), and ARIS (venue templates, cross-model review). Highlights: a claim–evidence spine with per-claim evidence grades (E1–E4), a **hedging budget** that prevents over-defensive writing, a two-stage figure workflow (plot-is-all-you-need for chart selection, figures4papers for publication-grade styling), and a pre-submission gate checklist including citation verification and an anti-over-defense audit.

---

## 为什么做这个

让通用大模型直接写论文，通病很稳定：

- **结构拼凑**：每节都像那么回事，但引言的主张在结果里没有证据、各节的研究问题各说一版；
- **语气校准失真**：要么 overclaim（把 `consistent with` 写成 `demonstrates`），要么**过度防御**——测出来的事实也加 `might`，一个句子叠三层弱化，贡献先自己贬一遍，审稿人还没挑，自己先把主张说没了；
- **引用不可信**：凭记忆生成的参考文献、挂错主张的引用；
- **语言细节失控**：时态乱跳分不清自他工作、冠词改了句意、`may not` 与 `cannot` 混用。

这个 skill 就是针对这四类病做的：用流程和闸门把它们堵在交付之前。

## 设计思想：一个主干，多路补强，冲突有裁决

| 来源 | 在本 skill 中的角色 |
|---|---|
| 「小盐的世界」《学术训练》五篇（Introduction / Methodology / Results / Discussion / Abstract） | **主干**：每节的「功能模块＋写作流程」与全部「语言力学」工具（时态语义、情态动词真值度、弱化策略、连接词、冠词、副词位置、被动语态分节规则）。该方法经一线导师认可，是本 skill 的骨架 |
| ARS（Academic Research Skills） | 结构补强：CARS 引言三步、摘要 5 组件、完整性闸门、venue 披露政策 |
| nature-writing | 结构补强：分节结构卡、证据阶梯、ML/CV 变体（方法型引言、摘要变体等） |
| ARIS | 流程补强：会议模板与页数口径、跨模型评审、写作质量五遍自查 |
| plot-is-all-you-need ＋ figures4papers | 绘图：前者管选型（看图库挑布局与配色），后者管顶刊规范出图。**均为外部依赖，不随本仓库分发**，见 `references/figures.md` |

**裁决规则**：来源冲突时以主干（导师法）为准。例如 ARIS 主张「校准但别弱化」，导师法主张弱化按证据强度分级——执行导师法，冲突点在使用时注明。

## 工作流总览

**第 0 步 · 先立脊柱，再动笔。** 产出一页 `PAPER_PLAN`：一句话贡献、主张—证据图（每条主张 ↔ 证据 ↔ 图表编号 ↔ **证据等级**）、gap 陈述（必须被文献综述许可，不许凭空制造）、按 venue 选定的结构模型与字数预算。

**第 1 步 · 分节写作，每节过四步。** 写作顺序：Methodology → Results → Discussion → Introduction → Abstract（摘要最后写）。每一节都走：①功能模块（导师法）→ ②结构卡（按 venue 选 ARS/nature 变体）→ ③语言力学检查 → ④本节自检清单。交付分节稿时必须附自检结果，不许只交正文。

**第 2 步 · 绘图配合。** 图在 Results 写作之前定稿大半：先选型、后规范，文字跟着定稿的图走。

**第 3 步 · 投稿前闸门。** 六道闸门（＋一道防御审计）逐项过，任何一项不过不许报「可投」；大改之后回归重跑。

## 核心机制详解

### 1. 证据等级 E1–E4：主张强度由证据决定

每条主张在 `PAPER_PLAN` 阶段就定级，它同时是第 2 节「弱化预算」的计价单位：

| 等级 | 含义 |
|---|---|
| E1 | 本文直接测量 / 观测到 |
| E2 | 多实验交叉或消融支撑的强推断 |
| E3 | 单一或间接证据的弱推断 |
| E4 | 猜想 / 外推到证据范围之外 |

### 2. 弱化预算制：防过度防御（本 skill 的原创机制）

弱化（hedging）是按证据付的账，不是免费保险。匹配是双向的：证据弱而语气强是 overclaim，证据强而语气弱是过度防御，同样是失真。规则写死在 `references/language-mechanics.md` §3：

| 证据等级 | 弱化预算 |
|---|---|
| E1 | **0 层**：直陈，不许 `may / might / suggest` |
| E2 | ≤1 层 |
| E3 | 1–2 层 |
| E4 | 必须弱化，并明说这是推测 |

配套五条硬规则：

- **单句上限**：一句话最多一个弱化装置；`suggest + may + appears` 式叠加只许出现在 E4 主张上；
- **事实句禁弱化**：测量数值、方法事实、直接观测的结果不许加弱化词——弱化只保护推断，不保护事实；
- **先写满格、再凭证据下调**：主张先按证据能支持的最强版本写；每次下调必须点名逼它下调的证据缺口（缺哪个实验、哪个对照），说不出缺口不许降；
- **贡献句不自降**：主张过强时正确的动作是收窄范围（把范围说精确），不是软化语气；
- **防御句式黑名单**：自贬开场（`although our method is simple...`）、`we only...`、自我贬低形容词、`it should be noted that...` 填充弱化，无证据支撑不许出现；真实局限只写进 Limitations 一处。

投稿前还要过**闸门 3B · 防御审计**（`references/gates.md`）：逐句标出全文弱化点、与证据等级逐条对账，并产出一张**弱化审计表**随稿交付。它与查 overclaim 的闸门 3 正好配成一对——一个查过强，一个查过弱。

### 3. 语言力学工具箱

全部出自主干方法，按工具归类在 `references/language-mechanics.md`，写任何一节的语言检查阶段逐项过：

- **时态语义表**：时态是态度与信息归属的标记——引前人结论用现在时还是过去时，等于告诉读者你把它当公认真理还是当时结论；标准操作（现在时）与自家操作（过去时）的切换处逐处检查；
- **情态动词真值度校准表**：六种功能（能力 / 可能性 / 概率 / 虚拟确定性 / 建议 / 必要性）逐词定权重，含最易混的几组：`may not`（可能不）≠ `cannot`（不可能）、`must` ＝「没有其他解释」、 `did not need to` ≠ `need not have`、`should`（给社区的建议）vs `will`（自家计划）；
- **弱化强度梯**：桥接动词梯（`suggest / indicate / imply` ＜ `demonstrate / prove`）、问题数据的标准动作（承认问题＋弱化影响＋转向正面）、升格禁令；
- **连接词分类与误用警告**：句首不用 `so`；`conversely / on the contrary` 蕴含一对一错，只是对比时用 `whereas / while`；`However / Although` 是引言 gap 的信号灯；
- **冠词 a / the**：改冠词即改句意——`may hide a connection`（可能有、看不清）vs `may hide the connection`（确有、被掩盖）；
- **副词位置三步法**：防「语法全对、意思全错」的歧义句；
- **被动语态分节规则＋替身主语**：引言禁用无施动者被动描述本文工作（用 `This paper presents...`），方法节被动是标准写法但必须配归属标记系统（`In this study, ...` / `As described by X, ...`）区分自他工作。

### 4. 分节功能模块速览

| 节 | 骨架 |
|---|---|
| Introduction | 漏斗四步：立领域重要性 → 背景与文献 → 指出 gap（须被综述许可、禁全称否定） → 介绍本文工作；补 CARS 三步与标题清单 |
| Methodology | 目标是**说服而非记录**：精确记录＋合理性辩护＋专业性展示；归属标记系统是本节生死线；每模块 Motivation / Mechanism / Evidence 三要素 |
| Results | 四模块菜单：开场引导 → 核心呈现（邀请看图＋只详述关键结果＋评价性语言定调） → 问题数据处理 → 收尾桥句（只到 `suggest / indicate / imply`）；出场顺序按证据阶梯，不按实验时间 |
| Discussion | 倒漏斗四模块：回顾 → 映射 → 成就与启示（先处理对手解释再推广） → 局限与未来；结论过 claim 检查 |
| Abstract | 最后写；两模型（结构化逐句 / 合并式）；摘要是「最短的证据链」，须在数据库中独立成立 |

### 5. 投稿前闸门（`references/gates.md`）

1. **引用抽验**：每条引用对原文核对，且必须支撑它所挂的那条主张；BibTeX 走核验链（DBLP → CrossRef），不许凭记忆生成，`[VERIFY]` 标记零残留；
2. **RQ 逐字一致**：研究问题在摘要/引言/方法/讨论中逐字对应，核心术语全文不许换名；
3. **主张—证据对齐**：每个实验都有论证职责，无职责的删、缩或移附录；过强主张收窄到证据支持的版本；
4. **3B 防御审计**：见上；
5. **反向提纲**：只读各段首句连读，应能组成连贯的缩小版全文；
6. **跨模型评审**：由另一个模型家族评审，分级处理意见；附写作质量五遍自查；
7. **Venue 模板/页数/披露**：模板、页数口径（ML 会议与 IEEE 不同）、引用命令、AI 使用披露落点按目标 venue 现行政策核对。

### 6. 绘图两阶段（`references/figures.md`）

先 **plot-is-all-you-need 选型**：从图库把候选图摆出来挑布局与配色（可自由组合），用自家数据演绎并与样例并排验证；后 **figures4papers 规范出图**：按出版级 house style 与矢量导出约定执行。再加导师法的图文配合四条（明确邀请看图、只详述关键结果、评价性语言定调、正文与图注数字不重复）与锚点图规矩（overview 图锚定方法节、主结果图与摘要共同决定审稿人去留）。

## 文件结构

```
paper-writing/
├── SKILL.md                        # 入口：总流程、调用指引、执行规则
├── README.md                       # 本文件
├── LICENSE
└── references/
    ├── introduction.md             # 引言：漏斗四步＋CARS＋方法型变体＋标题清单
    ├── methodology.md              # 方法：说服三目标＋归属标记＋模块三要素
    ├── results.md                  # 结果：四模块菜单＋证据阶梯＋统计纪律
    ├── discussion.md               # 讨论：倒漏斗四模块＋对手解释＋过claim检查
    ├── abstract.md                 # 摘要：两模型＋时态分工＋5 组件＋ML/CV 变体
    ├── language-mechanics.md       # 语言力学速查：时态/情态/弱化预算/连接词/冠词/副词/被动
    ├── figures.md                  # 绘图：选型＋规范＋图文配合＋锚点图
    └── gates.md                    # 投稿前闸门：引用抽验/RQ一致/对齐/防御审计/反向提纲/评审/venue
```

## 安装与使用

把本仓库克隆或复制到你的 agent 的 skills 目录（例如 Claude Code 的 `~/.claude/skills/paper-writing/`，或你的运行时约定的 skills 路径），保持 `SKILL.md` 与 `references/` 的相对结构不变即可。

触发示例（中英文均可）：

- 「帮我改一下这篇的 Introduction，gap 感觉立不住」
- 「方法部分怎么结构化？这是我的实验记录」
- 「摘要太长了，帮我压到 250 词以内」
- 「投稿前帮我过一遍闸门」/「给这稿做一次防御审计」
- 「这个结果该画什么图？」→ 会转入绘图两阶段（需另行安装两个配套 skill）

适用：CVPR / ICCV / NeurIPS / ICML 等会议稿与期刊稿的写作与改稿。**不适用**：公众号解读、科普长文等内容稿——那是另一种文体，本 skill 的主张—证据纪律会过紧。

## 来源、致谢与边界

- 本 skill 的方法骨架提炼自公众号「小盐的世界」《学术训练》系列五篇（「功能模块＋语言力学」法），谨此致谢；文中例句为教学短例。本仓库**不包含**该系列的原文复制，细节请回原系列阅读。
- 结构与流程补强分别来自 ARS、nature-writing、ARIS 三套开源工作，引用处均在各 reference 文件内注明来源。
- 绘图依赖的 figures4papers 为 CC BY-NC 许可：本仓库只引用其设计规范、**不包含**其任何代码或脚本；plot-is-all-you-need 图库中的论文图只可参考版式与配色，不可转载。
- 本 skill 给出的是写作流程与检查标准，不替代领域判断与实验本身；引用核验、venue 政策等时效信息以投稿时的官方原文为准。

## 验证状态

作者在自家论文工作流中实际使用（方法主干 2026-10 定版）。两点如实说明：

- **弱化预算制与防御审计为 2026-10-10 新增机制**，已写入流程与闸门，其全程效果待第一篇完整稿件跑通后验证，本节届时更新；
- 各分节手册中的结构补强（ARS / nature / ARIS）为多源综合，与主干冲突时的裁决规则见上文。

## License

MIT，见 `LICENSE`。方法来源的致谢义务见上一节——如果你分发或改编本 skill，请保留来源说明。
