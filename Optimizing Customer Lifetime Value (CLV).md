# Optimizing Customer Lifetime Value (CLV)
import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_squared_error

# Load customer data into a pandas DataFrame
customer_data = pd.read_csv("customer_data.csv")

# Extract target variable (CLV) and features
target = customer_data["CLV"]
features = customer_data.drop("CLV", axis=1)

# Split the data into training and testing sets
train_features, test_features, train_target, test_target = train_test_split(features, target, test_size=0.2)

# Train a linear regression model
lin_reg = LinearRegression()
lin_reg.fit(train_features, train_target)
lin_reg_pred = lin_reg.predict(test_features)
lin_reg_mse = mean_squared_error(test_target, lin_reg_pred)

# Train a random forest regression model
rf_reg = RandomForestRegressor()
rf_reg.fit(train_features, train_target)
rf_reg_pred = rf_reg.predict(test_features)
rf_reg_mse = mean_squared_error(test_target, rf_reg_pred)

# Compare the mean squared errors of the two models
if lin_reg_mse < rf_reg_mse:
    print("Linear Regression model performs better with MSE:", lin_reg_mse)
else:
    print("Random Forest Regression model performs better with MSE:", rf_reg_mse)
