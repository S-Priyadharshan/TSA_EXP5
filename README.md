# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```python

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.arima_process import ArmaProcess
from statsmodels.graphics.tsaplots import plot_acf, plot_pacf
from statsmodels.tsa.seasonal import seasonal_decompose

df = pd.read_csv("/content/co2_gr_mlo.csv", comment="#")

df['year'] = pd.to_datetime(df['year'], format='%Y')
df.set_index('year', inplace=True)

df['Total_CO2'] = df['ann inc'] + df['unc']

co2_data = df['Total_CO2']

decomposition = seasonal_decompose(co2_data, model='additive', period=2)

trend = decomposition.trend
seasonal = decomposition.seasonal
residuals = decomposition.resid

plt.figure(figsize=(12, 6))
plt.plot(co2_data, label='Original CO2 Data')
plt.title('Original CO2 Data')
plt.legend()
plt.show()

plt.figure(figsize=(12, 6))
plt.plot(seasonal, label='Seasonal Component', color='orange')
plt.title('Seasonal Component')
plt.legend()
plt.show()

plt.figure(figsize=(12, 6))
plt.plot(trend, label='Trend Component', color='green')
plt.title('Trend Component')
plt.legend()
plt.show()

plt.figure(figsize=(12, 6))
plt.plot(residuals, label='Residuals', color='red')
plt.title('Residuals')
plt.legend()
plt.show()


plt.figure(figsize=(12, 8))
decomposition.plot()
plt.show()


```
### OUTPUT:
FIRST FIVE ROWS:
<img width="347" height="284" alt="image" src="https://github.com/user-attachments/assets/152d0d7b-7c94-4074-bf75-031d31c732f8" />

PLOTTING THE DATA:
<img width="981" height="528" alt="image" src="https://github.com/user-attachments/assets/7337af5c-ccc2-4e94-9c99-fb579b4d8271" />

SEASONAL PLOT REPRESENTATION:
<img width="1002" height="528" alt="image" src="https://github.com/user-attachments/assets/da4088bb-7025-4727-b153-62e886b7bf33" />

TREND PLOT REPRESENTATION:
<img width="981" height="528" alt="image" src="https://github.com/user-attachments/assets/8dacb9b4-35f1-42b8-a7a5-b01c2eead616" />

RESIDUALS REPRESENTATION:
<img width="993" height="528" alt="image" src="https://github.com/user-attachments/assets/527a7ae0-d2e4-426b-a1f8-ea16ebc57af4" />

OVERAL REPRESENTATION:
<img width="630" height="470" alt="image" src="https://github.com/user-attachments/assets/57913b31-bb8d-46b3-80af-bbd9a564d315" />

### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
