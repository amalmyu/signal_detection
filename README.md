<link rel="stylesheet" type="text/css" href="auto-number-title.css" />
# signal_detection

# 简介
检测药物不良反应信号。

# 方法

表1 药品不良反应四格表
|   |目标不良反应   |其他不良反应   |
| ------------ | ------------ | ------------ |
|目标药品   |a   |b   |
|其他药品   |c   |d   |

a：目标药品的目标不良反应报告数<br> 
b：目标药品的其他不良反应报告数<br> 
c：其他药品的目标不良反应报告数<br> 
d：其他药品的其他不良反应报告数<br> 

如果某种药品与不良反应之间的计算结果大于规定阈值，则称之为失衡，提示产生一个信号。<br> 

## 报告比值比法（ROR）
公式<br> 
$$ROR = \frac{a/c}{b/d}$$
$$ROR{\kern 2pt}95\\%CI=e^{ln(ROR)\pm 1.96 \sqrt{\left(\frac{1}{a}+\frac{1}{b}+\frac{1}{c}+\frac{1}{d}\right)}}$$
\* $95\\%CI$ 表示95\%置信区间

## 比例报告比法（PRR）
$$PRR=\frac{\frac{a}{(a+b)}}{\frac{c}{(c+d)}}$$
$$PRR{\kern 2pt}95\\%CI=e^{ln(PRR)\pm 1.96 \sqrt{\left(\frac{1}{a}+\frac{1}{a+b}+\frac{1}{c}+\frac{1}{c+d}\right)}}$$
