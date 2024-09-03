### Name: KARTHIKEYAN R
### Register No: 212222240045
### Date:
# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
### AIM:
To Implement Linear and Polynomial Trend Estiamtion Using Python.

### ALGORITHM:
1.Import necessary libraries (NumPy, Matplotlib)

2.Load the dataset

3.Calculate the linear trend values using least square method

4.Calculate the polynomial trend values using least square method

5.End the program

End the program
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import PolynomialFeatures
df = pd.read_csv('/content/rainfall.csv')
df.head(5)
# Check the actual column names in your DataFrame
print(df.columns)

# Assuming the date column is named 'date' 
df['date'] = pd.to_datetime(df['date'])  # Convert 'date' column to datetime
df = df.sort_values('date')

# Convert 'date' column to datetime, handling potential errors
df['date'] = pd.to_datetime(df['date'], errors='coerce')

# Drop rows with invalid dates (if any)
df = df.dropna(subset=['date'])

# Now apply the toordinal() function
df['Date_ordinal'] = df['date'].apply(lambda x: x.toordinal())
X = df['Date_ordinal'].values.reshape(-1, 1)
print(df.columns)

```
A - LINEAR TREND ESTIMATION
```
y = df['rainfall'].values  # Use 'rainfall' column instead of 'Price'
if 'Close' in df.columns:
    y = df['Close'].values
linear_model = LinearRegression()
linear_model.fit(X, y)
df['Linear_Trend'] = linear_model.predict(X)
plt.figure(figsize=(10, 6))
plt.plot(df['date'], df['rainfall'], label='Original Data', color='blue')  # Use 'date' and 'rainfall'
plt.plot(df['date'], df['Linear_Trend'], color='yellow', label='Linear Trend')
plt.title('Linear Trend Estimation')
plt.xlabel('Date')
plt.ylabel('Rainfall') # Changed y-axis label to reflect the 'rainfall' data
plt.legend()
plt.grid(True)
plt.show()
```

B- POLYNOMIAL TREND ESTIMATION
```
poly_features = PolynomialFeatures(degree=2)
X_poly = poly_features.fit_transform(X)
poly_model = LinearRegression()
poly_model.fit(X_poly, y)
df['Polynomial_Trend'] = poly_model.predict(X_poly)
plt.figure(figsize=(10, 6))
plt.plot(df['date'], df['rainfall'], label='Original Data', color='blue') # Changed 'Date' to 'date' and 'Price' to 'rainfall'
plt.plot(df['date'], df['Polynomial_Trend'], color='green', label='Polynomial Trend (Degree 2)')
plt.title('Polynomial Trend Estimation')
plt.xlabel('Date')
plt.ylabel('Rainfall') # Changed y-axis label to reflect the 'rainfall' data
plt.legend()
plt.grid(True)
plt.show()
```

## OUTPUT 

![Screenshot 2024-09-03 200825](https://github.com/user-attachments/assets/66412a24-df14-481d-a420-cbc066c93d1a)

A - LINEAR TREND ESTIMATION

![image](https://github.com/user-attachments/assets/e06f0a53-a05f-4580-aabc-84ae3669183c)

B- POLYNOMIAL TREND ESTIMATION

![image](https://github.com/user-attachments/assets/694358cb-f5d0-4542-809a-88dcd284d1c8)



### RESULT:
Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
