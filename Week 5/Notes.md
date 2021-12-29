## Wee 5
**Model Evaluation and Refinement**
- Training Set: 70%
- Testing Set: 30%
```
from sklearn.model_selection import train_test_split

x_train, x_test, y_train, y_test = train_test_split(x_data, y_data, test_size=0.3, random_state=0)
```
**Generalization Performance**
- is a measure of how well model in predicting unseen data, can be closely related to testing data
- find the balance between **accuracy** and **precision**

**Cross Validation**
- each observation is used for both training and testing
```
from sklearn.model_selection import cross_val_score

scores = cross_val_score(lr, x_data, y_data, cv=nth partitions)

np.mean(scores)
```

**Cross Validation Predict**
- returns the prediction that was obtained for each element when it was in the test set
```
from sklearn.model_selection import cross_val_predict

yhat = cross_val_predict(Ir2e, x_data, y_data, cv=nth partitions)
```
---
**Model Selection Fitting**
- **underfitting** model is too simple to generally represents the data
- **best fit** what we are looking for with highest value of R-square and tolerable amount of error v alues
- **overfitting** the model is too complex to generally represents the data

```
Rsqu_test = []

order = [1, 2, 3, 4]

for n in order:
  pr = PolynomialFeatures(degree=n)

  x_train_pr = pr.fit_transform(x_train[['column']])

  x_test_pr = pr.fit_transform(x_test[['column']])

  Ir.fit(x_train_pr, y_train)

  Rsqu_test.append(Ir.score(x_test_pr, y_test))
```
---
**Ridge regression** is a regression that is employed in a **Multiple regression model when Multicollinearity occurs**. Multicollinearity is when there is a **strong relationship among the independent variables**. Ridge regression is very common with polynomial regression.  The next video shows how Ridge regression is used to **regularize and reduce the standard errors to avoid over-fitting a regression model**.
- aims to prevent overfitting
- introduce a parameters called **alpha** to control the coefficient values especially for large polynomial degree polynomial equations
- if alpha is too large (underfit data), and vice versa
```
from sklearn.linear_model import Ridge

RidgeModel = Ridge(alpha=value)

RidgeModel.fit(X, y)

Yhat = RidgeModel.predict(X)
```
- introducing it has the effect of reducing the accuracy for performance for training data, but increase the performance for testing data which is desirable
- plot of R-Square against alpha values
---
**Grid Search**
- helps us to fine tune the **hyperparameters values** with few lines of code
- a validation phase is introduced to optimize the hyperparameters values
```
from sklearn.linear_model import Ridge
from sklearn.model_selection import GridSearchCV

parameters = [{'alpha':[0.001, 0.1, 1, 10, 100], 'normalize': [True, False]}]

RR = Ridge()

Grid1 = GridSearchCV(RR, parameters, cv=number of folds) # Default is gauge by the highest R-Square values

Grid1.fit(x_data[['column1', 'column2', 'columnns']], y_data)

Grid1.best_estimator_

scores = Grid1.cv_results_

for param, mean_val, mean_test inzip(scores['params'], scores['mean_test_score'], scores['mean_train_score']):
  print(param, "R^2 on test data:", mean_val, "R^2 on train data:", mean_test)
  
```
