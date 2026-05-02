# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 02-05-2026

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

# Load dataset
data = pd.read_csv('/content/chennai_temperature_120days.csv',
                   parse_dates=['Date'],
                   index_col='Date')

# Renaming the 'Avg_Temp_C' column to 'Temp' as it seems to be the intended temperature column
data.rename(columns={'Avg_Temp_C': 'Temp'}, inplace=True)

# 1. Original Data
plt.figure(figsize=(12, 6))
plt.plot(data['Temp'])
plt.title('Original Time Series')
plt.xlabel('Date')
plt.ylabel('Temperature')
plt.grid(True)
plt.show()

# 2. Log Transformation
data['Temp_Log'] = np.log(data['Temp'])

plt.figure(figsize=(12, 6))
plt.plot(data['Temp_Log'])
plt.title('Log Transformation')
plt.xlabel('Date')
plt.ylabel('Log(Temperature)')
plt.grid(True)
plt.show()

# 3. Regular Differencing
data['Temp_Diff'] = data['Temp'].diff(1)

plt.figure(figsize=(12, 6))
plt.plot(data['Temp_Diff'])
plt.title('Regular Differencing')
plt.xlabel('Date')
plt.ylabel('Difference')
plt.grid(True)
plt.show()

# 4. Seasonal Adjustments
data['Temp_Seasonal_Diff'] = data['Temp'].diff(7)

plt.figure(figsize=(12, 6))
plt.plot(data['Temp_Seasonal_Diff'])
plt.title('Seasonal Adjustments')
plt.xlabel('Date')
plt.ylabel('Seasonal Difference')
plt.grid(True)
plt.show()

# 5. Combined Transformations
data['Temp_Log_Diff_Seasonal'] = data['Temp_Log'].diff(1).diff(7)

plt.figure(figsize=(12, 6))
plt.plot(data['Temp_Log_Diff_Seasonal'])
plt.title('LOG, REGULAR, AND SEASONAL DIFFERENCING')
plt.xlabel('Date')
plt.ylabel('Transformed Values')
plt.grid(True)
plt.show()

# Decomposition
decomposition = seasonal_decompose(data['Temp'], model='additive', period=7)

decomposition.plot()
plt.suptitle('Seasonal Decomposition', y=1.02)
plt.tight_layout()
plt.show()
```

### OUTPUT:
<img width="1006" height="546" alt="image" src="https://github.com/user-attachments/assets/87856585-9b9d-440c-aeff-58d2b6eb6014" />


<img width="1014" height="547" alt="1 2" src="https://github.com/user-attachments/assets/23ae0e91-4e22-4b5c-bd2c-3bc78efecdc9" />

REGULAR DIFFERENCING:

<img width="1004" height="547" alt="1 3" src="https://github.com/user-attachments/assets/e8c98857-6f4a-4101-9009-1ecb344d86d5" />

SEASONAL ADJUSTMENT:
<img width="1005" height="547" alt="1 4" src="https://github.com/user-attachments/assets/cbb830a8-eddf-4ab2-b0d2-b4cba4ce46ec" />


LOG TRANSFORMATION:

<img width="1018" height="547" alt="1 5" src="https://github.com/user-attachments/assets/6cead831-71f2-4b8d-94e1-3185000d927b" />

<img width="630" height="494" alt="1 6" src="https://github.com/user-attachments/assets/0075dcee-ffd1-4559-bcf6-2c16a967467a" />

### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
