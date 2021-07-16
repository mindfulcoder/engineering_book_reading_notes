# Clean Agile

## 1.敏捷软件开发简介

### 1.1 敏捷的历史

可能从人类诞生就有了敏捷的概念，因为通过制定小目标、衡量每个目标的进展的工作方式是人类的直觉，把这种方式称为革命有点夸大其词。

在现代工业中，可能从第一台蒸汽机、第一座磨坊、第一台内燃机、第一架飞机的发明开始，人们就在使用我们今天称为“敏捷”的工作方式了。

在软件开发中，阿兰图灵在1936年写下的第一个程序时，他就是按照写小的步骤、频繁的测试的方式进行的。

在现代的敏捷软件开发诞生之前，在工业和制造业领域占据统治地位的方法论是“科学管理”。

科学管理采用的是一种自上而下，命令与控制的方式。管理者通过科学的手段确保完成目标需要的最佳流程被实施，并且具体指导下属遵照计划执行。换句话说，这是一种预先规划，详细实施的方式。

1970年代，科学管理被引入软件工程领域。科学管理在应付变更成本较大、需求清晰、目标确定的项目时非常成功。在此背景下，Winston  Royce写了一篇关于管理大型软件项目的论文，在他的论文中用到了下面的示意图：

![](.\image\waterfall.PNG)

因为这个图看起来很像是一个“瀑布”，所以这种软件开发方式被称为瀑布模型。瀑布模型是科学管理在软件开发领域的体现。

自1970年以后的30年间，瀑布模型是最主流的软件开发方式。

但是，瀑布模型总是失败：因为，无论如何细致的分析和设计软件，一到实现阶段总会面目全非；一旦遇到变化，无论前期考虑得如何周全，总会导致严重的延期。尽管一次又一次地失败，人们总是在执行上找原因，而不是在战略层面。因为人们也想不到更好的方法。

在1990年代，面向对象的程序设计语言逐渐兴起，面向对象设计、设计模式、XP逐渐被人们提起。在1995年，关于Scrum的论文被发表，从此有如开闸洪水，人们开始逐步抛弃瀑布模式。

Robert C Martin当时是一个C++的咨询顾问，他当时的想法是把面向对象程序设计语言和瀑布相结合，从而创建出一套新的软件开发流程。幸运的是，他后来遇到了Kent Beck，从Kent Beck那里他了解到了极限编程的基本思想。他越学习极限编程，越感兴趣，所以决定抛弃他自己最初的想法，拥抱极限编程。

在2000年的时候，Kent Beck邀请了很多来自极限编程流派和设计模式的流派的软件开发人员参加“极限编程领导者”会议。会上，Robert C Martin提出了创建一个关于极限编程的非营利性组织的设想，但是因为已经存在一个不受人喜欢的关于设计模式的类似组织，所以大家都不同意。伤心至极的Robert C Martin退出了会议，Martin Fowler也跟随退出，并商定两人单独谈一次。

Robert C Martin和Martin Fowler在Thought Works附近的咖啡店会面，他向Martin Fowler介绍了关于轻量级流程的想法，以及创建一个统一的宣言的建议。于是，Martin Fowler起草了一份参与者名单，邀请参与者来参与一次“轻量级流程峰会”。受邀者中有一位Alistair Cockburn正巧也准备举办类似的活动，所以他们决定将两次会议合二为一。会议的举办地点就定在盐湖城的雪鸟滑雪场。

### 1.2 雪鸟会议

总共有17名资深程序员决定出席这次会议。

一个小小的插曲是，17个人都中年白人男性，所以为了避免嫌疑，他们决定邀请知名的女程序员Agneta Jacobson出席，但是她最终还是没有到场。

17个参与者的根据观点分成5个主要的流派：

- **极限编程**： Kent Beck, Robert C Martin, James Grenning, Ward Cunningham, Ron Jeffries
- **Scrum**:  Ken Schwaber, Mike Beedle, Jeff Sutherland
- **Feature Driven Development**:  Jon Kern
- **Dynamic System Development Method**:   Arie van Bennekum
- **Crystal Family of Process：**  Alistair Cockburn

其他人不属于任何流派，各持自己的观点。

虽然Martin Fowler也是属于极限编程流派，但是他对于自我标榜的人总是持怀疑态度，所以他并没有明确表态。

经过一天的讨论后，在众人的围绕下，Martin Fowler在白板上写下了如下4句话：

> Individuals and interactions over processes and tools
> Working software over comprehensive documentation
> Customer collaboration over contract negotiation
> Responding to change over following a plan

与会者都同意者四句话，但是他们没有想到一个合适的名字来描述这是什么。Robert C Martin想叫它“轻量级流程”，不过其他人都反对。各种各样的名字都冒出来，最终有人提了“敏捷”这个词，因为当时军队里流行这个词。没人喜欢“敏捷”这个词，但是因为没有更好的选项，所以只好叫它“敏捷”。

会后的两周，他们又以这4条基本原则为基础，想出了12条具体原则。

这就是敏捷宣言的由来。

### 1.3 敏捷概览

如何管理软件项目呢？

一直以来有各种各样的方法论--当然，其中一些很糟糕。有些项目经理甚至认为有一个掌管软件项目的神，所以寄希望于祈祷和许愿。另外一些不信神的项目经理采用一些“激励”手段来保证进度，你可以想象一幅有皮鞭、铁链、油锅、惊涛骇浪、惨叫、悲惨的人在岩石上爬行的景象。

上述手段无一例外地都失败了。

**铁十字原理**

这些手段失败的原因就在于管理者不理解软件项目的基本运作原理。

铁十字原理：

> 如果质量好、开发快、成本低和按时完工位于一个十字架的4个端点，那么最多只能获得其中3个。

好的管理者理解四者之间必须进行妥协，所以驱使项目尽量符合四个目标，而不要求达到100%。

敏捷软件开发就是管理者与开发者共同达成这种目标的理论框架。但是这仍然取决于如何运作敏捷。

**墙上的图表**

敏捷软件开发团队产生各种各样的数据，管理者可以根据这些数据做出最佳决策。

![](.\image\team_velocity.PNG)

速率图能够帮助管理者知晓开发团队在一个迭代内能够完成多少个点数，从而预测下个迭代可以完成多少用户故事。

![](.\image\burning_down.PNG)

燃尽图可以帮助管理者判断里程碑是否能够在预期内达成。

将速率图和燃尽图挂在墙上是敏捷团队的重要目标。当然，有人会说，敏捷宣言里面就没有提过这两个图啊！

其实关键的不是图表，而是图表所提供的数据。

敏捷软件开发是一种基于反馈的软件开发方式。每周、每天、每小时、甚至是每分钟，敏捷团队都可以通过数据的反馈来进行调整。

如果没有数据，那么项目是无法被管理的。所以，无论你是真的把这两个图挂在墙上，还是采用其他方式，请确保管理层随时知道这些数据。

**软件项目最重要的事情**

对于软件项目而言，最重要的事情就是上线日期。

上线日期一旦决定，通常是无法更改的，因为其背后往往有业务上的原因。

但是，需求的范围又是难以冻结的。因为客户往往只清楚他们要解决的问题，而不明确他们需要什么样的软件。所以软件需求经常会变化，因为客户总是在重新思考与评估：新需求被添加进来，老需求被删除，用户界面每天都在变化......

这就是软件开发团队所面临的真实情况。

在软件开发的世界中，上线日期是总是固定的，而需求总是持续变化的。

**项目启动会议**

在瀑布模式下，一个典型的项目启动会议是这样的：

5月的某一天，大老板把软件开发人员叫到会议室。

“我们准备启动一个新项目 。” 老板说。“首先要明确的是，我们必须在11月上线。我现在还没有具体需求，我在几周内就会给你们。你们觉得需求分析需要花多长时间？”

开发人员面面相觑，没人想说话。有人小声说：“需求都没有啊......”

"假设你们有需求！" 老板咆哮道。“你们都是专家，我不需要你们给我精确的估计，我只需要做一个简单的计划。当然，如果时间超过2个月，那么我们就不启动这个项目。”

“两个月？” 有个开发人员小声说到。

“太好了，这就是我需要的答案！”老板说。“现在，你们觉得完成设计要花多少时间呢？”

会议室又一次陷入了沉默，考虑到距离11月还有6个月，所以有人小声说 ”两个月？“

”太好了，我也是这样想的。这样，我们还剩下2个月来做实现！感谢各位参会！“

**分析阶段**

一离开会议室，开发人员立刻开始分析。因为项目现在已经进入分析阶段，所以现在的干的都是“分析”。至于什么是分析，这很重要吗？

无论你看那一本关于关于软件分析设计的书，都没有人可以给“分析”下精确定义。“分析”可能是指需求细化的过程，也可能是指发现潜在需求的过程，也可能是创建底层数据模型或者对象模型......总之， “分析”就是分析师干的事情。

当然，也有一些显而易见的事情，比如项目的可行性、人力、上线日期、业务目标等。

分析阶段是项目的蜜月期，每个人都忙着上网、购物、见客户、开会、画一些好看的图......总之大家都很开心。

然后，奇迹发生了，到了7月1日开发人员宣布完成了“分析”。要不然还能怎么办呢？时间都用完了。

**设计阶段**

那就开始“设计”吧！哦，对了，什么是设计来着？

作为资深开发人员，我们对于设计有一点信心。软件设计就是将软件项目拆分成模块，定义模块间接口，以及模块之间的交互方式的过程。总的来说，我们期望通过制定一个切实可行的细节实施计划来优化整体计划。

当然，在这个阶段各种变化频繁发生。新功能被添加进来、老的功能被删除......以前分析过的又拿出来再分析，设计推倒重来......当然时间有限，所以有些事情就“特殊”处理了。

然后，奇迹发生了，到了9月1日开发人员宣布完成了“设计”。要不然还能怎么办呢？时间都用完了。

**实现阶段**

实现阶段到了。你们也知道，实现阶段要交付具体的软件，所以没法忽悠过去。

在实现阶段，开发人员都发疯似地写代码......写代码的人都知道前面4个月啥都没干。

当然了，需求仍然在变化，针对这些变化，开发人员不得不做重新的分析和设计。但是，没几个星期剩下了，所以怎么“快”就怎么来吧，谁还管细节呢！

此时，我们的代码和最初的设计已经关系不大了。不过，时间一分一秒地过去，谁还关心这些呢。

10月15日，突然有人问“上线日期是哪天来着？” 那一刻，所有的开发人员都意识到他们是不可能在11月1日上线的。所以，开发团队斗胆找到了业务干系人，说：“我们现在出了一点小小的问题......”

干系人愤怒了，“在分析阶段你们怎么不说呢？那个时候你们不是应该评估进度的可行性吗？在设计阶段你们怎么不说呢？有什么问题你们不是应该在那个阶段就发现吗？离上线还有两周，你来告诉我不能上线！&￥#@!&”

**死亡竞速阶段**

现在客户愤怒了，干系人愤怒了，压力巨大。团队开始拼命加班。团队中有人果断地离职了。一副地狱般的景象。

到了第二年3月，他们终于上线了一个部分满足业务需求的半成品。所有人都很郁闷。

开发团队拍着胸脯向用户保证，下次一定会做得更好：诸如分析会做得更细，设计会做得更好......做了一些其实开发心里完全没有把握的承诺。

**夸大其词吧？**

的确，以上的故事将发生在多个软件项目中的故事进行了拼接和放大。现实中，并非所有的瀑布项目都失败得那么惨，但是几乎所有的瀑布项目都或多或少地出了这些问题。

**更好的方式**

瀑布模型的想法很直接：分析问题、设计方案、实现。这个过程简单、直接、明显，但是却是错的。

敏捷的方式和上述故事完全不同，但是更加现实可行。

敏捷的项目起于分析，但是分析是贯穿整个流程的。

如下图，我们将时间分成一个个小小的迭代，每个迭代一两周时间。

![](.\image\sprint.PNG)

**初始迭代**

第一个迭代主要用于产出用户需要的功能列表--用户故事，也用于开发环境搭建、故事估算、初始计划制定。此时制定的初始计划只是对用户故事实现顺序的简单安排。此后，开发人员和架构师也根据用户故事简单搭建系统架构。

有些人会认为，敏捷的迭代只是一系列的小瀑布。其实不是这样的，迭代并没有本拆分为3个阶段，分析也不是只在迭代开始时才进行。在敏捷的每一个迭代中，开发用户故事、估算、计划和设计的过程永不停歇。

**敏捷产生数据**

在初始迭代中，到底能完成多少用户故事完全是拍脑袋想出来的，所以初始迭代到底能完成多少用户故事是不确定的。

但是，初始迭代完成后，根据实际情况，我们就获得了迭代速率的真实数据。利用这些真实数据，我们可以对计划进行修正。

随着迭代的进行，我们根据数据不停地进行修正，最终的计划就会越来越靠谱。

**愿望 V.S 管理**

敏捷的一个首要目标就是要放弃愿望，我们实践敏捷就是要在愿望干掉项目前干掉愿望。

愿望是项目杀手，因为愿望导致开发团队提供错误的进度信息进而误导管理者。当管理者问“进展如何”时，期望得到是准确答案，而不是“很好”，“很好”只是一种愿望。敏捷用数据说话，从而避免了“愿望”。

敏捷也不是越快越好。敏捷是关于如何尽早知道我们到底有多糟，从而即使做出管理决策。

最好的结果未必是管理者和干系人期望的结果。但是，最好的结果是经过努力以后，我们能够达到的最好状况。

**管理铁十字**

在敏捷项目管理中，项目经理可以更好地管理质量、速度、成本和按时上线之间的关系。

1. 延期：如果要延期，可以尽早告诉干系人到底要延期多久。
2. 加人：如果不能延期，则管理者可能尝试加人，但是加人未必会带来产能提升。
3. 降低质量：如果加人也不行，那么只能降低质量标准，但是大家都知道“要想走得快，就要走得稳”。
4. 改变范围：所以，最终能够妥协的是减少上线的需求范围。

**业务价值优先级**

如果你不想要用户告诉你，你们做的功能完全不是用户需要的，那么你就要让用户自己来决定实施功能的优先级。

以上的这些就简单概括了敏捷。

### 1.4 生命之环

Ron Jeffry 使用一个称为“生命之环”的图来描述极限编程的实践。

![](.\image\circle_of_life.PNG)

在敏捷的各种实践中，XP是定义最清楚、最完整、最不容易让人误解的。因此，本文中将以XP的实践为主介绍敏捷。其实，敏捷的其他实践或多或少都是极限编程的子集或者变体。

生命之环的最外层是面向业务的实践。这一层和Scrum的实践是等同的。

- **计划游戏**：用于将项目拆分成细节的功能、用户故事和任务，并针对它们排优先级和估算。
- **小的发布**：按照迭代方式增量发布。
- **验收测试**：提供针对功能、故事、任务的完工判断标准。
- **完整团队**：同一个团队中包含不同职能的人，一起为共同的目标努力。

生命之环的中间是面向团队的实践。这一层提供了团队沟通、管理的框架和原则。

- **可持续的节奏：**使团队保持稳定的节奏，避免在距离完成还很遥远时就榨干团队。
- **集体所有权**：避免团队分裂，共同担责。
- **持续集成**：频繁构建，持续反馈，让团队时刻清楚系统状态。
- **隐喻**：创建一种业务和开发都能理解的词汇表。

生命之环的中间是面向软件工程的实践。这些实践用来保证软件产品的质量。

- **结对**：让技术团队持续进行技能分享、评审和协作。
- **简单设计：**避免过度设计，减少浪费。
- **重构：**持续改进产品的内建质量。
- **测试驱动开发**：提供快速、高质量开发的安全保证。

以上这些实践和敏捷宣言是一致的，其对应关系如下。

| 敏捷宣言                   | 极限编程实践                                                 |
| -------------------------- | ------------------------------------------------------------ |
| 个体和互动 高于 流程和工具 | 整体团队、隐喻、集体所有权、结对、可持续的节奏               |
| 工作的软件 高于 详尽的文档 | 验收测试、测试驱动开发、简单设计、重构、持续集成             |
| 客户合作 高于 合同谈判     | 小的发布、计划游戏、验收测试**、**隐喻                       |
| 响应变化 高于 遵循计划     | 小的发布、计划游戏、可持续的节奏、测试驱动开发、重构、验收测试 |

### 1.5 总结

敏捷是一系列小的实践、他可以帮助小的团队构建小的软件。然而，无论项目大小，原理是相通的，因为大的项目也是由小的项目组成的。

## 2.拥抱敏捷的原因

敏捷很重要，这不仅是针对软件开发，而且对于工业、社会和整个人类文明的很重要。但是，很多人学习敏捷只是随大流，或者觉得敏捷可以提高速度和质量。这些并不是敏捷重要的原因，敏捷软件开发有着更深层次的哲学和道德原因。

### 2.1 专业性

敏捷要想做对，我们必须结队编程、测试现行、重构和实践简单设计；我们必须在小的迭代中工作，每个迭代都产出可用的软件；我们必须定期地、持续地和业务沟通。
敏捷软件开发是在软件产业中推进专业性的必由之路。
我们曾经失败得太多，我们交付了太多垃圾，我们制造了太多缺陷，我们做了太多的妥协。作为软件从业人员，我们必须提升专业性了。
**软件无处不在**
现在，人们的生活中处处都有软件的身影，没有软件现在人类社会就无法正常运行。
**程序员统治世界**
某种意义上程序员统治世界！软件开发人员的行为和人们的生命财产息息相关。
**软件导致的灾难**
你知道2013年丰田因软件缺陷导致汽车故障，赔偿了几百万美金吗？你知道，大众因尾气排放造假，在接受国会质询时声称是软件问题导致排放数据不准确。

### 2.2 合理的预期 

以下是管理层、用户和客户对软件开发人员的合理要求。
- 我们永不交付垃圾！
- 持续的技术可读性。
- 稳定的产能。
- 廉价的可适应性。
- 持续地改进。
- 问心无愧的专业能力。
- QA找不到任何缺陷。
- 自动化测试。
- 团队互相护持。
- 准确的预估。
- 必要时勇于说“不”。
- 持续疯狂地学习。
- 言传身教。

### 2.3 权利法案

作为客户，应该拥有如下权利：
- 有权知晓完成计划所需要的时间和成本；
- 有权在每个迭代都获得尽可能大的业务价值；
- 有权了解系统的进展，并通过客户定义的测试来验收功能；
- 有权在不增加额外成本的情况下改变想法、替换功能和调整优先级；
- 有权被告知计划和范围变更，有权随时取消功能，但是已完成的功能仍然可用；

作为软件开发人员，应该拥有如下权利：
- 有权知道需求内容，和清楚的优先级定义；
- 有权在任何时候生产高质量的代码；
- 有权要求同事、管理者和客户进行帮助；
- 有权更改预估；
- 有权主动选择任务而不是被动分配；

### 2.4 小结

敏捷是支持专业软件开发的原则框架。
敏捷不是一个过程、潮流和规则，敏捷是推动软件工程师职业道德建设的一系列的权利、期望和原则。

## 3.业务实践

### 3.1 计划

如何进行项目估算呢？

一个简单的办法就是将项目拆分成许多小的部分，针对这些小的部分进行估算。如果这些小的组成部分仍然难以估算，那么证明他们还需要继续拆分。

如果你想要非常准确，那么可以细化到代码行的程度--但是这样的话，基本上等价于你已经花费大量的时间把代码写出来了，那么估算的价值又再哪里呢？

这样说来，在允许的实践范围内，估算只能尽量准确，但是又不能强求精确。

对于软件开发来说，估算就是要使用少量时间，在最小范围内保持准确。

**用户故事**

用户故事的方法采用标准口径针对真实情况进行频繁反馈的循环来解决准确度的问题。一开始准确度很差，但是随着循环进行，准确度会越来越高。

用户故事，是从用户视角出发，对一个系统功能的简单描述。例如：

> 作为一名汽车驾驶员，为了提高汽车的速度，我将会用脚踩加速踏板。

当然，有些人细化用一个词，比如“加速踏板”，表述上述故事。

无论长还是短，都只是作为一次业务需求沟通的助记符或者提词器。用户故事的描述尽量简单，避免细节，细节可以等到要开发功能之前再沟通。真正的业务需求沟通，可能就发生在写下这些助记符的那一刻。

用户故事被记录在用户故事卡片上，卡片通常被贴在墙上或者白板上。

用户故事的拆分需要符合**INVEST**原则：

- **Independent(独立)**

​       用户故事之间是互相独立的，没有依赖，因而实现顺序上不存在先后之分。

-  **Negotiable（可沟通）**

​       不写需求细节的原因就在于我们期望细节是可以沟通的。

- **Valuable（有价值）**

​       用户故事必须有清晰地可量化的业务价值。

- **Estimable（可预估）**

​       用户故事必须足够具体，这样开发人员才能做出预估。

- **Small（小）**

​       用户故事应该小到一两个开发人员在一个迭代内能够完成。

- **Testable（可测试）**

​     业务可以通过清楚的测试来验证功能是否完成。

**故事点数**

现在，开发人员、测试人员、干系人......坐在一起对用户故事卡片进行估算。估算的目的是根据用户故事的实现复杂度和难度，估计实现所需要花费的工作量，我们用“点数”来代表这种工作量。

这种估算是相对的，所以我们需要选择一个标准故事（Golden Story）。先确定标准故事的点数，其他故事相对于标准故事而言，评估出点数。

当然，在此过程中，团队可能需要针对每一个故事所代表的需求进行细节讨论，干系人需要将自己需要的功能细节进行阐述，这样团队才能得出一个具体的点数。

![](.\image\atm_story_point.PNG)

举例，上面是一个ATM用户故事估算，我们选择Login为标准用户故事，设定其点数为3，则其他用户故事根据与Login相比得出其点数。

实践中，有几种常见的方式来得出点数：

- 猜拳（Fly Finger）

​     开发人员围坐在一个桌子周围，逐个讨论用户故事。每个开发者将一只手放在身后，让别人看不见，同时准备好用伸出的手指数量代表点数。然后，一起数1...2...3...后同时出示藏在背后的手。如果大家出的点数都差不多，那么故事点就确定了；如果大家出的点数差异很大，则差异大的人给出自己的理由，然后重新出点，知道基本上达成一致。

- 扑克游戏（Poker Game）

扑克牌游戏和猜拳差不多，只不过通过出扑克牌来代表故事点数。通常，出的点数是符合斐波那契数列的，即0、1、2、3、5...∞。0代表故事太过琐碎，此时可能需要合并用户故事；∞代表故事太大，需要进行拆分。

**迭代启动会议**

在迭代开始之前，先进行迭代启动会议。

迭代启动会议占用迭代周期的1/20，也就是说，如果迭代周期是两周，那么迭代启动会议要花半天时间。

迭代启动会议的目标是要决定哪些用户故事可以在本次迭代中完成。

当然，首先要根据业务需求的优先级考虑，这个优先级是业务干系人定义的。

团队的“速率”也是关键考虑因素。“速率”是指开发、测试在一个迭代中所能完成的总点数。计划阶段使用的“速率''就是上一个迭代实际完成的故事点数。第一个迭代只能猜一个合适的速率值，随着迭代的进行，这个值将越来越准确。

投资回报率也是一个重要的考虑因素，通常考虑业务价值和实现成本。例如，业务价值高但是成本最低的用户故事优先实现。

![](.\image\story_roi.PNG)

**中期评审会**

在迭代的中间，例如第二周的星期一，团队进行中期评审会议，根据迭代前半部分进展情况调整用户故事范围。

例如，迭代计划完成30个用户点数，但是中期评审会上发现前一周只完成了10个点数，所以基本上可以认为迭代只能完成20个点数，那么以为还有10个点的故事需要从迭代中移除。

如果到迭代结束时，总共只完成了18个用户点数，那是不是意味着迭代失败了？不是的，只要迭代能够产出数据用于管理层指导下一个迭代，迭代就不算失败，即使没有完成计划的点数。

**验收测试**

在迭代启动会议结束后，测试人员就应该开始开发自动化的验收测试了。优先级高的用户故事的验收测试应该先写，所有的验收测试应该在中期评审会前完成。只有这样，才能保证测试不会成为完成用户故事的瓶颈。

当然，如果到了中期评审会，验收测试仍然没有开发完成，那么部分开发人员应该停下开发工作，转而帮助测试人员开发验收测试。

如果测试人员在中期评审会之前就已经完成了所有验收测试开发，那么测试人员也可以为下一个迭代的用户故事编写验收测试。

话又说回来，如果到整个迭代结束时，验收测试都没有开发完成，那么意味着团队中开发和测试人员的比例不合理。

用户故事完工的验收标准就是通过验收测试。如果迭代快结束时，仍然有部分用户故事没有通过，那么就决定抛弃其中一些故事，全力保证剩余故事完成。

**产品演示**

在迭代结束前，开发团队需要向业务干系人简要地演示系统功能。当然，首先要演示所有的验收测试和单元测试都通过了，然后演示本次迭代所新开发完成的功能。这个过程最好是由业务干系人自己操作的，免得开发人员有隐瞒的嫌疑。

**项目完结**

随着一轮又一轮迭代的进行，每一轮迭代的速率本统计出来形成速率图，现在每一个人都知道团队的速度有多快了。

在这样的迭代进行中，可能不停地有新的用户故事被添加进来，但是迟早有一天所有有价值的用户故事都会被实现完成，此时项目就接近结束了。

### 3.2 小的发布

小的发布就意味着开发团队需要尽可能频繁地发布应用。小的发布的终极目标即使持续交付，也就是每一次变更都发布到生产环境。

小的发布不仅仅是要减小发布的周期，而是要减少软件发布过程中涉及的所有环节的周期。

敏捷的流程会驱使团队朝着小的发布周期迈进。但是，要想尽量减小发布周期，就要实现发布和部署分离。”发布“是指软件在技术上做好了生产部署的准备；”部署“是指将软件实际安装到生产环境提供给用户实际使用。”部署“是一个纯粹的业务决策。

### 3.3 验收测试

在所有的敏捷实践中，验收测试是最不被理解、最少使用和最让人困惑的一个实践。

造成这种奇怪现象的原因非常简单：需求是由业务部门制定的。业务需求往往不那么具体，或者业务需求往往只是愿景，而业务部门希望开发部门自己搞清楚细节。与此同时，开发部门希望的正好是业务部门告知所有的细节。所以，这里需要一种妥协。

验收测试应该是一种规范，例如：

> 当用户输入有效的用户名和密码，并且点击”登录“后，系统显示欢迎页面。

这种规范显然也是一种测试案例，当然也应该被自动化。这种测试就被称为验收测试。

那么问题又来了，谁来负责写自动化的验收测试案例呢？

莫非你想让业务部门来写测试代码？他们要能写代码还用得着来找开发部门开发软件？

难道你想让开发人员来写验收测试代码？他们既要写实现代码，又要写测试代码，怎么保证测试是从用户的角度出发的呢？

现在，你知道为什么这个实践是如此的让人困惑了吧！

**工具与方法论**

更糟糕的是，验收测试的实践被淹没在各种工具和方法论中。

如果你想让业务部门很容易地开发出验收测试，那么有一些工具可以帮助。例如：

Fitness、JBehave、SpecFlow、Cucumber

这些工具通常屏蔽了技术细节，并且通过这种表单的格式来录入业务验收测试。

这里有一个假设，即业务人员使用这些工具来写出面向业务的验收测试，而开发人员使用胶水代码将这些验收测试和被测系统粘合起来。

这种想法看起来美，因为即能保证业务参与，又能解决技术问题。但是，现实中真正愿意写这种测试案例的业务人员少之又少，业务人员更喜欢把这个认为交给测试人员。

**行为驱动开发（Behavior Driven Development）**

BDD是业务层面的TDD，即采用规范的动词：Given、When、Then来定义业务验收测试，通过工具的支持来进行测试，这样使得验收测试专注于业务。

BDD使得业务人员不用再关系技术细节，有保证测试真的可以执行，同时也保证了测试规范性和准确性。

**验收测试实际运用**

验收测试的思想很简单，业务通过测试来描述对于用户故事的期望，开发让这种测试自动化。验收测试一旦开发完成，那么用户故事所代表的业务功能的细节就确定了。

业务需求分析人员或者测试人员在中期评审前完成验收测试开发，开发人员将这些测试集成到持续集成中，通过验收测试则证明用户故事开发完成。

**业务分析人员和测试人员的分工**

既然现实中业务分析人员和测试人员共同完成验收测试，那么二者的工作有什么不同呢？

通常，业务分析人员偏向于开发”正向“测试案例，也就是正常业务案例；测试人员偏向于开发”逆向“测试案例，也就是”破坏性“测业务测试案例。专业的测试人员最擅长的就是这种破坏性的测试，因为一方面他们有技术背景，知道什么情况下体统容易被破坏；另外一方面他们更容易与开发人员协作，从而开发出技术上有意义的测试。

由此可见，测试人员肩负了重要的责任，他们已经不是传统意义上的验证者，更加是站在业务角度需求定义者。

**测试前置**

测试前置与测试自动化解决了一个重大的问题：传统的手工进行的开发完成才进行的测试，通常使得测试变成整个团队的瓶颈。

在传统的手工测试下，所有上游的延迟、质量不佳所产生的压力都转嫁到测试头上，而上线日期又是不可妥协的，所以测试往往会被牺牲掉。这样又会导致更加严重的问题。

**开发人员执行测试**

测试人员为一个迭代中的用户故事开发验收测试，但是测试人员却不负责执行验收测试，开发人员负责执行验收测试。

这样，开发人员的职责就变成了让自己开发的程序通过验收测试，所以开发人员不得不将验收测试集成到持续构建流水线中，从而导致了持续集成。

### 3.4 完整团队

完整团队是指尽量减小开发团队成员之间的物理距离。理想情况下，开发团队的所有成员都应该在同一个办公室中工作。

开发团队的所有人都在一起办公毫无疑问地能提升沟通效率--问题与答案就发生在几秒之内。同时，这也极大地增加了意外发现问题的机会。例如，测试人员会听到开发人员之间的讨论，而意外发现他们的错误；产品经理会意外发现界面设计不符合预期。

完整团队本算作业务实践，那是因为最大的收益在于业务方面。

**本地办公**

设立团队专属的办公室或者工作空间，能够极大地提升团队的效率。

**异地办公**

如果团队无法实现物理上的本地办公，那么一个可选项就是高带宽的网络加上在线沟通工具。当然，此时最好能够保证团队成员处于同一个时区、使用同一个中语言、并且具备相同的文化背景。

### 3.5 小结

敏捷的一个目标就是要治愈开发团队与业务团队之间的隔阂，而这些业务实践扮演了一个重要角色。

## 4.团队实践

处于生命之环中间的是团队实践。团队实践用于处理团队成员之间的关系，以及团队与产品之间的关系。

### 4.1 隐喻

隐喻是一种令人窘迫的实践，因为我们无法描述清楚什么是隐喻！我们也知道隐喻很重要，并且能给出很多例子，但是往往只有等你看到了“隐喻”，你才明白什么是隐喻。

隐喻的基本想法是，为了团队的有效沟通，团队需要形成一种规范统一的词汇表，团队对这些词汇代表的概念有着一致的理解。

利用隐喻，用户和开发团队可以进行顺畅的沟通，因为现在大家都有共同的语言。

但是，如果对于隐喻的理解造成偏差，则又会产生很大的问题。这也就是我们常说的，“你以为你理解了，其实你并不理解”。有些时候，隐喻甚至会导致开发团队与业务部门之间的冲突。

**领域驱动设计**

在领域驱动设计中，我们使用“一致性语言”来描述问题域中所有团队成员都认可的词汇表。这不单是隐喻的一种实现，也解决了难以解释什么是隐喻的困境。

一旦“一致性语言”形成，开发、测试、运维、业务都会使用。业务部门会用这种词汇来描述需求，架构师会用这种词汇来描述设计......这样整个项目中的沟通就被一致地联系起来。

### 4.2 可持续的节奏

上帝创世的第七天，他选择了休息。所以，上帝肯定知道可持续的节奏的重要性。

每周工作60小时、80小时，甚至熬通宵，怎么样？有些人认为这样的开发人员才够专业、才够努力、才有价值，因为这样的开发人员可以以一人之力决定整个项目的成败。

但是，这种玩儿命的工作方式是不可持续的，因为你迟早有一天要崩溃。然后呢？带着一腔怒火，你离职了，留给公司一个千疮百孔的系统。

**加班**

事实上，大部分技术债务都是在头脑不太清醒的状态下制造的，而加班甚至是熬夜很容造成这种状态。然而，因为加班所带来的产能提升远远小于偿还这些技术债务的花费。所以，总体来说，如果不是为了应对紧急状态，加班得不偿失。

**马拉松**

软件的项目就像是马拉松，而不是短跑，更不是一系列的短跑。如果你一开始就是竭尽全力，那么还没有到达终点你就精疲力尽了。

所以，你必须以一种可持续的速度来跑，只有在快接近终点时，如果你还有体力，你可以冲刺一下。

可能有些时候你的老板会要求你加班，但是作为一个专业的开发人员，你必须考虑如何让自己以可持续的节奏工作。

**奉献**

加班并不是体现你的奉献精神的方式；加班意味着你的计划做得不好；加班意味着你不应该接受不切实际的上线日期；加班意味着你只是一个容易操作的劳工，而不是一个专家。

以上并不表示所有的加班都是坏的，或者说你永远都不应该加班，总会有紧急情况导致加班是唯一选项。但是，这种情况应该很罕见，且你应该意识到其成本比收益要大。

**睡眠**

程序员一生中最重要的养料就是充足的睡眠。我们通常需要每天睡7个小时以上，可以忍受偶尔6个小时以上，否则我们的工作效率直线下降。

### 4.3 集体所有权

敏捷的项目的源代码由团队成员集体控制。这也就是说团队中每一个成员都可以修改任何一个模块的代码。

集体所有权并比不是说我们不需要专家，而是意味着我们不应该被专业领域所局限。每一个团队成员都应该具备在自己的专业领域外工作的能力。只有这样，才能保证团队的技能均衡分布，才能确保每一个团队成员都了解系统和各种边界，才能促进团队进行有效的沟通。

### 4.4 持续集成

持续集成意味着开发人员每隔几小时就要提交一次代码，完成代码合并到主线，触发构建，通过所有的单元测试和验收测试，完成部署的过程。

在现在的持续构建工具的支持下，持续集成的频率不再是小时级，而是分钟级。当然，这就要求开发团队真正是按照“集成”的方式来提交变化，违反这种提交频率的代价就是永远完不成集成。

例如，如果开发团队中大多数人是以分钟级的频率提交变更的，而团队中有一个开发人员是以小时级来提交变更。那么，这个特殊的开发人员可能代码合并过程永远无法完成，因为他刚完成一次合并，其他人的变更又来了，以至于他永远都无法完成。

**持续集成失败**

持续集成失败应该作为头等大事来对待，团队应该响起警报，停下所有手头的工作，全力解决导致失败地问题。

**作弊的代价**

对持续集成失败坐视不理，甚至是故意跳过测试，这属于典型的自杀行为。一旦团队形成这种风气，那么就意味着默许可以交付存在问题的软件。

### 4.5 站会

敏捷中的站会的定义是：

- 站会是可选的，很多团队没有站会也运作得很好。
- 不用每天都开，选择合适团队的频率很重要。
- 每次站会在10分钟左右，即便是大型团队也这样。
- 会议遵循简单的模式。

仅此而已！没有讨论，没有姿态，也没有深入的解释，没有冷板凳，也没有话唠。每个人用30秒回答下面问题，然后开始工作。

- 从上次站会起，我做了什么事情。
- 到下次展会前，我将会做什么事情。
- 我遇到了什么难题。

 **鸡蛋与火腿的故事**

故事的主旨就是，只有开发人员应该在站会上发言，而管理层只应该听而不应该发言。

**喊出来**

如果可以，我想增加一个问题，就是“你想感谢谁？”，如果有请大声讲出来。

### **4.6 小结**

敏捷软件开发是一系列帮助小团队开发小型软件的原则、实践和纪律。敏捷的团队实践帮助团队真正的看起来像一个团队。

## 5.技术实践

敏捷的技术 实践是现代的程序员和流行了70多年的工作方式的彻底决裂。敏捷的工程实践由一系列意义深远的仪式性行为构成。

当然，有些开发人员认为这些工程实践是荒谬可笑的，所尝试跳过工程实践去应用敏捷，但是无一列的都失败了。因为，敏捷的工程实践是敏捷的核心。没有TDD、重构、简单设计和结对编程，敏捷就变成了一个没用的空壳。

### 5.1 测试驱动开发

测试驱动开发是一个复杂、内容丰富的话题，值得用一本书来详细描述。在这里我们只是概要的描述测试驱动开发背后深层次的动机和正当性，而不是技术上的原因。

软件开发是一个独特的专业领域。我们产出了一堆充满神秘符号的文档，任何一个符号都必须精确，否则就会导致财富甚至是生命的损失。

还有哪个专业领域是这样的呢？会计！

那么会计师是如何保证他们产出的文档的正确性呢？

**复式记账法**

每一笔交易都要在两个相关账户中进行登记，两个账户中资金额变化是相等的。会计师在每记录一笔账目后都会计算余额，这样便于快速发现错误；而不会等到记录很多笔账目后才计算余额。这种简单的规则如此之重要，甚至变成了基本的会计准则，甚至是法律。

TDD是复式记账法在软件开发领域的体现，因为每一个功能都被录入了两遍：一遍作为单元测试，一遍作为实现代码。两个过程互为补充，从而避免产生bug。

实施TDD时，开发人员先写测试案例，然后再写业务代码让测试通过，这样就能够快速地发现缺陷。开发人员避免写太多的生产代码，否则缺陷就难以定位。

**TDD的三条法则**

- 在写出失败的单元测试之前，不允许写任何业务实现代码。
- 只要有测试失败，就不能再写测试--编译失败也算。
- 只要当前失败地测试通过，就不能再写业务实现代码。

只要有几个月开发经验的程序员，大多数都会觉得这种规则太过诡异，甚至是反人类的......。

这种规则导致了一种只持续几十秒的编程周期。开发人员先为还没有实现的业务代码写一个测试。此时测试会编译失败，因为被依赖的测代码还没不存在。开发人员停止写测试，开始写业务实现代码。仅仅一小会儿，测试代码可以编译通过了。然后开发人员继续写测试，测试执行失败。然后开发人员停止写测试，继续写业务实现代码......

写测试与写实现两种状态的切换在几十秒内发生，开发人员深陷于这种循环。大多数开发的开发人员一开始都会认为TDD过程容易导致思路被打断，以至于无法写出一个深思熟虑的代码。

然而，假设团队中每一个开发人员都在实践TDD，那么随便谁写的代码都是经过测试的。这也就是说，某种意义上，只要代码被写下，整个系统在任何时候都是可以工作的。

**调试**

调试程序是一个费时费力的过程，实践TDD极大地减少了调试出现的可能性。当然，也不是说TDD写出的程序就绝对没有bug，只不过是这种方法极大地减少了bug。

**文档**

按照TDD的方式写代码，那么单元测试就变成了对业务代码使用的样例代码。所以，如果你想了解业务代码的如何使用，则测试提供了最好的文档。

**乐趣**

如果你先写业务实现代码，再写测试，那么写测试的过程变得毫无乐趣。因为，作为开发者，你已经知道你的代码能工作了--你在写的时候就已经手工测试过、调试过了。你写测试只是应该老板要求你写测试，这个过程经常是纯属应付，索然无味。

当你先写测试时，你就会感觉快乐多了。这就好像一次次的挑战，每一次测试通过都能带来小小的喜悦。这种充满节奏的小步迭代，才是真正确保你的代码能工作的方式。

**测试完成度**

在测试后置的方式下，开发人员已经完成了功能开发，但是由于各种规定，不得不在事后补充单元测试。

但是，开发人员迟早会遇到很难测试的情况，因为原来写代码时并没有考虑可测性。那么问题来了，要不要去改动现有代码，使得其可测呢？在时间紧迫且面临破坏已经完成的功能的情况下--此时验收测试可能已经完成，如何选择呢？

大多数时候，开发人员说服自己，这种单元测试是不必要的，然后放弃了测试。所以，现在有些功能是可能有问题的，反正没有测试，就像系统中有一个潜在的陷阱。

如果整个团队都这么想，那么测试的完成度有多高呢？90%？80%？

如果采用测试前置，那么上述这种情况就不会发生。当然，我不可能做100%的但是测试，但是至少我们都想到的所有测试都做了，完成度已经是尽可能的高。

**可测性设计**

测试难写的原因就在于代码设计时就没有考虑可测性。

在测试驱动开发的方式下，如果不写测试就不能写功能实现代码，因此开发人员自然而然地会写出可测的代码。这种先天具备的可测性会促成松耦合的代码设计。这也是为什么TDD被也被当做是一种设计工具的原因。

**勇气**

到此，我们已经看到了TDD带来的各种好处：减少调试、良好的文档、充满乐趣、测试完成度高和松耦合的设计。但是，这些只是附属收益，真正的收益是勇气！

当开发人员面对遗留代码时，第一反应是“我应该优化这段代码”，第二反应是“算了吧，别动，一旦搞坏了就变成我的事了”。开发人员测内心是矛盾的，也是充满恐惧的。

如果开发团队里人人都这样想，那么系统必定会腐败！最终的结局就是系统的越来越改不动，然后迟早有一天团队在绝望中会要求重写系统。

这就是为什么我们需要TDD，因为TDD给了我们保持代码整洁的勇气，也给了我们保持自己专业性的勇气！

### **5.2 重构**

重构是另外一个值得用一本书来描述的话题，幸运的是，Martin Fowler的《重构：改善既有代码的设计》就是这样一本书。所以，本文中我们只讲重构的基本原则，而不涉及重构的细节。

重构是一种在不改变由测试定义的代码行为的前提下调整代码结构的实践。这种实践和TDD是紧密相连的。因为，要想毫无畏惧地进行重构，我就需要有测试来保证不破坏系统的功能。

**红、绿、重构**

重构的流程被融入TDD过程中，从而形成了“红、绿、重构”这样一种循环。

1. 首先，我们创建会执行失败地测试；
2. 然后，我们让测试通过；
3. 接着，我们优化代码结构；
4. 回到步骤1；

![](.\image\red_green_refactor_circle.PNG)

我们将写单元测试、写业务实现代码和重构分开，从而形成了一种清晰的、可持续的流程。

重构不是一项特别的任务，不需要特别规划，他是正常编写代码工作中必要的一环。

**更大范围的重构**

有时，需求和变化是如此之巨大，以至于我们会觉得现在的设计和架构很不理想，需要进行重大的变更。

这种变化同样可以通过“红、绿、重构”这种循环来进行。我们不需要单独启动一个重构的项目或者任务，我们也不单独为这种重构预留时间。相反，我们只是在常规的功能迭代中逐步把功能一点一点地迁移到新设计之下。

这种设计的变更可能花费几天、几周、几个月甚至是几年，但是在这个过程中，系统持续的通过测试，被部署到生产环境，尽管设计的变迁一直在进行中。

### **5.3 简单设计**

简单设计是只设计最简单、最小和最清晰的结构的实践。简单设计就是重构的基本目标。

Kent Beck定义的简单设计的步骤为：

1. 通过测试；
2. 揭示意图；
3. 移除重复；
4. 精简结构；

上述序既表示执行的顺序，又表示了优先级。

第1点是为了自我证明，代码通过所有测试，表明代码能够工作。

第2点是说在代码可以工作以后，我们应该让代码变得清晰，从而能够显而易见地揭示程序员的意图。

第3点是说我们应该移除重复，意味着我们需要应用各种抽象和设计模式。

第4点是说我们应该尽量减少程序所需要的类、函数和变量。

简单的设计是为了尽量减少设计的重量。

**设计的重量**

一个设计越复杂，则其带给程序员的认知负担就越重，这种认知的负担就称为设计的重量。

设计的重量越大，则程序员用于理解和维护系统所花费的时间精力就越多。

类似的，需求越复杂，则程序员用于理解和实现需求所花费的时间精力就越多。

然而，上述两种因素的效果并不是叠加的。复杂的功能可以被一个更加复杂的设计所简化。系统整体的复杂度可以通过选择合适的设计来进行简化。

简单设计的目标就是在设计和功能复杂度之间寻求一种平衡，只有保持这种平衡，才能确保最大化的生产率。

### 5.4 结对编程

多年以来，开发人员对结对编程实践总是充满了非议与误解。

很多人对两个人协同功能能提升效率始终持负面态度。

首先，结对应该是可选的。我们不应该强制进行结对编程。其次，结对是断断续续的。结对的时间占总时间的30%~80%之间比较合适。不管怎样，是否结对应该是团队的选择。

**什么是结对编程？**

结对编程是两个人一起解决同一个编程问题。两个人可以坐在同一台电脑前，共享显示器、键盘和鼠标，或者他们可以使用屏幕共享软件，或者是远程协作，只要他们能共享语音和数据。

结对的程序员轮流担任不同的角色。

一种分工是"驾驶员"与"领航员"：驾驶员负责控制键盘和鼠标，领航员负责观察和给出建议。

另外一种分工是测试者和开发者：测试者负责开发单元测试，开发者负责实现业务功能通过测试。这种模式也叫作”乒乓“。

更常见一种情况是没有明确角色分工，结对的程序员平等地控制鼠标和键盘。

结队应该是开发人员的自主选择，而不应该故意安排；结队是短期的，通常在1~2个小时以内。

用户故事不是分配给结队的两个程序员，而是由其中一个人认领。程序员的时间应该有可以分一半来完成自己认领的任务，另外一半主动去和其他人结队完成他们的任务。

老手应该经常和新手结队，新手应该主动要去和老手结队，领域专家应该和领域外的工程师结队。

结队的目标是传播和交换知识。

**为什么要结队**？

通过结队，我们能表现得像一个团队。团队成员之间彼此不孤立，而是互相协作和支持。

结队是团队成员之间共享知识并防止形成知识孤岛的最佳方法。

结队可以减少错误并提高设计质量。许多团队使用结队代替代码评审。

**结队当作代码评审**

结队是一种代码评审的形式，但是比一般的代码评审方式优越得多。结队的两人在结队期间是共同作者，虽然说他们真正的目的是写新代码，但是他们也会自然而然地评审旧代码。因此，结队是对代码当前状态的动态回顾，着眼于在不久的将来代码的发展。

**结队的代价**

结对最直接的代价就是两个人共同处理一个问题。一些研究表明，结队的直接成本为15%，也就是说需要115位程序员来完成原本需要100位程序员的工作。

但是，如果结队的时间只占50%，那么在生产力上付出的代价不到8%。另外，如果结队时间代替了代码评审，那么很可能生产力根本不会降低。

另外，结队对知识传递所带来的好处不容易量化，但可能会非常重要。

**结队只能两个人吗？**

通常结队通常只涉及2个人，但是有时也可以多个人共同解决某个问题。

**管理**

管理者通常很高兴看到程序员进行协作和合作，这给人以工作正在取得进展的印象。

如果你是管理者，如果你担心结队对效率的影响，那么请放心，让程序员们自行解决这个问题。

**5.5 小结**

敏捷的技术实践是任何敏捷工作中最本质的组成部分。任何敏捷实践导入的尝试，如果不包含技术实践，就注定会失败。

## 6.总结

本文的主要内容提取自《Clean Agile》这本书的前5章。如果你对敏捷还存在困惑，那么强烈建议阅读原书。

《Clean Agile》的第6章以后也提到了关于敏捷转型和敏捷教练的内容，不太适合精简，读者可以自行去探索。