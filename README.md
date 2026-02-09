# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data=pd.read_csv('/content/car_price.csv')
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
data=pd.read_csv('/content/car_price.csv')

data['Mileage_diff']=data['Mileage']-data['Mileage'].shift(1)
result = seasonal_decompose(data['Mileage'].dropna(), model='additive', period=12)
data['Mileage_sea_diff']=result.resid
data['Mileage_log'] = np.log(data['Mileage'])
data['Mileage_log_diff']=data['Mileage_log']-data['Mileage_log'].shift(1)
result = seasonal_decompose(data['Mileage_log_diff'].dropna(), model='additive', period=12)
data['Mileage_log_seasonal_diff']=result.resid

plt.figure(figsize=(12, 18))
plt.subplot(6, 1, 2)
plt.plot(data['Mileage_diff'], label='Regular Difference')
plt.legend(loc='best')
plt.title('Regular Differencing')
plt.xlabel('Year')
plt.ylabel('Differenced No of Mileage')
plt.subplot(6, 1, 3)
plt.plot(data['Mileage_sea_diff'], label='Seasonal Adjustment')
plt.legend(loc='best')
plt.title('Seasonal Adjustment')
plt.xlabel('Year')
plt.ylabel('Seasonally Adjusted No of Mileage')
plt.subplot(6, 1, 4)
plt.plot(data['Mileage_log'], label='Log Transformation')
plt.legend(loc='best')
plt.title('Log Transformation')
plt.xlabel('Year')
plt.ylabel('Log(No of Mileage)')
plt.subplot(6, 1, 5)
plt.plot(data['Mileage_log_diff'], label='Log Transformation and Regular Differencing')
plt.legend(loc='best')
plt.title('Log Transformation and Regular Differencing')
plt.xlabel('Year')
plt.ylabel('RDiff(Log(No of Mileage))')
plt.subplot(6, 1, 6)
plt.plot(data['Mileage_log_seasonal_diff'], label='Log Transformation and regular Diff')
plt.legend(loc='best')
plt.title('Log Transformation and Regular Differencing and Seasonal Differencing')
plt.xlabel('Year')
plt.ylabel('SDiff(RDiff(Log(No of Mileage)))')
plt.tight_layout()
plt.show()
### OUTPUT:
<img width="1261" height="323" alt="image" src="https://github.com/user-attachments/assets/637376a8-7e98-4d62-82f4-356882712bdc" />
<img width="1263" height="326" alt="image" src="https://github.com/user-attachments/assets/a86531be-6c51-485f-b56a-18440a9545b9" />
<img width="1264" height="335" alt="image" src="https://github.com/user-attachments/assets/c6f93805-4af6-48bc-a418-976dfe4f4ee4" />
<img width="1267" height="328" alt="image" src="https://github.com/user-attachments/assets/ff2d6ddd-bab6-450a-b979-ffaf0096add9" />


### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
