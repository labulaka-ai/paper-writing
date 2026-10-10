# 语言力学速查（跨节共用）

全部规则出自「功能模块＋语言力学」法，按工具归类；标注了主要适用节。写任何一节的「语言检查」阶段打开本表逐项过。

## 1. 时态语义表

时态不只是语法，是态度与信息归属的标记：改变时态，就改变读者对结论可靠性的认知。

| 场景 | 时态 | 出处 |
|---|---|---|
| 引用他人研究，你视之为公认真理 | 一般现在时 | Introduction |
| 引用他人研究，仅是其当时的结论 | 一般过去时 | Introduction |
| 公认的标准操作 / 通用程序 | 一般现在时 | Methodology |
| 自己实际做的操作 | 一般过去时 | Methodology |
| 本文做什么、包含什么 | 一般现在时 | Abstract |
| 实际操作的方法论（摘要中） | 一般过去时 | Abstract |
| 结果，想升格为事实/真理 | 一般现在时 | Abstract |
| 结果，仅是本次实验的观测 | 一般过去时 | Abstract |
| 成就 | 现在完成时或现在时 | Abstract |
| 应用 | 一般现在时 | Abstract |
| 回顾方法论或结果（`was used / is used / has been used` 皆可） | 过去时 / 现在时 / 现在完成时 | Discussion |
| Results 正文报告观察 | 以过去时为主 | Results |

**切换纪律**（Methodology）：在「标准操作（现在时）」与「自己操作（过去时）」之间切换时，每次切换刻意检查时态是否变化；只靠时态不够时，叠加归属标记词（见 §7）。

## 2. 情态动词真值度校准表

情态动词的核心功能是调整句子的「真值度」（truth value）——你对某个陈述的确定程度。六种功能：能力（ability/capability）、可能性（possibility/options）、概率（probability/expectation）、虚拟确定性（virtual certainty）、建议（advice/recommendation）、必要性（necessity）。按证据强度精确选词。

**能力**
- `can` 只有一般现在式与过去式（could）两种时态；需要其他时态时切换为 `be capable of` 或 `be able to`（如 `It is believed that this software will eventually be capable of distinguishing...`）。
- `could`（一般能力）≠ `was able to`（特定事件、特定场合的能力）。
- 「本可以但没做」用 `could have done`（`If we had extended the time period we could have produced more crystals.`）。
- 过去式否定**不能**用 could not have 或 cannot have 表能力——它们属于虚拟确定性（表示「不可能」）。

**可能性**
- `may well` ＝很有可能（`This may well be due to leakage.`）；`might` 比 `may` 更弱、更不确定。
- **`can not`（两个词）≠ `cannot`（一个词）**：can not ＝「可能不」，用于如 `This can not only damage the sample, it may even destroy it completely.` 的结构；cannot ＝「不可能」，属于虚拟确定性而非简单否定。
- **`may not`（可能不）≠ `cannot`（不可能）**——Discussion 最易混的一组，强度有本质区别。

**概率/预期**
- `should` 在此类别表预期：`The material should remain stable.`（我预期它会稳定）。
- 过去式 `should have done` 在此类别指「在过去某个时间点之前，某事预期已经完成」，强调预期——与「建议」类别的同形用法区别见下。

**虚拟确定性**
- `must` ＝「没有其他解释」：表达的是逻辑推理而非直接观察到的证据；强度非常高，没有排除其他解释时不许用。
- 否定用 `cannot` / `could not`：属「几乎肯定不可能」的强度级别，与可能性类别中的 `may not`（也许不）有本质区别。
- `must not` ≠「不必要」：**must not ＝不被允许/禁止**。一般现在式的否定中绝对不能用 must not 表「不必要」；`have to` 在学术写作中不如 must 常用。

**建议**
- `should` 向他人建议；`ought to` 与 should 意思相同，但在学术写作中不如 should 常用。
- `should have done` ＝「本应该做但没做」（遗憾未发生）；`should not have done` ＝「本不该做但做了」（遗憾已发生）。
- 未来工作中的语气分工：**should ＝向他人/社区的建议；will ＝自家计划**。

**必要性（否定最易错）**
- 「不必要」的正确表达：`need not` / `do not need to` / `do not have to`。
- **`did not need to` ≠ `need not have`**：`We did not need to heat the valves` ＝我们不需要加热阀门（不说明是否真的加热了）；`We need not have heated the valves` ＝我们本不需要加热阀门的（隐含：已经加热了，但白费功夫）。

**组合纪律**：情态动词＋弱化策略组合使用是 Discussion 的常见模式（如 suggest + may + appears），用组合保护强主张不被轻易证伪；但组合后的总强度仍须与证据强度匹配。

## 3. 弱化（hedging）强度梯

科学写作需要避免被证伪，因此常用多种方式弱化因果陈述。可以组合多种弱化方式，但加得太多，句子会变得几乎没有实质内容——**根据实际证据的强度选择合适的弱化程度**。

- **桥接动词梯**（Results 收尾与过渡）：`suggest` / `indicate` / `imply`（暗示级，Results 只到此处）＜ `demonstrate` / `prove`（断言级，Results 不用，Discussion 中也要有设计撑腰）。
- **弱化词库**（问题数据与收敛表述）：slightly, somewhat, only approximate, a minor deficit, negligible, not significant, it should be noted that...
- **问题数据的标准动作**（Results）：承认问题＋弱化影响＋转向正面——`Although the average uncertainty slightly exceeds the 50% acceptability limit, nevertheless these results suggest that...`
- **评价性语言不是弱化**（Results）：`significantly lower`、`a striking difference was noted` 是给读者定调的评价，与弱化方向相反，两者不要混用抵消。
- **升格禁令**：不要把 `consistent with` 级别的发现升格为 `demonstrates` 的措辞；使用 `must`、`cannot`、`demonstrates` 或因果动词前，必须能点名许可这一强度的研究设计特征。

**弱化预算（防过度防御，2026-10-10 rui 定）**：弱化是按证据付的账，不是免费保险。匹配是双向的——证据弱而语气强是 overclaim，证据强而语气弱是过度防御，同样是失真。每条主张先在 PAPER_PLAN 里定证据等级，弱化层数不得超预算：

| 证据等级 | 含义 | 弱化预算 |
|---|---|---|
| E1 | 本文直接测量/观测到 | 0 层：直陈，不许 may / might / suggest |
| E2 | 多实验交叉/消融支撑的强推断 | ≤1 层 |
| E3 | 单一或间接证据的弱推断 | 1–2 层 |
| E4 | 猜想、外推到证据范围外 | 必须弱化，并明说这是推测 |

- **单句上限**：一句话最多一个弱化装置（一个情态动词、或一个桥接动词、或一个弱化副词）；`suggest + may + appears` 这类叠床架屋的组合只许出现在 E4 主张上，其余一律拆改。
- **事实句禁弱化**：测量数值、方法事实、定义、本文直接观测的结果——这些是事实不是推断，不许加弱化词。弱化只保护推断，不保护事实。
- **先写满格、再凭证据下调**：主张先按证据能支持的最强版本写出来，再逐条检查要不要下调；每次下调必须点名证据缺口（缺哪个实验、哪个对照），说不出缺口就不许降。一上来就写保守版，是过度防御的源头。
- **贡献句不自降**：摘要与引言的贡献陈述按证据等级写满。主张过强时正确的动作是收窄范围（把范围说精确），不是把语气说软——范围精确的主张用断言语气。
- **防御句式黑名单**（无证据支撑不许出现）：`although our method is simple/limited...` 式自贬开场、`we only...`、「初步的/简单的」式自我贬低、`it should be noted that...` 填充弱化。真实局限只写进 Limitations 一处（见 gates.md 闸门 3 与 3B）。

## 4. 连接词分类与误用警告

句号到下一个大写字母之间是「危险地带」：不用 signalling language 标明句子关系，读者很容易误解你的意图。

| 功能 | 词表 |
|---|---|
| 原因（Cause） | because, due to (the fact that), since, on account of, in view of, as |
| 结果（Result） | therefore, as a result, consequently, hence, which is why |
| 对比/差异（Contrast） | whereas, while, on the other hand, but, however, by contrast |
| 意外/转折（Unexpectedness） | Although, Even though, Though, However, Despite, In spite of, Regardless of, Notwithstanding, Nevertheless, however, yet, nonetheless, even so |
| 补充（Addition） | In addition, furthermore, moreover, apart from that/which, also, secondly, in the second place, what is more |

**误用警告**：
- **不要在句子开头使用 "so"**——非常不正式。（结果类用 therefore / as a result / consequently 等。）
- **谨慎使用 conversely 与 on the contrary**：它们不仅表示前后两者有区别，还强调两者是**一对一错**的；只是对比、并非对错时用 whereas / while / by contrast。
- **besides 比其他补充词都更用力**：要用在相当具有说服力的补充上，一般补充用 In addition / furthermore / moreover。
- **However 与 Although 是 gap 的信号灯**（Introduction）：走到「指出研究空白」一步时，这两个词能瞬间让读者明白铺垫结束、作者开始提问题——gap 处必须有转折词在场。

## 5. 冠词 a / the

用 **the**——当「你和读者都知道」指的是哪一个时：
- 逻辑上唯一、读者自然知道：`I bought a new computer but the keyboard was faulty.`（一提到电脑，键盘就是唯一且共知的部件）；前文提过的东西再提：`The samples were collected in brown glass bottles; the bottles were then sealed.`
- 只有一个人/一样东西可能存在：`Cairo is the capital of Egypt.`；`The opening was located in the centre of each mesh.`（每个网格只有一个中心）

用 **a**——当读者不知道，或具体哪一个不重要时：
- 读者不知道你具体指哪一个：`The subject then spoke to an interviewer.`
- 具体哪一个不重要：`A 35 ml brown glass bottle was used to store the liquid.`（重要的是规格，不是具体哪一只瓶子）

**改冠词即改句意**：
- `This effect may hide a connection between the two.` —— 可能有一个联系，但被掩盖了、我们看不清。
- `This effect may hide the connection between the two.` —— 确实有一个联系、而且被掩盖了：你确切知道这个联系存在，只是看不见。

下笔前先问：这个东西是「确切存在且双方共知」，还是「可能存在/任意一个」。

## 6. 副词位置

副词用不好，会造成语法上完全正确、但意思和你想表达的完全不同的错误（`The patient was discharged from hospital after being shot in the back with a 9mm gun.`——被枪击，还是用枪击背？`He gave a lecture about liver cancer at the hospital last January.`——讲座一月做的，还是一月病例的讲座？）。

应对三步法：
1. **副词修饰整个句子时，移到句首**：`Last January, he gave a lecture at the hospital.`；`As a result, the pressure dropped rapidly.`
2. **句中副词太多时，拆开写**：`Last January he gave a lecture at the hospital; his subject was liver cancer.`
3. **「with＋名词」结构容易歧义时，重写句子**：不写 `Look at that dog with one eye`（用一只眼看，还是一只眼的狗？），写 `Look at that dog that has one eye.`

核心原则：**副词位置放错，读者就会误解。如果一句话读起来可能产生歧义，就拆成两句，或者把副词移到句首。保证清晰永远是第一优先级。**

## 7. 被动语态分节规则 ＋ 替身主语 ＋ We 的用法

被动语态的使用率因节而异（本法总规则）：

| 节 | 规则 |
|---|---|
| Introduction | **避开无施动者被动描述本文工作**。引言必须严格区分「前人贡献」与「本文工作」，agentless passive（如 `X is presented`、`The data were analyzed...`）会让读者分不清是谁做的，造成混乱。用替身主语改主动（见下）。 |
| Methodology | **被动是标准写法**（如 was measured, was added），不带 by us / by me / by researchers；但必须配归属标记系统区分自他工作：自己的工作加 `In this study, ...` / `for this study` / `in our laboratory`；他人的工作加 `As described by X, ...`。 |
| Results | 无施动者被动常见且是标准写法（如 was measured, was added）。 |
| 全节通用 | 学术写作不用 "I" 作主语。 |

**替身主语**（引言描述本文工作的推荐写法——主动语态，主语指代论文本身）：
- `This paper presents a set of criteria...`
- `The present study describes the preparation of...`
- 反例（不推荐）：`A set of criteria is presented...`（谁呈现的？不清楚！）

**We 的用法**：
- `We` 只指自己的研究团队：`We have developed...`
- 泛指「人们普遍认为」不许用 We：不写 `We know that...`，写 `It is known/thought that...`（用 "It" 结构）。

**段落纪律**（本法，跨节通用）：一段只讲一个核心观点；每段第一句是主题句，后文围绕它展开。写完初稿后只读各段首句——连起来应能组成一个连贯的缩小版文本（此即 gates.md 反向提纲的本法版本）。

<!-- 时空AI深水区 · Spatiotemporal AI Deep Dive — Ruixue Han (@labulaka-ai) -->
