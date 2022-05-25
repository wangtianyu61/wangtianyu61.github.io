---
layout: post
title: Revenue Management的前世今生
date: 2019-10-21
categories: blog
tags: [收益管理]
description: 
---
开一个坑，等这学期结束reading week的时候或全部考完再更新。可能会中英文混杂（翻译有些单词总觉得怪怪的orz)。感觉这门课是交换学期听的最认真的一门课了（虽然是旁听且经常咕咕）【或许是人少会经常被cue】，能力有限如有错误欢迎指出并更正。


revenue management真是一门有意思的学科啊【太难了】，感觉他才是真正体现你院你系培养方案的目标。【雾
## Review of each lecture
### 历史与简介

![KN1ovR.png](https://s2.ax1x.com/2019/10/24/KN1ovR.md.png)

直接盗图，revenue management是operations research在商业界较为广泛的应用之一。也是一个非常商业化的领域，他结合了很多市场营销、经济博弈论领域的内容，而他的实现高效性又不得不与优化算法更好融合，甚至与数据挖掘中刻画用户画像，根据现有数据调整反馈（偏向于online/reinforcement learning等）。不仅来自经济、营销、数据学习等多方面的领域在研究，商家更需要这些新的模型来分析，比如最早开始的航空/酒店行业，现在也被广泛的线上线下零售业、广告业研究，甚至被作为思路应用到服务行业中去。


That is how trivial mathematics can lead a long way.

revenue management核心是消费者和商家双边市场的决策研究。直接抄ppt就是，the objective of RM is to sell the right goods at the right time to the right price through the right channel. The decisions are often related to structural decisions, pricing decisions and quantity decisions.

课上最早的案例便是航空业，也是RM领域最早的应用。基本决策也就是根据顾客的WTP来卖机票。一个基本的思路就是航空业如何收集历史数据，并通过需求分类不同等级的舱位，因而做出决策。早期航空业是不存在多种舱位的，但是自从1978年美国政策宽松后，廉航进入市场使得大型公司亏损。迫于无奈，1985年American Airlines就采用收益管理的系统，取得巨大收益并同时引起其他公司效仿。

Now no companies could survive without a good RM system.

同时传统的operations model滨不能很好地分析顾客行为，在现实生活中消费者行为本身就是一个很大的领域。在现代电子商务发展的时候，更是如此，这也促使RM不得不从传统优化与概率模型中寻找新的出路（当然还是得在现有基础上），而更多地向心理学、经济学、市场营销学挖掘新的想法。
### Single Price Optimization and Capacity Control
上课前记得自己还认为这个没啥好讨论的，结果...
single pricing model中最重要的还是 maximize f(p) = (p-c)d(p).其中d(p)表示需求函数，核心观点便是

[![KN3OLq.th.png](https://s2.ax1x.com/2019/10/24/KN3OLq.png)](https://imgchr.com/i/KN3OLq)

价格弹性系数比价格更重要，也就是需求对价格的敏感性。最优情况下：

[![KN3je0.png](https://s2.ax1x.com/2019/10/24/KN3je0.png)](https://imgchr.com/i/KN3je0)

下一步就是价格歧视（显然完全的价格歧视是不可能实现的），由此引出second degree discrimination和third degree price discrimination,分别是对购买数量和不同人群进行。但是有可能被要高价的人群会找到买低价的方法，即cannibalization.如何减少这种现象呢？

let the customers self-selct into appropriate categories.

市场的手是无形的。

于是就有use coupons/product versioning/damaging/opaque selling一堆方法，核心就是卖不同的产品，甚至于故意弄破产品实现价格歧视或者不告诉你到底是啥（见鬼）。但是价格歧视也不一定会降低customer surplus.

另一种就是动态定价的思路，核心就是运用DP。一篇经典的文献便是Gallego and van Ryzin(1994).事实上，constant pricing strategy is in asymptotically optimal.但是完全动态定价思路是不现实的，因此会有对markdown/markup pricing的研究。

定好价格歧视之后，航空公司还需要做的一个决策便是sell the tickets for flight given the classes, 最经典的就是[EMSR模型](https://en.wikipedia.org/wiki/Expected_marginal_seat_revenue). 

[![KN3vwV.md.png](https://s2.ax1x.com/2019/10/24/KN3vwV.md.png)](https://imgchr.com/i/KN3vwV)

但是EMSR的假设太强（需要顾客到达顺序和WTP完全相反），这显然是不现实的。而直接考虑在不同时间不同级别顾客到来是否接受，这就是一个典型的可以用DP方法求解的问题。最优策略也自然是一种threshold的方法，自然这种方法也是经不起complex customer behavior和商家行为的考验的，会有buy-up effect/spiral-down effect等许多的从choice model出发去修改去考虑，真的比较有意思。

另一个在revenue management值得一提的观点是no-show和对应的overbooking.对此的连锁现象是--（飞机/酒店）顾客买票/预订然后咕咕-->资源浪费-->收益损失。对此，最简单的方法就是overbooking.

也即是既然你可能会咕我，我就先下手为强，把你咕了，然后给你补偿。互咕不算咕（划去。

就是说可能会买票付款后被拒载。【万恶的资本主义

[![KN8SFU.md.png](https://s2.ax1x.com/2019/10/24/KN8SFU.md.png)](https://imgchr.com/i/KN8SFU)

在multiply class/network等设置的情况下，overbooking模型会涉及很多有意思的决策，就像咕谁，咕完是花钱消灾还是给其他好处等等。

### 世界是联系的：网络模型

当然，任何公司都不可能只卖一种东西，而航空公司这里体现的就是网络，网络之间节点的调度，构成了network capacity control的最基本元素。最简单的例子就是A到C的航班，和A到B且B到C的航班的比较。

[![KNNWLj.md.png](https://s2.ax1x.com/2019/10/24/KNNWLj.md.png)](https://imgchr.com/i/KNNWLj)

不同的origin-destination pair如果进行独立定价优化的话，可能会出现hidden city phenomenon，就是像上文中所说A到B的航班比A到C的航班贵这种现象。因此A到B的乘客就有激励去假装买A到C，然后半路跑路。解决这一问题不仅是单纯提价这么简单。

而最基本的network capacity control可看作一个m种资源和n种产品的DP问题，考虑问题是是否拒绝某一时间段某一乘客的要求的决策，即下文的u.

[![KNNgSS.md.png](https://s2.ax1x.com/2019/10/24/KNNgSS.md.png)](https://imgchr.com/i/KNNgSS)

但是这个回溯求解的DP显然是会遇到维数爆炸的问题，这种NP求解的方法主要是估计近似求解。主要来说，近似求解有两种思路，一种是松弛假设，转换原问题；另一种不松驰假设，近似表达式。

比如deterministic linear programming model就是确定性知道每一阶段的需求，从而利用LP求解每一阶段接受的request。而这个需求直接是future demand expectation.因此，理所应当会比原问题求解目标（利润）更大。

得到了想接受的request数量，下一步就是如何通过这个optimal request去构建控制策略呢？

课上讲了三种思路，partition allocation rule/bid price rule/certainty equivalent control.理论分析和数值模拟表明这些方法都能达到asymptotic optimal.(Talluri and van Ryzin 1998, Cooper 2002, Bersimas and Popoescu 2003, Adelman 2007) 

在DP方法中还有一种比较常见的就是approximate DP method.并且可作为原问题的上界。一般思路就是：

[![KNNsFP.md.png](https://s2.ax1x.com/2019/10/24/KNNsFP.md.png)](https://imgchr.com/i/KNNsFP)

当然，现有主要的NRM还是从sell side出发，从乘客出发的话会兴起choice-based model等一些交叉的东西, 如Liu and van Ryzin(2003).

### data-driven: no data and online data
【逐渐自闭
就是这节课，坐在第一排C位，被TCPcue where are you from;然后一通无厘头傻笑wtcl

开始还说的是人话的时候，就是收益管理中如果需求参数不会提前知道的情况下，怎么去预测。就有种robust optimization的味道在里面。应该这是第一节TCP的课，然后当时坐在下面就想：会不会讲DP和强化学习呢？那我可能就能听懂了。

讲是真的讲了，在线凸优化证明我是基本完全没听懂。

分为两种情况，一种是没有数据衡量的competitive ratio;另一种是在线数据衡量下的regret指标。然后讲了讲应用。

开头的例子挺容易的，就是两种等级的顾客。不同算法的比较由给出最差情况下该算法的收益/采取其他策略的收益的比值进行衡量，给出了myopic algorithm和conservative两种benchmark，然后用Book limit方法进行比较。

[![KbrP0g.md.png](https://s2.ax1x.com/2019/11/01/KbrP0g.md.png)](https://imgchr.com/i/KbrP0g)

对于这种continuous two-fare problem的问题，Ball and Queyranne (2009)给出了一个最优的competitive ratio, b(r);和相应的booking policy.【文献懒得挂reference了，就是初中数学】

然后突然就是凸分析了，佛了。

听说有人研究不同动物启发式行为对优化理论和算法的启示，还每个动物发一篇paper?【知道我上课为什么笑了吧

笑着笑着突然就————

[![KbrAts.md.png](https://s2.ax1x.com/2019/11/01/KbrAts.md.png)](https://imgchr.com/i/KbrAts)

其实在线学习就是通过之前新得到的数据更新，进行梯度下降的方法；和rolling window sample的含义挺相似的。regret就是每次的结果累计和最优结果之间的差距，然后是几页slides的证明。

[![KbrZpq.md.png](https://s2.ax1x.com/2019/11/01/KbrZpq.md.png)](https://imgchr.com/i/KbrZpq)

由此估计差值，引出Bregman Divergence和KL散度。也就是信息误差。

data-driven online learning是优化在数据时代与机器学习交叉一个非常实际的应用领域，为防止局部收敛到非最优解，通常不会采用passive learning的方法，而是active learning的方法。【哲学上看，就是不要固步自封，多出去走走？不然就囿于自身的圈子咯。也有点像多臂老虎机，即exploration and exploitation.

还有一部分是关于随机凸优化的，只知道LDR和SAA，其他一窍不通。溜了溜了

最后是一个关于滴滴多目标规划的问题，交通问题的匹配调度也就是满意解和最优解的区别。【多么富有哲学意味啊

终极不过在乌托邦那里罢了。Pareto最优也只能保证我们在efficient frontier上移动。

[![Kbre10.md.png](https://s2.ax1x.com/2019/11/01/Kbre10.md.png)](https://imgchr.com/i/Kbre10)

当你跳出乘客、司机、滴滴的三方视角上看，从waiting time/income/platform revenue跳出时间的周而复始，不过又是一次终极的trade-off罢了。
### 越来越复杂的选择模型
【不过真的太难了，全靠ppt翻译，这两节自己都没去听课
印象真的太深了，自己大二读过的第一篇paper好像就是transportation science B的一篇discrete choice analysis.当时被数学公式和符号吓着了orz.一年后再看，感觉已经轻松很多了。（虽然好像啥都没学懂

前文已经提到，assortment和network下基于的都是有限的选择情况，比如一堆经济舱/贵宾舱云云，抑或是豪华套间/普通间/大床房/套房等等。由于资源是有限的，DIY的机会并不太多。那么顾客也就仅能在这几种中挑好的咯。

Discrete choice model盛行于各种学科，比如经济学、社会学、心理学、生物统计学等。惊了，刚刚一查知乎居然还有人写专栏,见[离散选择模型](https://zhuanlan.zhihu.com/logit)好像比较偏向于logistic。不管了。

选择模型主要的用途有三：预测选择概率/估计因素相对重要性/协助企业最优决策。总之是挺决策论的东西。具体来说可分为参数和非参数的模型，参数模型主要是由utility决定绝对重要性，非参数则通过会有偏序性之类的。近年来也有提出semi-parametric model的。
#### RUM
不说了，大段抄PPT.

[![KyMUKO.md.png](https://s2.ax1x.com/2019/10/27/KyMUKO.md.png)](https://imgchr.com/i/KyMUKO)

说白了就是共性特征+个性特征。

其中最为著名也广为人知的就是MNL Model (Multinomial Logit Model, proposed by McFadden 1974),其是RUM模型中唯一具有Independence of Irrelevant Property (That is the ratio of choice probabilities between two alternatives does not depend on the utility and the presence of other alternatives).

[![KyMTGq.md.png](https://s2.ax1x.com/2019/10/27/KyMTGq.md.png)](https://imgchr.com/i/KyMTGq)

举个经典的Blue bus/red blus例子，假设乘客在选择乘公交还是taxi回家，若效用相同，则选择可能均为0.5.假设公交有两种颜色，并且乘客对哪种颜色不关系（P.S这个特征好奇怪的，真的会有人管哪种颜色吗）因此，U（taxi）= U(Bus1）= U（Bus2),那么现在taxi\bus1\bus2搭乘的概率就都变成1/3，显然不对。因此，这里就需要保证选择一致的。

但是，上述问题也可以被分为两阶段考虑，第一阶段考虑什么工具，第二阶段考虑什么颜色，就形成了nested logit model.

[![KyMLsU.md.png](https://s2.ax1x.com/2019/10/27/KyMLsU.md.png)](https://imgchr.com/i/KyMLsU)

这样就其使得满足IIA(Independence of Irrelevant Property)的性质了。NLM广义上来说属于更宏观的GEV Model（写不动了

[![KyMvdJ.md.png](https://s2.ax1x.com/2019/10/27/KyMvdJ.md.png)](https://imgchr.com/i/KyMvdJ)

然后又有对于\epsilon的研究，将RUM变成MNP模型。
#### Localization and Featurization
比如只有其中一部分选择呢？对于MNL是很简单的，对于一般的RUM把没有的变成负无穷不就行了吗？（多么朴素的想法

Utility究竟是什么？比如是特征的线性组合？当然对于不同顾客也可以将其变得很复杂。

这部分内容其实不多，也就是一些变体。

#### Beyond Random Utility Model(撕掉一些假设

[![KyQSiR.md.png](https://s2.ax1x.com/2019/10/27/KyQSiR.md.png)](https://imgchr.com/i/KyQSiR)

经济学、行为学和心理学又登场了！那就根据现实修正呗，突然变成了调参的世界【NLM参数多就是任性】古往今来，行为学给多少科研人员提供了生活的希望啊。【人性本善

[![KyQkLD.md.png](https://s2.ax1x.com/2019/10/27/KyQkLD.md.png)](https://imgchr.com/i/KyQkLD)

另外，Representative Agent Model证明了宏观调控会趋近于MNL。【社会主义好

[![KyQVdH.md.png](https://s2.ax1x.com/2019/10/27/KyQVdH.md.png)](https://imgchr.com/i/KyQVdH)

#### Semi-Parametric Choice Model
了解得不是很多，没怎么看懂其实。感觉是也对RUM的\epsilon做出的分布假设。说白了这个和RAM其实都是RUM的变体，并且能够解释一些非理性行为。

【把世界约束在数学之下实在是太难了，于是就有more and more model

[![KyQuWt.md.png](https://s2.ax1x.com/2019/10/27/KyQuWt.md.png)](https://imgchr.com/i/KyQuWt)

#### 大数据时代下的非参数模型
未来的很多研究方向还是从一些机器学习方法中抽取选择模型吧，反正都是在做选择。并且有可能会基于更多的行为，比如search.话说回来，rank list model指的就是不算utility了，直接搞排序，然后从高到低排。【有种你院评奖学金的感觉（删去】然后马尔可夫居然都出来了？？？真的能扯，但很实在。

选择模型真是一个奇妙的世界啊。【突然又想到那句，从底层神经科学打通到深度神经网络，贯穿上课所有领域研究的很少，可能choice model就算一个。

#### Estimations and Applications
被应用到Operations Research领域，最常见的有两个：一个是multiproduct pricing，另一个是assortment planning.

Multiproduct pricing用过来就是把purchase behavior直接转换为choice model，然后求解。会根据要求加各种各样的约束。当然这些选择模型就主要是参数的咯，非参加进去比较困难。

Assortment的策略就是Revenue-Ordered Assortment，直接把NP搞成P.

估计参数的问题交给统计学家咯，搞搞特征啥的，有种非参又不好弄特征了，比如rank-list choice model就调不同顾客类型。Markov-Chain choice model就争取把矩阵凑出来，比如EM算法等。

### 融合行为学的现代收益管理

### 走向双边市场与博弈

### 拾遗
讲的最后一节新课中提到了bundling,也就是捆绑销售。整理的时候真的是十分应景了。（想想自己与英签&VFS GLOBAL的故事orz)

作为一种新型的selling strategy,bundling在日常生活中得到了广泛运用，各种套餐blabla.

今天（20191114）的时候对operations and technology management的tutor的一句话真的是十分感同身受了。

All models are wrong, but some are useful. -- George Box.

什么假设什么模型都能整出来，跪了。模型还挺有趣的（凡是概率论都是扯犊子【划去】，假定顾客的WTP服从独立的二点伯努利分布，当然不取0，然后看各种bundling能够获得的收益，然后就是自然一堆CLT和Chebyshev估计界【话说感觉OR/MS一堆paper最后搞理论全是渐进最优，然后全是这些东西【太工程化了）

说白了bundling本质上是一种营销手段，说到底还是价格歧视。这里衡量的指标就是regret rate (RR)，与完全价格歧视相比较。

这块还是一个比较新的研究领域，看了下年份。

一些术语就是component pricing / pure bundling / mixed bundling

第一个是单独分别定价，第二个是全部所有绑在一起销售，第三个是选择部分销售。但是mixed bundling其实做起来是一件非常不tractable的事情的。基本等于穷举。

然后现在另一个热点就是bundling size pricing (BSP),就是customer自己选择bundle的大小然后以此定价。比如定杂志分别定一季度/年度blabla.

背景说完了其实后面就讲了若干数学推导，就像之前说的是一个MIP问题 #NP-hard.然后还有一种cross moment model。【也就是给定低阶矩信息，然后搞分布。和我这学期做的东西也比较像】图也懒得挂了。

然后就是如何从已知bundle顾客的结果学到一些东西...反正都是learning.

最后是讲了一些最新的应用，包括ancillary product pricing / flexi fare and free cancellation / check-out recommendation (you may also like ...)
其中最后有个东西倒是比较跪的。【老师在上面讲他和下面一个学生一起的paper,大家一起在乐呵呵。










## Highlight and Optimization Models

## Thoughts about future


## 参考资料
slides from BDC6248/IE 6881: Revenue Management (Xiaobo Li and Chung-Piaw Teo, NUS)

维基百科https://en.wikipedia.org/wiki/Revenue_management

Danial Adelman. Dynamic Bid Prices in Revenue Management. Operations Research, 2007.

Dimitris Bertsimas and Ioana Popescu. Revenue Management in a Dynamic Network Environment. Transportation Science, 2003.

William Cooper. Asymptotic Behavior of an Allocation Policy for Revenue Management. Operations Research, 2002.

Guillermo Gallego and Garrett van Ryzin. Optimal Dynamic Pricing of Inventories with Stochastic Demand over Finite Horizons. Management Science, 1994.

Guillermo Gallego and Garrett van Ryzin. A Multiproduct Pricing Problem and its Applications to Network Yield Management. Operations Research, 1997.

Qian Liu and Garrett van Ryzin. On the Choice-Based Linear Programming Model for Network Revenue Management. MSOM, 2008
