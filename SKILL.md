---
name: paper-writing
description: >-
  学术论文分节写作与改稿：按导师认可的「功能模块＋语言力学」法（公众号「小盐的世界」《学术训练》五篇）为骨架，
  ARS 的 CARS 模型与摘要 5 组件、nature-writing 的分节结构卡与 ML/CV 变体、ARIS 的会议模板与评审流程作补强，
  绘图走 plot-is-all-you-need 选型＋figures4papers 规范。触发场景：写或改论文的
  Introduction / Methodology / Results / Discussion / Abstract 任一节；问「引言怎么写」「方法部分怎么结构化」
  「摘要怎么压缩」；投稿前自检、模拟审稿、引用核查；适用 CVPR / ICCV / NeurIPS / ICML 等会议稿与期刊稿。
  不用于公众号解读文章写作（那是内容稿，不是论文本体）。
---

# Paper Writing（自家论文写作 · 组合版）

方法主干是导师认可的「功能模块＋语言力学」法：每节先定**功能模块与写作流程**，再配**语言工具**（时态、情态动词、连接词、冠词、副词位置、弱化策略）。ARS、nature-writing、ARIS 只作结构补强；来源冲突时以导师法为准。

## 总流程

### 第 0 步：先立主张-证据脊柱，再动笔

结构是骨架，主张与证据的对齐才是脊柱。开写前先产出一页 PAPER_PLAN：

- 一句话贡献（one-sentence contribution）：全文所有节都要能回指它
- 主张-证据图：每条主张 ↔ 支撑证据 ↔ 对应图表编号 ↔ **证据等级 E1–E4**（E1 本文直接测量/观测；E2 多实验交叉或消融支撑的强推断；E3 单一或间接证据的弱推断；E4 猜想/外推）。证据等级是弱化预算的依据，见 references/language-mechanics.md §3 与 gates.md 闸门 3B
- gap 陈述：必须被文献综述许可，不许凭空制造（见 references/introduction.md 的 CARS 纪律）
- 选定结构模型与字数预算（ARS 结构模式）：IMRaD 6000 词示例为 Intro 15% / Lit 25% / Method 15% / Results 20% / Discussion 20% / Conclusion 5%；会议短稿 3000 词示例为 Intro 15% / Related 20% / Method 20% / Results 25% / Discussion 12% / Conclusion 8%。venue 的硬性页数/字数限制永远优先

### 第 1 步：分节写作，每节过四步

写作顺序建议：Methodology → Results → Discussion → Introduction → Abstract（摘要最后写，导师法与 nature 卡一致）。每一节都走同一套四步：

1. **功能模块**（导师法）：打开对应节的 reference，先按模块清单列出本节要完成的每个功能，逐模块写
2. **结构卡**（补强）：同一 reference 内的 ARS / nature 结构卡按 venue 与论文类型选变体（如方法型论文的引言变体、摘要的 ML/CV 变体）
3. **语言力学**：对照 references/language-mechanics.md 检查本节的时态、情态、弱化、连接词、冠词、副词位置、被动语态分节规则
4. **闸门**：跑完该节文末的自检清单；全文成稿后统一过 references/gates.md

### 第 2 步：绘图配合

图在 Results 写作之前定稿大半。调用顺序与图文配合规范见 references/figures.md：先 plot-is-all-you-need 选型，后 figures4papers 规范出图。

### 第 3 步：投稿前闸门

references/gates.md 全表逐项过：引用抽验、RQ 逐字一致、主张-证据对齐、反向提纲、跨模型评审、venue 模板/页数/披露。任何一项不过，不许报「可投」。

## References 调用指引

| 文件 | 何时打开 |
|---|---|
| references/introduction.md | 写/改引言、标题；漏斗四步（导师法）＋CARS 三步（ARS）＋方法型引言变体（nature） |
| references/methodology.md | 写/改方法节；说服三目标与归属标记（导师法）＋模块三要素与禁用模糊词（nature）＋会议页数与记号规范（ARIS） |
| references/results.md | 写/改结果节；四模块菜单与评价性语言（导师法）＋证据阶梯（nature） |
| references/discussion.md | 写/改讨论与结论；倒漏斗四模块与情态校准（导师法）＋对手解释与结论过claim检查（nature/ARIS） |
| references/abstract.md | 最后写摘要；两模型与时态分工（导师法）＋5 组件（ARS）＋ML/CV 变体（nature）＋5 段流（ARIS） |
| references/language-mechanics.md | 任何一节的语言检查阶段必查：时态语义、情态真值度、弱化梯、连接词、冠词、副词、被动分节规则、替身主语 |
| references/figures.md | 定图、改图、写图注、Results 图文配合时 |
| references/gates.md | 全文成稿后、投稿前；以及任何一次大改之后的回归检查 |

## Operating Rules

1. 导师法优先：ARS/nature/ARIS 的建议与导师法冲突时，执行导师法，并在交付说明中注明冲突点。
2. 不编造：Methods 只写材料中真实记录的操作（导师法「精确记录」）；gap 不许凭空制造（ARS：gap 必须被综述许可）；引用不许凭记忆生成（见 gates.md 的核验链）。
3. 主张强度不得超过证据：过强的主张先收窄到证据支持的版本，而不是换个柔和的同义词（ARIS 纪律，与导师法「弱化程度与证据强度匹配」同向时以导师法的弱化工具执行）。
4. 摘要最后写；摘要只许出现正文已有的内容（导师法）。
5. 每次交付分节稿时，附上该节自检清单的逐项结果，不许只交正文不交自检。
6. 防过度防御（弱化预算制）：弱化层数不得超过主张证据等级的预算（E1 零弱化、E2 ≤1 层、E3 1–2 层、E4 必须弱化并标明推测）；事实与直接观测句不许弱化；下调主张语气必须点名逼它下调的证据缺口，无名理由不许降。细则见 references/language-mechanics.md §3，投稿前过 gates.md 闸门 3B 并附弱化审计表。
