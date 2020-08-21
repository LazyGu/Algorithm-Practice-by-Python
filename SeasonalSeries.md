# Algorithm-Practice-by-Python
```
import numpy as np

a = np.array([[5465,4564,45645,15645],[456465,13545,1312,56544],[2135,1321,54654,123513]])

m,n = a.shape

amean = a.mean()
cmean = a.mean(axis=0)
r = cmean/amean
w = np.arange(1, m+1)
yh = w.dot(a.sum(axis=1))/w.sum()
yj = yh/n
yjh = yj*r
print("下一年度个月预测值为：", np.round(yjh))
```
