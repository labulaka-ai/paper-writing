# 绘图：选型＋规范＋Results 图文配合

绘图分两个阶段，顺序固定：**先选型（plot-is-all-you-need），后规范出图（figures4papers / scientific-figure-making）**。图在 Results 写作之前定稿大半——先图后文，文字跟着定稿的图走（见下「图文配合」）。

## 阶段一 · 选型：plot-is-all-you-need

解决「这个数据该画成什么图」的问题，不要用文字硬描述需求：

1. 从技能自带图库中把候选图摆出来，挑**布局**与**配色**——两者可自由组合（A 的布局＋C 的配色）。
2. 选型维度：数据形态（趋势/对照/分布/多面板）、论证职责（这张图要证明 PAPER_PLAN 里的哪条主张）、读者一眼要读出的对比。
3. 用自家数据照选定样式画出来，**与样例并排验证**再定稿；不合意就换候选，不要在错的图型上修修补补。
4. 图库持续维护：新图型入图库时配鉴赏卡（什么数据适合、什么不适合），去重、删过时样式。

> 使用注意：图库里的论文图只可参考版式与配色，不可转载原图。

配套 skill（需另行安装，不随本仓库分发）：**plot-is-all-you-need**（作者 liouhai；触发说法：「这个数据怎么画好看」「帮我出张图」「想换配色或版式」等）。

## 阶段二 · 规范出图：figures4papers（scientific-figure-making）

解决「按顶刊规范把图出对」的问题，覆盖 publication-ready 的 matplotlib 图：柱状、趋势、散点、热图与多面板布局。

- 按该技能的 house style 执行：字体、配色、spine、图例等出版级规范，并按其 print/vector 导出约定出 PDF/SVG。
- 不适用范围（该技能自述）：交互式仪表盘、探索性草图、主导性的 3D 或地理制图、Illustrator/Figma 优先的信息图工作流——这类需求回到阶段一选型或自家其他管线，不要硬套。
- 配套 skill（需另行安装，不随本仓库分发）：**figures4papers** 的 scientific-figure-making。

> 使用注意：figures4papers 许可为 CC BY-NC——学它的设计规范、用自家代码实现没有问题；把它的脚本搬进收费交付物不行（自家论文自用不受此限）。

## Results 图文配合（本法为主）

图定稿后，Results 的文字按本法与图配合，四条硬规则：

1. **明确邀请读者看图**：不能假设读者会自动去看图。每幅被讨论的图表都要有邀请句：`Figure 1 shows the results...` / `As can be seen in Fig. 1...` / `The results are summarized in Table 1...`（详见 results.md 模块 2a）。
2. **只详述关键结果**：图表里的结果不平均用力——选重要的、典型的、特别有趣的详述；你详述哪个，读者就认为哪个重要。详述对象应与 PAPER_PLAN 的主打结果一致。
3. **评价性语言定调**：图给数据，文字给解读。同图写 `the two curves are very similar` 读者聚焦相似，写 `noticeably different` 读者聚焦差异——图注与正文的评价词必须与本文主张一致，不要无意中替对手结论定调。
4. **数字不重复**：同一批效应量、区间、P 值不要在正文与图注里重复报；正文讲关键数字与解读，图注讲图的结构与读法，分工写明。

## 锚点图（ML/CV 惯例）

- **Overview / pipeline 图**是 Methodology 的锚点（写前清单——「Overview figure 是否存在？它锚定全节」）：方法节动笔前先有此图，逐模块文字与图中模块一一对应。
- **Teaser / 主结果图**：审稿人按标题→摘要→图→引言跳读，第一张图与摘要共同决定去留；篇幅允许时主结果图进引言。此图的评价性图注按上面第 3 条定调。
- 图序按论证排列（证据阶梯：建立现象→压力测试→排除替代→拓宽→解释→设界，见 results.md 的 补强），不按实验发生的时间顺序排图。

<!-- 时空AI深水区 · Spatiotemporal AI Deep Dive — Ruixue Han (@labulaka-ai) -->
