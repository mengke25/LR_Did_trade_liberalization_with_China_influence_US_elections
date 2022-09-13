# LR_Did_trade_liberalization_with_China_influence_US_elections# Did trade liberalization with China influence US elections?

## 一、概要

* 在进口竞争激烈的地区，选民更可能投票给倾向限制贸易的民主党
* 永久正常贸易关系(PNTR)消除了中美贸易战的可能性
* 根据县的产业结构构建exposure，衡量c地区受到PNTR的影响
* 在PNTR之后的第一个10年中，Exposure更大的县对民主党投票的份额相对增加
* 解释为什么2000年初选票转向民主党——使用断点回归，比较民主党险胜共和党的立法票——民主党人比共和党人更有可能投限制国际贸易的票，反对支持贸易的共和党总统
* 拓展到2016年川普总统的选举——进口竞争大幅增加的地区转而将选票投给反贸易的共和党人，Exposure较大的地区选民对“Tea Party”（共和党派的分支）的好感度及积极分子数量相对增加。

## 二、中美贸易/政治背景

* 中国逐渐成为美国最大的进口来源国——1990: 3%; 2007: 17%; 2016: 21%
* 2000年美国给与中国PNTR之后，中国进口激增。

​	<img src="D:\Typora\figs\Did_trade_liberalization_with_China_influence_US_elections\fig1.jpg" alt="image-20220911223033879" style="zoom:30%;" />

* 来自中国的进口增速迅猛，美国制造业就业人数大幅下降，
* 美国各级政府立法者会对“国际贸易”表态
* 克林顿总统主持NAFTA协定批准，并给予中国PNTR
* Tea Party的兴起导致，国会中越来越多的共和党加入民主党的行列，反对贸易协定
* 2016年共和党不仅反对新的贸易协定，还呼吁推翻现有的协定

<img src="D:\Typora\figs\Did_trade_liberalization_with_China_influence_US_elections\fig2.jpg" alt="image-20220911223033879" style="zoom:30%;float:left" />

## 三、数据

### （一）PNTR暴露程度的衡量

* 使用美国关税表（US tariff schedule）衡量每个行业受PNTR的影响，再根据c县的就业权重计算Exposure
* 美国关税两套基本税率：①NTR灌输，个行业平均4%；②非NTR关税，个行业平均为34%，
* 从中国进口的商品使用非NTR关税，总统有权对这些国家豁免，给予NTR关税的待遇。从1980年开始，总统每年都给与中国这样的豁免，但8964政治风波后，这种豁免变得有争议不确定（这种不确定与双边政治关系有关，如1993中国向巴基斯坦转让导弹技术；1996年台海导弹危机）
* 1990年10月，中国成为美国的PNTR对象之一，意味着美国对从中国进口的商品以较低NTR税率征收关税

分两步计算各个县对PNTR的exposure程度：

* ①计算美国行业的exposure；定义其为NTR关税的差距，各行业的NTRGap很大，这种variation主要归因于NonNTR税率的变化（NonNTR税率实在PNTR通过前70年设定的，排除其对就业下降进口增长影响到反向因果）

$$
NTRGap_{j}=NonNTRRate_{j}-NTRRate_{j}
$$

<img src="D:\Typora\figs\Did_trade_liberalization_with_China_influence_US_elections\fig3.jpg" alt="image-20220911223033879" style="zoom:30%;float:left" />

* ②将美国各个县的行业就业份额作为权重，计算每个县的平均NTRGap

$$
NTRGap_{c}=\sum_{j}(\frac{L_{jc}}{L_{c}}NTRGap_{j})
$$

* NTRGap只有在制造业、农业、矿产品这些类别下才可计算，服务业的NTRGap为0
* 县级NTRGap的峰比行业NTRGap的峰更靠左因为服务业就业占比很大

### （二）选举数据

* 数据源自Dave Leip的美国总统选举地图集（Dave Leip's Atlas of US Presidential Elections）

* 众议院和参议院的投票情况：每个县在每个选举年获得每个办公室选票的数量；登记选民的数量；选民的投票率

### （三）社会经济特征

* 1990年，各县的制造业就业份额
* 其他人口变量
* 家庭收入中位数
* 拥有学士学位、研究生学位的人口占比
* 非白人人口占比；65所以上；退伍军人人口

<img src="D:\Typora\figs\Did_trade_liberalization_with_China_influence_US_elections\table1.png" alt="image-20220911223033879" style="zoom:100%" />

### （四）进口竞争控制变量

* 县平均NTR率
* 取消纺织品、服装产品配额的exposure（同上式）
* 各个县对于MFA phase-out的exposure
* 各个县对于NAFTA削减关税的exposure

## 四、美中PNTR与美国大选投票的联系

### （一）基准回归策略

* 双重差分：第一重差异NTR Gap；第二重差异贸易政策发生前后
* 首先考察1992-2008年期间的选举（金融危机之前；茶党出现之前）
* 第一列：众议院选举结果；第二列：参议院选举结果；第三列：总统办公室；第四列：选民投票率
* y是county的，但cluster在state

$$
DemShare_{ct}=\theta PostPNTR_{t} × NTRGap_{c}+ PostPNTR_{t}+X_{c}^{`}\gamma+Z_{ct}^{`}\beta+\delta_{c}+\delta_{t}+\epsilon_{ct}
$$

<img src="D:\Typora\figs\Did_trade_liberalization_with_China_influence_US_elections\table2.png" alt="image-20220911223033879" style="zoom:100%" />

### （二）PNTR暴露程度与众议院选举

* 众议院选举结果：第一列，众议院选举中，相对于1990年代，各县对PNTR的Exposure促进了民主党投票份额。将一个县的Exposure从25%分位数移动至75%（从3.5%变成7.5%），民主党候选人选票份额增加2.2%【0.561*(7.5%-3.5%)】
* 原因：民主党人更有可能在立法上采取贸易保护立场；民主党代表在2000年转向反贸易立场是在2000年共和党总统选举后突然发生的，这使得政策选择对于贸易敏感的选民更加突出

### （三）参议院与总统办公室

* 不同于众议院每两年举行一次选举，参议院选举每6年进行一次；总统选举发生在1992、1996年等。每个县的观察结果仅基于该县所在州举行参议院选举的年份
* 参议院选举结果：第二列，参议院选举中，各县对PNTR的Exposure促进了民主党投票份额
* 总统选举结果：第三列，总统选举中，各县对PNTR的Exposure与民主党总统获得选票份额没有统计显著意义
* 原因：frequency——众议院任期短，不太可能采取与选区选民偏好不一致的立场；参议院任期长，参议员比众议员更有可能在任期内的前四年支持贸易自由化，在最后两年面临选举时再顾及选民的立场
* 相比较众议院，参议院和总统梗有可能支持符合整个国家长期利益（而不是区域的个别利益）的政策（例如自由贸易）

### （四）选民投票率

* PNTR Exposure驱动的民主党获票变化可能会受到投票率变化的影响：如已有文献指出，较高的地方工资和就业率会降低美国众议院和其他办公室的选举投票率；你经济周期会增加选民投票率；因此为了验证PNTR Exposure驱动的民主党获票变化是否与投票率相关，作者将投票率作为被解释变量，将其定义为“在选举中投票的人数 ÷ 登记选民人数”
* 选民投票率结果：第四列，PNTR Exposure与选民投票率没有关系。

### （五）区级分析 & 县级分析

讨论使用国会区级数据和县级数据的利弊

* 上述回归基于县级数据，因为县级数据提供了很多好处——县的边界(borders)非常稳定，投票数据能够在很长一段时间内去衡量（跨期也可以比）；而国会区的边界每10年会更改一次，由此会带来两种不便：①在区层面衡量投票数据，但需保证区划保持不变（1992-2000；2002-2010）；②用地区人口加权的平均值来构建跨期（跨期可能导致区划的重构）区级投票数据，但跨期的加权的均值可能无法准确反映重划区的投票。
* 上述回归基于县级数据，如果拆解为国会区级的数据，县商业数据无法被拆解到各个区上。
* 但国会选举实在区级进行的，选民偏好的变化可能导致代表政策选择的变化，因此还是要构建区级的数据进行实证检验

<img src="D:\Typora\figs\Did_trade_liberalization_with_China_influence_US_elections\table3.png" alt="image-20220911223033879" style="zoom:80%" />

* 基于区级数据的回归结果表明：PNTR的Exposure促进了民主党的获票份额
* 基于县级数据的回归和基于区级数据的回归结果高度相似，结果并不是县级汇总数据所驱动的

## 五、稳健性检验

<img src="D:\Typora\figs\Did_trade_liberalization_with_China_influence_US_elections\table4.png" alt="image-20220911223033879" style="zoom:80%" />

### （一）不连续的exposure

* baseline中的exposure属于“treatment intensity”，典型双重差分使用的是Binary Variable。因此提取Exposure前25%和后25%的样本，分别作为treat和control（1和0）
* 第2列表明，exposure较高的县（treat=1）投给民主党选票的份额相对增加

### （二）不包括NTR & 制造业就业份额

* 协变量的相关性：NTR税率既出现在NTRGap的计算中，又在回归等式中出现。不包括NTR税率再次进行估计
* 第3列表明，排除NTR税率项，双重差分项DiD系数与baseline十分接近
* NTRGap大于零的行业主要是制造业、农业、采矿业；导致”县级制造业就业“与NTRGap的相关性高达0.88
* 第4列表明，剔除制造业就业控制变量，核心解释变量的系数虽然变小但仍显著为正

### （三）用2000人口进行加权

* baseline中基于样本期初人口进行加权；更改为基于2000年的人口权重进行加权
* 第5列表明，替换为不同年份的人口作为权重，结果依旧文件

### （四）不包括县的特征

* baseline包括了 ”县级固定效应“ 和 ”县级特征×Post“。
* ”县级固定效应“控制了可能影响投票的县任何不随时间变化的属性，从而提高exposure较大和exposure较小的县的可比性；
* ”县级特征×Post“有助于确保DiD系数所捕捉的趋势中的中断（break），独立于这些属性的趋势的break
* 第6列表明，排除县级的控制变量，DiD项系数不再显著。

### （五）排除县固定效应

* 排除县级固定效应，DiD项系数依然稳健。

<img src="D:\Typora\figs\Did_trade_liberalization_with_China_influence_US_elections\tableA3.png" alt="image-20220911223033879" style="zoom:80%" />

## 六、拓展到2016年

* 背景：Mutz Davis Chinni等人指出，在过去的10年中，共和党候选人获得工业领域的支持，并且更加反对国际贸易。因此文章将研究延伸至2016年，使用广义DiD，允许PNTR的exposure与投票之间的关系因选举年不同而不同

$$
DemShare_{ct}=\sum_{t}\theta_{t}1[year = t ]×NTRGap_{c}+\sum_{t}\gamma_{t}1[year = t]×X_{c}+Z_{ct}^{`}\beta+\delta_{c}+\delta_{t}+\epsilon_{ct}
$$

* θ是1994-2016的时间虚拟变量，其与NTRGap的交互项捕捉了”各年民主党获票与NTRGap的关系“（时间趋势）

<img src="D:\Typora\figs\Did_trade_liberalization_with_China_influence_US_elections\fig4.jpg" alt="image-20220911223033879" style="zoom:40%" />

* 上图画出了每一年的系数和90%置信区间
* 系数直接展示了经济意义——NTRGap从25%分位数移动到75%分位数，对民主党选票的影响（经过了处理，系数和置信区间上下限分别乘以NTR差距的四分位数范围）
* 第一个阶段：1992-2000，PNTR的exposure与民主党投票份额没有关系
* 第二个阶段：2000-2008，系数估计值明显上升；
* 第三个阶段：2008年之后，exposure对民主党选票的影响效应减弱

<img src="D:\Typora\figs\Did_trade_liberalization_with_China_influence_US_elections\table5.png" alt="image-20220911223033879" style="zoom:90%" />

* PNTR的exposure会影响Tea Party：Tea Party的好感度以及Tea Party的积极分子数量

## 七、党派和立法者的投票行为

使用断点回归考察民主党和共和党在与国际贸易相关的法案上投票的差异

哪一方在哪个时间段内更加支持保护主义？

### （一）贸易相关法案的分类

* 将美国众议院的贸易相关法案区分为”赞成贸易“和”反对贸易“，并收集立法者对每一类法案的投票。
* 使用Comparative Agendas开发的主题领域分类方法，，该分类收集了美国国会所有唱名投票的数据，并将其分为子类别 18对外贸易-1802贸易协定/1807关说与进口
* 关注的法案是最终通过的法案，不包括中间程序性的投票
* 排除了不直接设计贸易限制的法案（broad appropriations）
* 根据bill是否设置或者消除壁垒，将法案分为支持贸易和反对贸易，针对每个法案给予排名（1明显的支持；2略微支持；3略微反对；4明显反对）

<img src="D:\Typora\figs\Did_trade_liberalization_with_China_influence_US_elections\tableA4.png" alt="image-20220911223033879" style="zoom:90%" />

### （二）识别策略

众议院议员对国际贸易法案的投票与党派之间的关系
$$
ProTrade_{dh}=\alpha+\beta Democrat_{dh}+\epsilon_{dh}
$$

* d代表选取，h代表在职两年的国会
* ProTrade代表特定国会所在的两年期内所投的赞成贸易票的份额
* Democrat代理Party affiliation；Democrat=1代表民主党人，Democrat=0代表其他
* 为了保证β的无偏性，党派关系Democrat应与误差项不相关。构建自然实验：选取民主党共和党险胜的立法选票，这样能够保证民主党的获胜是偶然的，其除了获胜成为了Treat之外，其他条件无异于Control。（随机意味着任何政党都不能操作选举）
* 如果选举结果是可操纵的，那么Margin (assignment variable) 在断点0处不连续。使用McCrary Test检验，（如图A.3左上所示）
* 在临界点检验国会选区的特征（家庭收入中位数、非白人、退伍军人、学士学位人口比例）（如图A.3其他图所示）

定义Margin为民主党和共和党在国会h 选区d选举中获得选票的份额差异
$$
Margin_{dh}=VoteShare_{dh}^{Democrat}-VoteShare_{dh}^{Republican}
$$
<img src="D:\Typora\figs\Did_trade_liberalization_with_China_influence_US_elections\figA3.png" alt="image-20220911223033879" style="zoom:90%" />

### （三）结果

* 表6检验了三个恒定周期的选区（国会选区特征在三个时间段内不变）
* 使用了参数和非参数估计
* 第一列表明：90年代民主党在贸易问题上所投的法案于共和党类似(PanelA)；90年代民主党稍微更加支持自由贸易
* 第二列表明：在2002-2010年间，民主党在立法投票中，体现出比共和党更反对贸易的倾向
* 第三列表明：在2012-2014年间，这种倾向消失了（但这一时期的相关法案比较少，双方可能都有反对贸易的倾向）

<img src="D:\Typora\figs\Did_trade_liberalization_with_China_influence_US_elections\table6.png" alt="image-20220911223033879" style="zoom:90%" />

* 为什么民主党在2000年代相较于共和党会变得“反对贸易”：①总统所在政党影响贸易法案的投票；②期初民主党作为代表的选区更容易受到PNTR shock的影响，因此他们改变了对贸易法案的看法。
* 在民主党总统比尔克林顿改任共和党总统乔治W布什之后，贸易相关法案的投票急剧下降(63%-40%)；共和党支持贸易的投票从72%上升至80%
* 共和党没有在2000年初采取贸易保护主义立场的原因：共和党代表要支持共和党总统布什政府的亲贸易立场；在民主党的大本营中，PNTR shock给民主党的收益更大，大本营选取会以较大的优势获胜，这些选区的收益不会引起共和党人的关注，因为这不会导致共和党代表的选区数量发生变化。

<img src="D:\Typora\figs\Did_trade_liberalization_with_China_influence_US_elections\tableA6.png" alt="image-20220911223033879" style="zoom:70%" />

* 民主党代表和共和党代表对贸易相关法案的投票(Y)演变是否受PNTR exposure高或低的地区(X)驱动
* 将地区划分为“高NTRGap”地区和“低NTRGap”地区

<img src="D:\Typora\figs\Did_trade_liberalization_with_China_influence_US_elections\table7.png" alt="image-20220911223033879" style="zoom:90%" />

## 八、结论

我们发现，与 1990 年代相比，在 2000 年代的前十年，美国各县通过 PNTR 更容易受到来自中国的激烈竞争，在国会选举中投给民主党的选票份额相对增加，而且这种转变在两个县都存在 - 并构建了地区级数据。 就经济意义而言，我们发现，在 2000 年代，将一个县从 PNTR 暴露的第 25 个百分位移动到第 75 个百分位，与民主党在众议院选举中的投票份额相对增加 2.2 个百分点或 4.6 个百分点相关。 相对于在 2000 年国会选举中投给民主党的平均票数增加百分比。 这种关系对于替代规格（不包括 NTR 关税税率或制造业就业份额）和替代权重是稳健的。 我们还表明，随着共和党茶党派的崛起，这种投票向民主党的转变在 2010 年代逐渐减弱，尽管 2010 年代的这种变化并未得到精确估计。 相关结果表明，接触 PNTR 与茶党活动的某些方面有关。

 在论文的第二部分，我们发现证据表明，贸易自由化和投票之间的关系可以通过民主党和共和党代表随着时间的推移而做出的政策选择来解释。 使用回归不连续性方法，我们发现 2000 年代初期的众议院民主党人比他们的共和党同事投票反对支持自由贸易的立法的可能性要大得多，这与这一时期在贸易领域对民主党人的更强选举支持一致。 然而，到 2000 年代的第二个十年，随着共和党茶党派的崛起，两党在贸易相关法案上的投票相似，为民主党失去提振提供了理由，尽管 在此期间考虑的贸易票据很少。 总而言之，我们的结果与贸易敏感地区的选民将支持转向倡导符合其经济利益的贸易政策的政党一致。
