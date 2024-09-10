# SGD-Regressor-for-Multivariate-Linear-Regression

## AIM:
To write a program to predict the price of the house and number of occupants in the house with SGD regressor.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Start
2.Data Preparation
3.Hypothesis Definition
4.Cost Function
5.Parameter Update Rule
6.Iterative Training
7.Model Evaluation
8.End
## Program:
```
Program to implement the multivariate linear regression model for predicting the price of the house and number of occupants in the house with SGD regressor.
Developed by: LOGA MITHRA R
RegisterNumber:  212223100027
```
```
import numpy as np
import pandas as pd
from sklearn.datasets import fetch_california_housing
from sklearn.linear_model import SGDRegressor
from sklearn.multioutput import MultiOutputRegressor
from sklearn.model_selection import train_test_split
from sklearn.metrics import mean_squared_error
from sklearn.preprocessing import StandardScaler

data = fetch_california_housing()
df=pd.DataFrame(data.data,columns=data.feature_names)
df['target']=data.target
print(df.head())

X=data.data[:, :3]
Y=np.column_stack((data.target,data.data[:, 6]))
X_train,X_test, Y_train, Y_test = train_test_split(X,Y, test_size = 0.2, random_state = 42)
scaler_X = StandardScaler()
scaler_Y = StandardScaler()

X_train=scaler_X.fit_transform(X_train)
X_test=scaler_X.transform(X_test)
Y_train=scaler_Y.fit_transform(Y_train)
Y_test=scaler_Y.transform(Y_test)
sgd=SGDRegressor(max_iter=1000, tol=1e-3)

multi_output_sgd=MultiOutputRegressor(sgd)
multi_output_sgd.fit(X_train,Y_train)

Y_pred=multi_output_sgd.predict(X_test)
Y_pred = scaler_Y.inverse_transform(Y_pred)
Y_test = scaler_Y.inverse_transform(Y_test)
mse=mean_squared_error(Y_test,Y_pred)
print("Mean Squared Error: ",mse)
print("\nPredictions:\n",Y_pred[:5])
```
## Output:
## Head:
![Screenshot 2024-09-10 112145](https://github.com/user-attachments/assets/3a51d001-28b9-4982-ad71-8c6d16c7e323)

## Prediction:
![Screenshot 2024-09-10 112500](https://github.com/user-attachments/assets/57054332-6010-4c11-b211-bf0ee9cb4dc1)

## Result:
Thus the program to implement the multivariate linear regression model for predicting the price of the house and number of occupants in the house with SGD regressor is written and verified using python programming.
