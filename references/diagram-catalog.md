# Mermaid 图表选择目录

按“读者需要看清什么关系”选图；同一问题可以用不同视角分图说明，不必把所有信息塞进一张流程图。

## 范围与兼容性

- 核对日期：2026-10-30。[Pele examples](https://pele.run/examples) 列出下述 **32 类**；分类页还展示了大量语法、布局、边线和窄屏变体。下表覆盖全部类型，并提炼与讲解有关的主要变体，不声称逐个执行过站内示例。
- “活用所有 examples”指掌握完整类型及其变体、遇到合适问题能选用；不要求一次回答展示所有类型，也不要求为了覆盖率轮流用图。
- [Pele 兼容页](https://pele.run/compatibility) 当前以 Mermaid 12.1.0 内置类型为目标。新增类型不能一概视为 Pele 私有语法；不同宿主的实际版本、构建与插件决定哪些类型可用。
- 表中关键字来自当前兼容页及分类页。多个关键字是该站列出的别名或子类型，不表示它们在所有宿主都可互换。`-beta`、新增和高级语法使用前确认宿主支持；未知时保留关系语义，改用基本 flowchart、sequence、state 或表格。不要仅修改首行来“转换”一种语法。
- 这里只保存选图规则与可查的示例索引。选定类型后，按需查看对应官方子页的具体语法；不用每次加载全部示例。

## 1. 算法、运行过程与协作

| 类型与官方示例 | 已核对的关键字 | 最适合回答什么 | 主要变体与误用边界 |
| --- | --- | --- | --- |
| [Flowchart 流程图](https://pele.run/examples/flowchart) | `flowchart`、`graph` | 算法分支、数据变换、依赖与反馈回路 | 条件、循环、自环、扇入扇出、并行边、子图和嵌套；可选 TD/BT/LR/RL。先说明箭头是控制、数据还是依赖，不能以排版顺序冒充真实执行顺序。 |
| [Sequence 时序图](https://pele.run/examples/sequence) | `sequenceDiagram` | 谁在何时调用谁、异步返回、消息交换、跨线程等待 | 参与者别名与类型、激活区间、分组、条件/循环/并行/关键区段、注释；只有实际存在的并发或等待才画出来，不能把调用关系自动解释成耗时比例。 |
| [State 状态图](https://pele.run/examples/state) | `stateDiagram-v2`、`stateDiagram` | 一个对象的生命周期、事件触发和合法迁移 | 起止、复合状态、选择、分叉/汇合、并发状态、注释；状态是可持续的条件，不是随意把函数步骤改名。 |
| [Swimlane 泳道图](https://pele.run/examples/swimlane) | `swimlane-beta` | 每步归谁负责、流程如何跨角色或部门交接 | 命名泳道、方向、跨泳道边、重试和分支；泳道表达责任归属，不等于真实线程或时间比例。 |
| [Agentflow 智能体流程](https://pele.run/examples/agentflow) | `agentflow-beta` | Agent 如何分工、使用工具、交接输入输出并处理失败 | 嵌套 flow、task/tool/input/decision/action/refdoc、connector、元数据、控制/引用/失败边；工具和智能体要区分，不能把声明的契约当成运行时已保证。 |
| [Event modeling 事件建模](https://pele.run/examples/eventmodeling) | `eventmodeling` | 命令如何形成业务事件、事件如何影响视图与可见信息 | 时间框、引用框、UI/命令/事件/视图、跨域引用；关注可观察信息演化，不用于代替每条底层指令或完整函数调用栈。 |

## 2. 结构、接口与系统边界

| 类型与官方示例 | 已核对的关键字 | 最适合回答什么 | 主要变体与误用边界 |
| --- | --- | --- | --- |
| [Block 块图](https://pele.run/examples/block) | `block`、`block-beta` | 如何组成、嵌套或排列模块，布局本身有什么意义 | 列数、跨列、空位、嵌套块、形状与块间连接；适合手动表达分层布局，不凭方块面积暗示真实内存大小或耗时。 |
| [C4 架构视图](https://pele.run/examples/c4) | `C4Context`、`C4Container`、`C4Component`、`C4Dynamic`、`C4Deployment` | 系统在谁的边界内、有哪些应用和组件、部署到哪里 | 依次选系统上下文、容器、组件、动态或部署视角；一张图保持同一抽象层。C4 的 Container 不是专指 Docker 容器。 |
| [Class 类图](https://pele.run/examples/class) | `classDiagram` | 类有哪些职责、接口、成员与静态关系 | 继承、实现、关联、依赖、聚合/组合、基数、泛型、命名空间、注释；组合意味着更强的拥有关系，不是“有一个指针”就能推定。 |
| [Entity relationship 实体关系图](https://pele.run/examples/er) | `erDiagram` | 数据实体怎样关联、键与基数是什么 | 属性、键、别名、可选性、一对多/多对多、识别关系、分组；按已知 schema 标注，不能从一次样例数据推定全局基数。 |
| [Architecture 架构连接图](https://pele.run/examples/architecture) | `architecture-beta` | 服务和基础设施如何连接、资源归属哪个组 | group/service、端点方向、junction、内置或外部图标；连通不自动表示执行顺序，外部图标需宿主提供解析器。 |
| [Packet 位字段图](https://pele.run/examples/packet) | `packet`、`packet-beta` | 协议或打包数据的每一位属于哪个字段 | 起止位、字段宽度、标题、跨行布局；先确认位数、偏移、顺序和单位，不从语言类型名猜 C++ 内存对齐或 GPU 格式。 |
| [Railroad 语法铁路图](https://pele.run/examples/railroad) | `railroad-beta`、`railroad-ebnf-beta`、`railroad-abnf-beta`、`railroad-peg-beta` | 一段输入怎样符合语法、哪些分支可选或重复 | 终结符/非终结符、串接、选择、可选、重复、递归引用；按 EBNF/ABNF/PEG 实际语义选择，不能把解析器运行流程当成文法。 |
| [Use case 用例图](https://pele.run/examples/usecase) | `usecase-beta` | 哪些角色通过系统完成哪些目标、功能边界在哪里 | actor、系统/包边界、包含/扩展、泛化、业务标注与注释；用例表示用户目标，不是 API 调用时序或页面跳转图。 |

## 3. 知识组织、集合与追溯

| 类型与官方示例 | 已核对的关键字 | 最适合回答什么 | 主要变体与误用边界 |
| --- | --- | --- | --- |
| [Mindmap 思维导图](https://pele.run/examples/mindmap) | `mindmap` | 一个概念包含哪些方面、知识如何分层 | 中心主题、多层分支、节点形状与文本样式；父子关系通常是分类或组成，不代表因果、调用或执行顺序。 |
| [Tree view 树视图](https://pele.run/examples/treeview) | `treeView-beta` | 目录、资源或组织怎样层层包含 | 缩进/树形输入、文件与目录、描述、图标、带引号名称；严格层级才能用，存在多父节点和交叉依赖时另补关系图。 |
| [Venn 集合图](https://pele.run/examples/venn) | `venn-beta` | 哪些能力/条件有交集、区别或包含关系 | 集合、交集标签、可选集合与交集数值；无数量时明确为概念示意，面积不能当成测量结果；复杂多集合关系通常更适合表格。 |
| [Requirement 需求图](https://pele.run/examples/requirement) | `requirementDiagram` | 要求如何分解、由什么满足、用什么验证 | 不同需求类型、元素、派生/包含/满足/验证/追溯关系、风险与验证方式；“计划验证”不能画成“已经验收通过”。 |

## 4. 数量、性能与比较

| 类型与官方示例 | 已核对的关键字 | 最适合回答什么 | 主要变体与误用边界 |
| --- | --- | --- | --- |
| [XY chart 坐标图](https://pele.run/examples/xychart) | `xychart`、`xychart-beta` | 数量怎样随输入变化、不同类别数值差多少 | 柱形、折线、多个序列、方向、坐标轴与标签；给单位和数据来源，理论曲线写清公式/假设，不把示意值称为实测性能。 |
| [Pie 饼图](https://pele.run/examples/pie) | `pie` | 同一整体由哪些互斥部分组成 | 标题、分类数值、显示数值；必须有共同分母和不重复计数的组成，不能用来画重叠功能覆盖率。 |
| [Sankey 桑基图](https://pele.run/examples/sankey) | `sankey`、`sankey-beta` | 同一种可计量资源从哪流到哪、怎样分配和损失 | 多级流、分流/汇流、CSV 转义、边宽；需要同口径数量，不能把带宽当任意重要程度，或拿普通函数调用次数假装资源守恒。 |
| [Treemap 矩形树图](https://pele.run/examples/treemap) | `treemap`、`treemap-beta` | 分层资源占用中谁占得最多 | 分类/子分类、叶节点数值、层级标签与颜色；面积必须对应明确数值，父节点汇总与叶节点不可重复累加。 |
| [Radar 雷达图](https://pele.run/examples/radar) | `radar-beta` | 多个对象在一套共同指标上有怎样的轮廓 | 多轴、多序列、轴别名与量程；先统一尺度与好坏方向，主观评分说明规则和依据，不能为画图临时编造分数。 |
| [Quadrant chart 四象限图](https://pele.run/examples/quadrant) | `quadrantChart` | 按两个有意义维度如何定位与取舍 | 两轴方向、象限标签、点位与样式；先定义两个轴。定性位置应标示为判断/示意，不用小数坐标制造测量精度。 |

## 5. 时间、版本、任务与体验

| 类型与官方示例 | 已核对的关键字 | 最适合回答什么 | 主要变体与误用边界 |
| --- | --- | --- | --- |
| [Gantt 甘特图](https://pele.run/examples/gantt) | `gantt` | 哪些任务何时进行、持续多久、先后依赖什么 | 分组、里程碑、状态、依赖、日期/时分格式、排除休息日；未知工期标为假设，不能把为了排版填写的日期当成交付承诺。 |
| [Git graph 版本图](https://pele.run/examples/git) | `gitGraph` | 提交如何分叉、合并和挑拣，分支策略如何运行 | commit/branch/checkout/merge/cherry-pick、标签、提交类型和方向；用来讲提交拓扑，工作目录、工作区和远端不是提交节点。 |
| [Kanban 看板](https://pele.run/examples/kanban) | `kanban` | 工作项分别处于哪个状态、由谁跟进 | 状态列、卡片、标签/负责人等元数据；表示任务分布，不代替任务依赖或完整排期。 |
| [Timeline 时间线](https://pele.run/examples/timeline) | `timeline` | 事件和技术演进按什么先后发生 | 分段、同时间多个事件、横向/纵向与样式；适合顺序和里程碑，不默认间距代表真实持续时长。 |
| [User journey 用户旅程](https://pele.run/examples/journey) | `journey` | 用户完成目标会经过哪些阶段、哪里体验困难 | 阶段、步骤、参与角色、体验评分；关注使用体验，评分需要访谈/观测/明确示意依据，不拿来替代技术调用流程。 |

## 6. 诊断与技术策略

| 类型与官方示例 | 已核对的关键字 | 最适合回答什么 | 主要变体与误用边界 |
| --- | --- | --- | --- |
| [Ishikawa 鱼骨图](https://pele.run/examples/ishikawa) | `ishikawa`、`ishikawa-beta` | 一个现象可能由哪些类别的因素造成 | 问题、原因类别、嵌套原因；区分假说与已证实原因，图上的分支不是因果证据。 |
| [Cynefin 复杂性框架](https://pele.run/examples/cynefin) | `cynefin-beta` | 不同问题应采用既有流程、专家分析、试探还是应急行动 | clear/complicated/complex/chaotic/confusion 五域、域间迁移、空框架；只在这一决策框架确有帮助时用，不把计算复杂度 O(n) 或工作量大小塞进来。 |
| [Wardley map 价值链地图](https://pele.run/examples/wardley) | `wardley-beta` | 围绕用户需求，哪些依赖应自研、采购或采用成熟能力 | 用户可见度、演进阶段、组件依赖、惯性、演进、采购策略、注释；解释轴和判断依据，不把横轴误读成日历时间或通用质量评分。 |

## 变体如何转化为讲解能力

- **分支、循环、反馈**：把触发条件、退出条件和反馈对象写在边上；只呈现与当前问题相关的路径。Flowchart 的形状、双向边和自环只是表达工具。
- **并行与同步**：时序图的并行区段、状态图的 fork/join、流程图的扇出不完全等价。说明哪些任务可同时运行、哪里必须等待，不能只画多个箭头就宣称并行。
- **分层与边界**：用子图、命名空间、复合状态或 C4 层次划出职责。需要放大时另画局部图，并保持符号和术语一致。
- **引用与依赖**：区分“调用”“包含”“拥有”“实现”“数据输入”“参考资料”。线型可辅助，准确的边标签与图例才是主要依据。
- **布局与样式**：Pele 的密集图、30 路扇入扇出、形状全集和边线路由案例主要展示渲染能力；讲解时应提炼共同结构、分组或拆图，不能照搬成阅读负担。
- **别名、标签与图标**：代码符号保持准确，用别名补充中文职责。装饰性图标、动画、HTML、链接和复杂配置只在宿主明确支持且任务需要时使用；优先简单标签。
- **数据、假设与证据**：数值图应可追溯到输入、测量或明确公式；概念图也要区分已知事实、推断和待验证关系。没有评分依据时使用定性表格，不为填满图形编数据。
- **增补表达**：结构由图承担，关键机制、推导、代码片段、限制和反例用文字补足。精确对照用表格，公式推导用数学表达；不要求所有内容都转为 Mermaid。

## 官方依据

- [Pele 图表目录](https://pele.run/examples)：完整分类、各子页编号示例，以及布局与窄屏变体。
- [Pele 兼容性](https://pele.run/compatibility)：目标 Mermaid 版本、关键字别名、外部插件限制、布局/样式/标签/数学/图标差异。Pele 的布局与 Mermaid 不必相同；Pele 的主题使用 CSS 变量，不能假定 Mermaid 主题配置生效。
- [Mermaid 图表语法](https://mermaid.js.org/intro/syntax-reference.html)：需要具体语法时查对应类型的官方说明。
- 新类型的原生支持可核对 [Agentflow](https://mermaid.js.org/syntax/agentflow.html)、[Cynefin](https://mermaid.js.org/syntax/cynefin)、[Event modeling](https://mermaid.js.org/syntax/eventmodeling.html) 和 [Use case](https://mermaid.js.org/syntax/usecase.html)。这些官方文档分别标出引入版本；仍以实际宿主支持为准。
