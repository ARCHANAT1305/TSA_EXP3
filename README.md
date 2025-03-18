# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
### Date:18/03/25 

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
NAME : ARCHANA T
REGISTER NUMBER : 212223240013
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
file_path = "MSFT(2000-2023).csv"  
df = pd.read_csv(file_path)
new_data = df["Adj Close"].dropna().tolist()
N = len(new_data)
lags = range(min(35, N))
autocorr_values = []
mean_data = np.mean(new_data)
variance_data = np.var(new_data)
for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((new_data[:-lag] - mean_data) * (new_data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data) 
plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values)  
plt.title('Autocorrelation of Microsoft Adjusted Close Prices (2000-2023)')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.show()
```


### OUTPUT:
![image](https://github.com/user-attachments/assets/743d96bf-f574-452c-9e2f-d0a22553dbc5)


### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
