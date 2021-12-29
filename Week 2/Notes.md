## Week 2
**Data-Pre-Processing** is the process of converting or mapping data from the initial "raw" form into another format, in order to prepare the data for further analysis. Also known as **data cleaning, and data wrangling**
---
**Dealing with missing values**
1. Drop the missing values
  - across rows
  - across columns
2. Replace the missing values
  - with average
  - with values that appear most frequently
  - based on other specific functions
3. Leave it as it is
**Code**
``df.dropna(subset=["columnname"], axis, inplace=True)``
- axis = 0 means drop the entire row
- axis = 1 means drop the entire column
``df.replace(missing_values, new_values)``
---
**Data Formatting** into the specific format
``df["new column name"] = arithmetic operations``
- pandas automatically vectorize and do the operations elemental row wise
``df.rename(columns={"oldname":"newname"}, inplace=True)``

**Checking datatype**
``df.dtypes()``

**Changing datatypes**
- object, int64, float64, etc.
``df["columnname"] = df['columnname'.astype("newformat")]``
---
**Data Normalization**
Normalization has several reasons such as to save computational cost, making comparison easier among columns and to make analysis task easier, and to avoid linear regression models being trained until biased (more influential parameters).
- refers three methods of normalizing the data
---
**Binning in Python**
- to see the distribution, like a histogram plot
```
bins = np.linspace(min(df['columnname']), max(df['columnname']), n-bars+1)
groupnames = ["low", "medium", "high"] - should be n-bars number of length
df["newcolumn"] = pd.cut(df["column"], bins, labels=groupnames, include_lowest=True)
```
---
**Converting categorical data into numerical data**
- *one-hot-encoding* techniques because models does not take string as input
``pd.get(dummies(df["columnname"]))``
