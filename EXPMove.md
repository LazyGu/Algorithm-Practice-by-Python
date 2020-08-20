# Exponential Smoothing
```
import numpy as np
import pandas as pd

y = np.array([1786,1768718,168786,16878671,54546,768456,7987564,3875486,54678646,4534846,8464848,632454,7951,3483,34,454])

class Single_Exponential_Smoothing:
    def ExpMove(y, a):
        n = len(y)
        M = np.zeros(n)
        M[0] = (y[0]+y[1])/2
        for i in range(1, len(y)):
            M[i] = a * y[i-1] + (1-a) * M[i-1]
        return M

    yt1 = ExpMove(y, 0.2)
    yt2 = ExpMove(y, 0.5)
    yt3 = ExpMove(y, 0.8)

    s1 = np.sqrt(((y-yt1)**2).mean())
    s2 = np.sqrt(((y-yt2)**2).mean())
    s3 = np.sqrt(((y-yt3)**2).mean())

    d = pd.DataFrame(np.c_[y, yt1, yt2, yt3])
    f = pd.ExcelWriter("Example.xlsx")
    d.to_excel(f)
    f.close()

    print("预测的标准误差分别为：", round(s1), round(s2), round(s3))
    yh = 0.8*y[-1] + 0.2*yt3[-1]
    print("下一期的预测值为：", round(yh))
    
class Quadratic_Exponential_Smoothing:
    n = len(y)
    alpha = 0.3
    yh = np.zeros(n)
    s1 = np.zeros(n)
    s2 = np.zeros(n)
    s1[0] = y[0]
    s2[0] = y[0]
    for i in range(1,n):
        s1[i] = alpha*y[i] + (1-alpha)*s1[i-1]
        s2[i] = alpha*s1[i] + (1-alpha)*s2[i-1]
        yh[i] = 2*s1[i-1] - s2[i-1] + alpha/(1-alpha) * (s1[i-1]-s2[i-1]) #直线趋势模型
    at = 2*s1[-1] - s2[-2]
    bt = alpha/(1-alpha) * (s1[-1]-s2[-1])
    m = np.array([1,2])
    yh2 = at + bt * m
    print("预测值为：", yh2)
    d = pd.DataFrame(np.c_[y, s1, s2,yh])
    f = pd.ExcelWriter("Example02.xlsx")
    d.to_excel(f)
    f.close()
```
