## Week 4
**Model Development** is the underlying mathematical equation that used to predict the output given one or more inputs.
**Input** feed into your model and there you have your **output prediction**.
---
**Linear Regressions**
- uses the equation of $y=b_0+b_1x$
- in real world data, there will be **noise** to your data even if your model is correct assumptions, there will still be error

**Multiple Regressions**
- uses the equation of $y=b_0+b_1x_1+b_2x_2+b_nx_n$
```
from sklearn.linear_model import LinearRegression

lm = LinearRegression()

X = df[["predictor1", "predictor2", "predictorn"]]
Y = df["target"]

lm.fit(X, Y) - find parameters

Yhat = lm.predict(X)

lm.intercept_    to retrieve the coefficient value (b0)

lm.coef_   to retrieve the coefficient value (b1 to bn)
```
---
**Model Evaluation using Visualization**
1. Regressions Plot
```
import seaborn as sns

sns.regplot(x="column1", y="column2", data=dataframe)
plt.ylim(0,)
```

2. Residual Plot, should not give trendline which will suggest linear assumtion is incorrect, generally need to stick to the x-axis for all scatter points
```
import seaborn as sns

sns.residplot(df['column1'], df['column2'])
```

3. Distribution Plot (actual and fitted y values (target variable) against x data column predictor variable)
```
import seaborn as sns

ax1 = sns.distplot(df['column1'], hist=False, color="r", label="Actual Value")

sns.distplot(Yhat, hist=False, color="b", label="Fitted Values", ax=ax1)
```
---
**Polynomial Regression**
- assumptions on the data relationship is non-linear
```
f = np.polyfit(x, y, nth-order of degree)

p = np.poly1d(f) --> only for one dimensions

print(p)
```
**For Polynomial Regression with more than one dimension**
```
from sklearn.preprocessing import PolynomialFeatures

pr = PolynomialFeatures(degree=n, include_bias=False)

x_polly = pr.fit_transform(x[["hoursepower", "curb-weight"]])

pr.fit_transform([[1, 2]])
```
**Alternatively, to include normalization process**
```
from sklearn.preprocessing import StandardScaler

SCALE = StandardScaler()

SCALE.fit(x_data[['column1', 'column2']])

x_scale = SCALE.transform(x_data[['column1', 'column2']])
```
**Pipeline** for simplification steps
1. X-input
2. Normalization
3. Polynomial Transform
4. Linear Regression
5. yhat prediction
```
from sklearn.preprocessing import PolynomialFeatures

from sklearn.linear_model import LinearRegression

from sklearn.preprocessing import StandardScaler

from sklearn.pipeline import Pipeline

Input = [('scale', StandardScaler()), ('polynomial', PolynomialFeatures(degree=2),...('mode', LinearRegression()))]

# Pipeline Constructor
pipe = Pipeline(Input)

# to Train the pipeline object
Pipe.fit(df[['column1', 'column2', 'columnns']], y)

yhat = Pipe.predict(X[['column1', 'column2', 'columnns']])
```
---
**Measure for In-Sample Evaluation** - model evaluation by numerical approaches
1. Mean Squared Error (MSE) = (Sum of error)^2/number of samples
2. R-square = (1-(MSE of regression line)/(MSE of the average of the data))
  - generally between 0 and 1
  - if negative means there is large likely hood that your model is overfitted
**MSE in python**
```
from sklearn.metrics import mean_squared_error

mean_squared_error(df['price'], Y_predict_simple_fit)
```

**R-Square in python**
```
x = df['column']
y = df['column']

lm.fit(X, Y)

lm.score(X, Y)
```
---
**Determining a good fit model**
1. Do the predicted values make sense (logical thinking)
2. Visualization
3. Numerical Measures for evaluation
4. Comparing Models
5. low mean square error and high R-square does not necessary means good fit, because high degree polynomial inherently and generally usually yield low mean square error and R-square if compared to linear model.
