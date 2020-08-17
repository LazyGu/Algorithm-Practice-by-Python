# SMA
```
import numpy as np
y = np.array([465,561,4645,12354,54354,4564,44])

class SMA_Method01:
    def MoveAverage(y, N):
        Mt = ['*']*N  # 设移动平均项数为N，结果前N项为 '*'
        for i in range (N+1, len(y)+2):  # 从第N+1项开始得出预测值，一直到第49项
            M = y[i-(N+1):i-1].mean()  # 索引N+1前三项并求得平均值
            Mt.append(round(M))  # 均值取整并加入列表Mt中
        return Mt

    yt3 = MoveAverage(y,3)
    s3 = np.sqrt(((y[3:] - yt3[3:-1])**2).mean())  # 算数平方根
    yt5 = MoveAverage(y,5)
    s5 = np.sqrt(((y[5:] - yt3[5:-1])**2).mean())
    print ('N=3时，预测值为：', yt3, ', 预测标准差为：', s3)
    print ('N=5时，预测值为：', yt5, ', 预测标准差为：', s5)

    
class SMA_Method02:
    def sma(arr, n):
        weights = np.ones(n)/n
        return np.convolve(weights, arr)[n-1:-n+1]  # 卷积法
    yt5 = sma(y, 5)
    for i in range(0, len(yt5)): 
        yt5[i] = round(yt5[i])
    print(yt5)
```
