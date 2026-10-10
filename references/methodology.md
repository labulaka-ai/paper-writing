# Methodology

本节骨架为导师法（「小盐的世界」《学术训练》· Methodology 篇）。方法写作最常见的误解是「把实验记录下来就行」——导师法的出发点正相反。

## 功能模块与写作流程（导师法）

**总目标：说服，而非记录。** 优秀的方法论写作的深层目标是说服读者接受你的实验操作——只有读者认可了你的方法，他们才会接受你的结果和结论。每一处方法文字都要同时完成三件事：

1. **精确记录**（Precise Record）：提供足够详细的细节，让其他研究者能够完全复现（replicate）你的工作并得到相似结果。
2. **合理性辩护**（Justification）：不仅写「做了什么」，更写「为什么这样做」。读者不理解你的选择，就不会信任你的结果。
3. **专业性展示**（Professionalism）：通过语言展示你在操作中严谨、细心，即使出现问题也知道如何妥善处理。

**归属标记系统（本节生死线）**：方法节三大致命陷阱全在同一件事——**分不清「你的工作」和「他人的工作」**：

- **陷阱一：全文只用过去时被动、没有任何标记。** 通篇 `The samples were collected... The data were analyzed...`，读者会困惑：这是你做的，还是前人文献中的标准做法？解法：用明确的标记词区分——标记自己的工作：`In this study, the samples were collected...`；标记他人的工作：`As described by Brown (1999), the samples were collected...`
- **陷阱二：描述自己的操作与描述参考文献中的方法用了完全一样的时态。** 先写 `The samples were collected using the method of Smith (2010)`，再写 `The samples were then analyzed`，两者都是过去时被动，区别在哪里？解法：描述自己的操作时加上 `in our laboratory` 或 `for this study` 等标记性短语。
- **陷阱三：忘记在「公认的标准操作」和「自己操作」之间切换时态。** 标准操作用现在时（`The equipment is calibrated daily`），自己操作用过去时（`The samples were collected`），切换时态读者就能清晰区分；全程过去时则分不清。解法：每次从「描述标准操作」切换到「描述自己操作」时，刻意检查时态是否变化——最好还是用标记词。

**主语与语态**：学术写作中不用 "I" 作主语；方法节通常使用被动语态，不带 "by us"、"by me"、"by researchers"。

## 语言力学要点（导师法）

- **时态切换规则**：标准操作/通用程序＝现在时；自己的实际操作＝过去时；切换处逐处检查（详见陷阱三）。时态参考总表见 language-mechanics.md。
- **冠词 a/the 会改变句意**：
- 用 **the**：你和读者都知道指的是哪一个——(1) 逻辑上唯一、读者自然知道（如一提到电脑，`the keyboard` 就是唯一且共知的部件；前文提过的瓶子再提时用 `the bottles were then sealed`）；(2) 只有一个人/一样东西可能存在（`Cairo is the capital of Egypt`；`The opening was located in the centre of each mesh`——每个网格只有一个中心）。
- 用 **a**：读者不知道具体哪一个（`The subject then spoke to an interviewer`——哪个面试官不知道也不重要），或具体哪一个不重要（`A 35 ml brown glass bottle was used to store the liquid`——重要的是规格，不是具体哪一只瓶子）。
- **改冠词即改句意**：`This effect may hide a connection between the two.`（可能有一个联系，但被掩盖了、我们看不清）vs `This effect may hide the connection between the two.`（确实有一个联系、而且被掩盖了——你确切知道它存在，只是看不见）。下笔前先问自己：这个东西「确切存在且双方共知」，还是「可能存在/任意一个」。
- **副词位置防歧义**：副词放错，句子语法完全正确、意思却全变（`The patient was discharged from hospital after being shot in the back with a 9mm gun.`——到底是被枪击还是用枪击背？`He gave a lecture about liver cancer at the hospital last January.`——讲座是一月做的，还是一月病例的讲座？）。应对三步法：(1) 副词修饰整个句子时移到句首（`Last January, he gave a lecture at the hospital.`、`As a result, the pressure dropped rapidly.`）；(2) 句中副词太多就拆开写（`Last January he gave a lecture at the hospital; his subject was liver cancer.`）；(3)「with＋名词」结构易歧义时重写（不写 `Look at that dog with one eye`，写 `Look at that dog that has one eye`）。核心原则：**一句话读起来可能产生歧义，就拆成两句或把副词移到句首；保证清晰永远是第一优先级。**

## 结构补强（nature / ARIS，注明来源）

**nature-writing · 方法结构卡**（`static/fragments/section/method.md`）：

- 默认结构：`task formulation -> overview (pipeline / system / approach) -> per-module detail -> implementation notes -> assumptions and boundary`
- **每模块三要素**（The three-element pattern）：每个模块必须回答三件事——(1) **Motivation**：这个模块解决什么问题，为什么显而易见的替代方案不行；(2) **Mechanism**：模块实际做什么，细到同行可照着复现；(3) **Evidence / role**：这个模块如何贡献于整体结果（消融挂钩）。缺任何一个要素，模块读起来就是黑箱，必须标出缺口。——这一条与导师法的「合理性辩护」正好互补：导师法要求为选择辩护，nature 卡把辩护定位到每个模块的 Motivation 槽位。
- **写前清单**：Task formulation（输入、输出、范围）；Overview figure / pipeline diagram 是否存在（它锚定全节）；记号只定义一次且全篇一致；复现范围（代码、权重、数据——什么会公开）。
- **禁用模糊短语**（Never leave）：`under standard conditions`、`using routine methods`、`data were analyzed statistically`、`the method was validated`、`samples were randomly assigned`（不说明如何随机）——一律换成实际的、可复现的信息。这一条是导师法「精确记录」的负面清单版。

**ARIS `paper-write` §3 清单**：

- 记号在节首尽早定义（共享记号文件，如 math_commands.tex，全篇统一）
- 形式化陈述用 definition / theorem 等环境；理论稿在正文放关键结果的证明梗概、完整证明入附录，并给「先前界 vs 本文界」对比表
- 适用时给算法伪代码（algorithm2e 或 algorithmic）
- 目标篇幅 1.5–2 页（会议稿口径）

## ML/CV 与 venue 注记

- **方法节的图锚**：ML/CV 稿的 overview/pipeline 图是本节的锚点（nature 清单），图的选型与规范走 figures.md；图未定稿不要先写模块细节文字，图文容易脱节。
- **模块写作顺序**：按 nature 默认结构先 task formulation 把问题形式化（输入/输出/范围），再 overview 让读者拿到全景，最后逐模块按三要素展开；`assumptions and boundary` 收尾，不要散落在各模块里各说一半。
- **页数与引用风格**（ARIS）：CVPR/ICLR/NeurIPS/ICML 等 ML 会议正文页数计到 Conclusion 结束、参考文献与附录不计；引用用 natbib 的 `\citep{}` / `\citet{}`，与 IEEE 的 `\cite{}` 绝不混用。IEEE venue 参考文献计入页数。
- **复现性声明的落点**：数据集、代码、权重的公开范围要在本节或 venue 要求的 reproducibility 位置交代清楚，与 nature 写前清单的 reproducibility scope 对齐，不要只在附录里含糊带过。

## 本节自检清单

- [] 三件事齐：每处操作都有可复现的细节（精确记录）、关键选择有「为什么」（合理性辩护）、问题处理显得有掌控（专业性展示）
- [] 全文搜被动句：凡「自己的工作」都带 In this study / for this study / in our laboratory 等标记；凡「他人的方法」都带 As described by X 等标记
- [] 标准操作（现在时）与自己操作（过去时）的每次切换处都检查过时态
- [] 无 "I" 作主语；被动不带 by us / by me
- [] 逐个冠词回查：the 处确为双方共知/唯一，a 处确为任意/未知；重点复查 may hide a/the connection 这一类「冠词改句意」的句子
- [] 逐句读副词：时间/方式状语位置无歧义；拿不准的已拆句或移句首；with＋名词结构已排查
- [] （nature）每个模块 Motivation / Mechanism / Evidence 三要素齐，缺项已标出并补齐
- [] （nature）禁用模糊短语全文零残留（standard conditions / routine methods / analyzed statistically / was validated 等）
- [] 记号只定义一次、全篇一致；overview 图与文字模块一一对应
