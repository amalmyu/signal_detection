<link rel="stylesheet" type="text/css" href="auto-number-title.css" />

# signal_detection

## 简介
检测药品不良反应（adverse drug reaction, ADR）信号。

## ADR数据挖掘方法

表1 药品不良反应四格表
|  | 目标不良反应 | 其他不良反应 | 合计 |
|---|---|---|---|
| 目标药品 | a | b | a+b |
| 其他药品 | c | d | c+d |
| 合计 | a+c | b+d | N=a+b+c+d |

a：目标药品的目标不良反应报告数<br> 
b：目标药品的其他不良反应报告数<br> 
c：其他药品的目标不良反应报告数<br> 
d：其他药品的其他不良反应报告数<br> 

如果某种药品与不良反应之间的计算结果大于规定阈值，则称之为失衡，提示产生一个信号。<br> 

### 频数类ADR数据挖掘方法

#### 报告比值比法（ROR）
公式<br> 

$$ROR = \frac{a/c}{b/d}$$

$$ROR{\kern 2pt}95\\%CI=e^{ln(ROR)\pm 1.96 \sqrt{\left(\frac{1}{a}+\frac{1}{b}+\frac{1}{c}+\frac{1}{d}\right)}}$$

\* $95\\%CI$ 表示95\%置信区间

#### 比例报告比法（PRR）
公式<br> 

$$PRR=\frac{\frac{a}{(a+b)}}{\frac{c}{(c+d)}}$$

$$PRR{\kern 2pt}95\\%CI=e^{ln(PRR)\pm 1.96 \sqrt{\left(\frac{1}{a}+\frac{1}{a+b}+\frac{1}{c}+\frac{1}{c+d}\right)}}$$

### 贝叶斯类ADR数据挖掘方法

#### 贝叶斯置信递进神经网络法（BCPNN）
公式<br> 


$$IC=log_2\frac{a(a+b+c+d)}{(a+b)(a+c)}$$

$$\gamma = \gamma_{11}\frac{(N+\alpha)(N+\beta)}{(a+b+\alpha_1)(a+b+\beta_1)}$$

$$E(IC)=log_2\frac{(a+\gamma_{11})(N+\alpha)(N+\beta)}{(N+\gamma)(a+b+\alpha_1)(a+c+\beta_1)}$$

$$V(IC)=\left(\frac{1}{\ln2}\right)^2\left[\frac{N-a+\gamma-\gamma_{11}}{(a+\gamma_{11})(1+N+\gamma)}+\frac{N-a-b+\alpha-\alpha_1}{(a+b+\alpha_1)(1+N+\alpha)}+\frac{N-a-c+\beta-\beta_1}{(a+c+\beta_1)(1+N+\beta)}\right]$$

$$IC025=E(IC)-2\sqrt{V(IC)}$$

$IC025$ 为 $95\\%CI$ 下限

$\gamma_{11}=1$， $\alpha_1=\beta_1=1$， $\alpha=\beta=2$
#### 多项伽马-泊松缩量评估法（MGPS）
公式<br> 
$$EBGM=\frac{a(a+b+c+d)}{(a+b)(a+c)}$$
