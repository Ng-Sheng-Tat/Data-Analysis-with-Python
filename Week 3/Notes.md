## Week 3
**Exploratory Data Analysis** is to:
1. Summarize main characteristics of the data
2. Gain better understanding of the data set
3. Uncover relationships between variables
4. Extract important variables
---
**Descriptive Statistics**
1. by using the describe methods (Nan values automatically excluded)
``df.describe()``

2. by using the value_counts() methods
```
dataframename = df['columnname'].value_counts().to_frame()
dataframename.rename(columns={'old name':'new name'}, inplace=True)
dataframename
```

3. Box-Plot
``sns.boxplot(x="x-columnaname", y="y-columnname", data=dataframe)``

4. Scatter Plot
```
y = df["tagets/dependent variables"]
x = df["predictor/independent variables"]
plt.scatter(x, y)
```
---
**Group By in Python**
1. Group by methods
```
df_test = df[["multiple column names including target"]]
df_group = df_test.groupby(["influential predictorsss"], as_index=False).mean()
de_group
```
2. Pivot Methods
``df_pivot = df_group.pivot(index="column1", columns="column2")``

3. Heat Map - for multidimensional visualization
```
plt.pcolor(df_pivot, cmap="RdBu")
plt.colorbar()
plt.show()
```
---
**Correlation**
- measures how one variable changes will affect the another variable (independency)
- does not imply causation
- shows relationship (positive/negative linear) by using a regression plot
```
sns.regplot(x="column1", y="column2", data=dataframe)
plt.ylim(0,)
```
---
**Statistical Correlation**
- calculate the p-value and the coefficient (refer to image notes)
`` coef, pvalue = stats.pearsonr(df['column1'], df['column2'])``
- can use together with a heatmap to visualize, generally strong relationship (linear) should give diagonal values of similar colot in the heatmap
---
**Association between two categorical variables: Chi-Square**
- for finding the relationship between two variables
- use crosstab or contingency table (similar to pivot table)
- refer to notes
``scipy.stats.chi2_contingency(cont_table, correction=True)``
