#### Developed by: Thiyagarajan A
#### Reg.no: 212222240110
#### Date:
# Ex.No: 08     MOVINTG AVERAGE MODEL AND EXPONENTIAL SMOOTHING
 
### AIM:
To implement Moving Average Model and Exponential smoothing Using Python.
### ALGORITHM:
1. Import necessary libraries
2. Read the google stack price - time series data from a CSV file,Display the shape and the first 20 rows of
the dataset
3. Set the figure size for plots
4. Suppress warnings
5. Plot the first 50 values of the 'Value' column
6. Perform rolling average transformation with a window size of 5
7. Display the first 10 values of the rolling mean
8. Perform rolling average transformation with a window size of 10
9. Create a new figure for plotting,Plot the original data and fitted value
10. Show the plot
11. Also perform exponential smoothing and plot the graph
### PROGRAM:
```
# Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt
import warnings

# Read the Google stock price time series data from a CSV file
df = pd.read_csv('Google_Stock_Price_Train.csv')  # Replace with your dataset
print("Dataset Shape:", df.shape)
print(df.head(5))  # Display the first 20 rows

# Convert the 'Close' column to numeric, handling any errors
df['Close'] = pd.to_numeric(df['Close'].str.replace(',', ''), errors='coerce')

# Suppress warnings
warnings.filterwarnings("ignore")

# Set figure size for plots
plt.figure(figsize=(12, 6))

# Plot the first 50 values of the 'Close' column
df['Close'][:50].plot()
plt.title("First 50 Values of Google Stock Prices (Close)")
plt.show()

# Perform rolling average transformation with a window size of 5
df['Rolling_Mean_5'] = df['Close'].rolling(window=5).mean()

# Display the first 10 values of the rolling mean
print(df[['Close', 'Rolling_Mean_5']].head(10))

# Perform rolling average transformation with a window size of 10
df['Rolling_Mean_10'] = df['Close'].rolling(window=10).mean()

# Create a new figure for plotting original data and fitted values
plt.figure(figsize=(12, 6))

# Plot the original data and fitted values
plt.plot(df['Close'], label='Original Data')
plt.plot(df['Rolling_Mean_5'], label='Rolling Mean (Window=5)', color='orange')
plt.plot(df['Rolling_Mean_10'], label='Rolling Mean (Window=10)', color='green')

# Add title and labels
plt.title('Moving Average on Google Stock Prices (Close)')
plt.legend()
plt.show()

# Exponential Smoothing
df['Exponential_Smoothing'] = df['Close'].ewm(span=5, adjust=False).mean()

# Plot the exponential smoothing along with the original data
plt.figure(figsize=(12, 6))
plt.plot(df['Close'], label='Original Data')
plt.plot(df['Exponential_Smoothing'], label='Exponential Smoothing (span=5)', color='red')

plt.title('Exponential Smoothing on Google Stock Prices (Close)')
plt.legend()
plt.show()
```
### OUTPUT:
![image](https://github.com/user-attachments/assets/6476203b-45f5-4283-8183-a41e0be55f25)
![image](https://github.com/user-attachments/assets/48a9a565-f99a-4000-87f7-297b257bf81b)
![image](https://github.com/user-attachments/assets/61dee739-904e-4ea8-a4bc-7726e66a9b63)
![image](https://github.com/user-attachments/assets/4a21c823-4dff-4d0b-9e8f-f454c4a05033)

![image](https://github.com/user-attachments/assets/754686c3-641d-41b9-87a3-1b58d0758cc3)




### RESULT:
Thus the implementation of the Moving Average Model and Exponential smoothing using python was successfully completed.
