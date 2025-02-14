# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. import pandas, numpy,matplotlib and upload the file that contains the required data
2. Use matplotlib to display the scatter plot of the data
3. Define computecost and gradientdescent
4. Use matplotlib to display the visual representation

## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: PRAVINRAJJ GK
RegisterNumber:  212222240080
*/

import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
data=pd.read_csv("/content/ex1.txt",header=None)
plt.scatter(data[0],data[1])
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City (10,000s)")
plt.ylabel("Profit($10,000")
plt.title("Profit Prediction")
def computeCost(X,y,theta):
  m=len(y)
  h=X.dot(theta)
  square_err=(h-y)**2
  return 1/(2*m)*np.sum(square_err)
  data_n=data.values
m=data_n[:,0].size
x=np.append(np.ones((m,1)),data_n[:,0].reshape(m,1),axis=1)
y=data_n[:,1].reshape(m,1)
theta=np.zeros((2,1))
computeCost(X,y,theta)
def gradientDescent(X,y,theta,alpha,num_iters):
  m=len(y)
  J_history=[]

  for i in range(num_iters):
    predictions = X.dot(theta)
    error=np.dot(X.transpose(),(predictions-y))
    descent=alpha*1/m*error
    theta-=descent
    J_history.append(computeCost(X,y,theta))
  return theta,J_history 
  theta,J_history=gradientDescent(x,y,theta,0.01,1500)
print("h(x) ="+str(round(theta[0,0],2))+" + "+str(round(theta[1,0],2))+"x1")
plt.plot(J_history)
plt.xlabel("Iteration")
plt.ylabel("$(\Theta)$")
plt.title("Cost function using Gradient Descent")
plt.scatter(data[0],data[1])
x_value=[x for x in range(25)]
y_value=[y*theta[1]+theta[0]for y in x_value]
plt.plot(x_value,y_value,color="r")
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City (10,000s)")
plt.ylabel("Profit ($10,000)")
plt.title("Profit Prediction")
def predict(x,theta):
  predictions=np.dot(theta.transpose(),x)
  return predictions[0]
  predict1=predict(np.array([1,3.5]),theta)*10000
print("For population = 35,000, we predict a profit of $"+str(round(predict1,0)))
predict2=predict(np.array([1,7]),theta)*10000
print("For population = 70,000, we predict a profit of $"+str(round(predict2,0)))
```

## Output:
## Profit Prediction
![image](https://user-images.githubusercontent.com/117917674/229184416-0d4fdbb2-ab96-4e42-8159-432674ccbdd3.png)
## Cost function
![image](https://user-images.githubusercontent.com/117917674/229984055-5d111f4d-6b8a-4c39-b044-515da4bb6a92.png)

## Gradient Descent
![image](https://user-images.githubusercontent.com/117917674/229984103-1acc5b9c-3776-44a4-af10-5e82b6398593.png)

## Cost function and Gradient descent
![image](https://user-images.githubusercontent.com/117917674/229184436-60602c8e-8be7-4046-93dc-e6810ebef421.png)
## GRAPH WITH BEST FIT LINE (PROFIT PREDICTION)
![image](https://user-images.githubusercontent.com/117917674/229184450-c17a2baf-f715-4e57-8324-d58a74b3672e.png)
## PROFIT PREDICTION FOR A POPULATION OF 35,000
![image](https://user-images.githubusercontent.com/117917674/229984420-474fe98f-313d-48e3-84c6-7a30f7f3a5de.png)
## PROFIT PREDICTION FOR A POPULATION OF 70,000
![image](https://user-images.githubusercontent.com/117917674/229984460-4ac6e988-91b9-40f3-b8ce-f3cdf3ac3ff3.png)

## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
