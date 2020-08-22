# ARMA
```
import pandas as pd
import numpy as np
import statsmodels.api as sm
import matplotlib.pyplot as plt
from statsmodels.graphics.tsaplots import plot_acf, plot_pacf

plt.rc('axes', unicode_minus=False)
plt.rc('font', family='SimHei')
plt.rc('font', size=10)

nums = [***SECRET***]
years = range(49)
data = pd.Series(nums, index=pd.date_range('1/1/2016', freq='M', periods = 48))
plt.plot(data, '-*')

ax1 = plt.subplot(121)
plot_acf(data, ax=ax1, title='自相关')
ax2 = plt.subplot(122)
plot_pacf(data, ax=ax2, title='偏自相关')

for i in range(0,6):
    for j in range(1,2):
        md = sm.tsa.ARMA(data,(i,j)).fit()
        print([i, j, md.aic, md.bic])
zmd = sm.tsa.ARMA(data,(3,1)).fit()
print(zmd.summary())

residuals = pd.DataFrame(zmd.resid)
fig, ax = plt.subplots(1,2)
residuals.plot(title='残差', ax=ax[0])
residuals.plot(kind='kde', title='密度', ax=ax[1])
plt.legend('')
plt.ylabel('')

dhat = zmd.predict()
plt.figure()
plt.plot(years[-12:], data.values[-12:], 'o-k')
plt.plot(years[-12:], dhat.values[-12:], 'p--')
plt.legend(('原始值', '预测值'))
dnext = zmd.predict(data.shape[0],data.shape[0])
print(dnext)
plt.show()
```
