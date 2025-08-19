# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date:19-08-2025 
### NAME: GANJI MUNI MADHURI
### REGISTER NUMBER:212223230060
### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

data=pd.read_csv('/content/ABB_15minute.cs')
data.head()

data['date']=pd.to_datetime(data['date'])
data.set_index('date',inplace=True)
data['open_diff']=data['open']-data['open'].shift(1)

result = seasonal_decompose(data['open'], model='additive', period=12)
data['open_sea_diff']=result.resid

data['open_log'] = np.log(data['open'])
data['open_log_diff']=data['open_log']-data['open_log'].shift(1)

result = seasonal_decompose(data['open_log_diff'].dropna(), model='additive', period=12)
data['open_log_seasonal_diff']=result.resid

plt.figure(figsize=(16, 16))

plt.subplot(6, 1, 1)
plt.plot(data['open'], label='Original')
plt.legend(loc='best')
plt.title('Original Data')
plt.xlabel('date')
plt.ylabel('open')

plt.subplot(6, 1, 2)
plt.plot(data['open_diff'], label='Regular Difference')
plt.legend(loc='best')
plt.title('Regular Differencing')
plt.xlabel('date')
plt.ylabel('open')

plt.subplot(6, 1, 3)
plt.plot(data['open_sea_diff'], label='Seasonal Adjustment')
plt.legend(loc='best')
plt.title('Seasonal Adjustment')
plt.xlabel('date')
plt.ylabel('open')

plt.subplot(6, 1, 4)
plt.plot(data['open_log'], label='Log Transformation')
plt.legend(loc='best')
plt.title('Log Transformation')
plt.xlabel('Date')
plt.ylabel('Log(No of open)')

plt.subplot(6, 1, 5)
plt.plot(data['open_log_diff'], label='Log Transformation and Regular Differencing')
plt.legend(loc='best')
plt.title('Log Transformation and Regular Differencing')
plt.xlabel('Date')
plt.ylabel('RDiff(Log(No of open))')

plt.figure(figsize=(16, 16))
plt.subplot(6, 1, 6)
plt.plot(data['open_log_seasonal_diff'], label='Log Transformation and regular Differencing and Seasonal Differencing')
plt.legend(loc='best')
plt.title('Log Transformation and Regular Differencing and Seasonal Differencing')
plt.xlabel('Date')
plt.ylabel('SDiff(RDiff(Log(No of open)))')

plt.tight_layout()
plt.show()

data.plot(kind='line')
```

### OUTPUT:
ORIGINAL DATASET:
<img width="1109" height="298" alt="image" src="https://github.com/user-attachments/assets/59af7a91-22e8-4048-a52d-1671bc81be44" />


REGULAR DIFFERENCING:
<img width="1109" height="296" alt="image" src="https://github.com/user-attachments/assets/3750653b-b5fc-4c1d-97d7-ab3654757049" />


SEASONAL ADJUSTMENT:

<img width="1105" height="305" alt="image" src="https://github.com/user-attachments/assets/dda59d9a-6351-41f0-8ada-2c41c47f25ab" />


LOG TRANSFORMATION:
<img width="1174" height="340" alt="image" src="https://github.com/user-attachments/assets/4d7d1a11-3f88-4afc-b5cb-1ee1303a1d2a" />
<img width="1281" height="331" alt="image" src="https://github.com/user-attachments/assets/5b55ce56-a3b8-47dc-b2b4-5f783cbaa3d0" />
<img width="1435" height="310" alt="image" src="https://github.com/user-attachments/assets/54e90147-4c2f-454e-bb55-c1e2e6928365" />


OVERALL VIEW:
<img width="1036" height="652" alt="image" src="https://github.com/user-attachments/assets/89812de9-b82c-496f-8b73-24e6ac31342a" />



### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
