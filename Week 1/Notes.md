## Week 1
- **Data Analysis** is important to extract information from vast amount of data.
- The predicted variable is known as the **label or target**.
- Scientific Computing Library: Pandas (dataframe), Numpy, Scipy
- Visualization Library: Matplotlib, Seaborn
- Algorithm Library: Scikit-learn, Statsmodels
---
**Using Pandas to read data**
- before reading data, we must know the file path and the file format

**File Reading**
``pd.read_csv(filepath/url, header=None)``

**Dataframe preview**
``df.head(n=5) or df.tail(n=5)``

**Replacing header of data frame**
``df.columns = headerlist``

**Saving csv file**
``df.to_csv(filepath)``
---
**Pandas Statistical Functions**
- the data type and data distribution are important to be known

**Checking Data Type**
``df.dtypes``

**The describe methods: include all means include information for object or string data**
``df.describe(include="all")``

**info method returns the top and bottom 30 rows information**
``df.info()``
---
**Database for Python**
- DBAPI is function for database query

**Connection Objects**
- Database connections
- Manage transaction
- methods include the following
```
cursor()
commit()
rollback()
close()
```

**Cursor Objects**
- Database Queries

**Examples of code using DB_API**
```
from dbmodule import connect

# Create connection object
connection = connect('databasename', 'username', 'password')

# Create a cursor object
cursor = connection.cursor()

# Run Queries
cursor.execute('SQL Statement')
results = cursor.fetchall()

# Close to free up resources
cursor.close()
connection.close()
```
