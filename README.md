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
$$
ROR = \frac{a/c}/{b/d}
$$
