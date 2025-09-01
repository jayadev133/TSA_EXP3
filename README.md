# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 01/09/2025

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
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

file_path = "/content/Coffe_sales.xlsx"
df = pd.ExcelFile(file_path)

print("Available sheets:", df.sheet_names)

data_df = pd.read_excel(file_path, sheet_name=0)

print(data_df.head())

data = data_df['money'].dropna().values

lags = range(35)

autocorr_values = []

mean_data = np.mean(data)
variance_data = np.var(data)

for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum((np.array(data[:-lag]) - mean_data) *
                          (np.array(data[lag:]) - mean_data)) / len(data)
        autocorr_values.append(auto_cov / variance_data)

plt.figure(figsize=(10, 6))
plt.stem(lags, autocorr_values, basefmt=" ")
plt.title("Autocorrelation Function (ACF)")
plt.xlabel("Lag")
plt.ylabel("Autocorrelation")
plt.grid(True)
plt.show()
```
### OUTPUT:
<img width="846" height="547" alt="exp3 ts pic" src="https://github.com/user-attachments/assets/5a4ca035-5160-499e-8d1a-d191eec91525" />

### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
