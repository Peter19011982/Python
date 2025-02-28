## Python_dat_anal_2.den

## PANDAS

-- treba si to prebehnut , vela pouzitelnych funkcii na datovu analyzu


-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/basics.md


-- subory csv: https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/tree/main/data


```python
import pandas as pd

data = [['Alex', 10], ['Ronald', 18], ['Jane', 33]]
df = pd.DataFrame(data, columns=['Name', 'Age'])
df.index+=1
print(df)

print(df.columns)
print(df.values)
print(df.index)

print('----------------')

print(df.shape)
print(df.size)
```

-- info o suboroch

```python
import pandas as pd

df = pd.read_csv('products.csv') 
print(df.info())


import pandas as pd

df = pd.read_csv('mock_data.csv') 
print(df.info())
```

-- describe function


```python
import pandas as pd

s1 = pd.Series([1, 2, 3, 4, 5, 6, 7, 8])
s2 = pd.Series([12, 23, 31, 14, 11, 61, 17, 18])

data = {'Vals 1': s1, 'Vals 2': s2}
df = pd.DataFrame(data)

print(df.describe())
```
for a scecific collumn

```python
import pandas as pd

filename = 'mock_data2.csv'
df = pd.read_csv(filename)

print('basic stats for Entries')
summary_entries = df['entries'].describe()

print(summary_entries)
```


-- export do roznych formatov


![image](https://github.com/user-attachments/assets/77dd58ea-b140-4d8d-a86a-0f6af0e7b1fa)


--napr. do csv

```python
import pandas as pd

data = [['Alex', 10], ['Ronald', 18], ['Jane', 33]]
df = pd.DataFrame(data, columns=['Name', 'Age'])

df.to_csv('users.csv', index=False)
```

-- change index


```python
import pandas as pd

df = pd.read_csv("military_spending.csv") 
df.index = df.index + 1

print(df)
```

-- custom index

```python
import pandas as pd

data = {'country': ['Brazil', 'Russia', 'India', 'China', 'South Africa'],
        'capital': ['Brasilia', 'Moscow', 'New Dehli', 'Beijing', 'Pretoria'],
        'area': [8.516, 17.10, 3.286, 9.597, 1.221],
        'population': [200.4, 143.5, 1252, 1357, 52.98]}

df = pd.DataFrame(data)
print(df)

print('------------------------------')

df.index = ['BR', 'RU', 'IN', 'CH', 'SA']
print(df)
```

--no index

```python
import pandas as pd 
  
df = pd.read_csv("military_spending.csv") 

# print(df)
print(df.to_string(header=False, index=False))
```

## The inplace attribute


https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/basics.md#the-inplace-attribute

```python
import pandas as pd

file_name = 'countries.csv'

df = pd.read_csv(file_name)

# tu sa nebude nic menit, iba sa vypise
df2 = df.query("continent == 'Europe'")
print(df2)


# tu sa zmeni povodny dataframe
# df.query("continent == 'Europe'", inplace=True)
# print(df)
```

-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/basics.md#data-type-inference


-- vyuzitie ake typy v DB mam nastavit pre dane stlpce


-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/basics.md#converters


-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/basics.md#missing-values

## IMPORT DATA

-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/import.md

-- pip instal lxml

```python
import pandas as pd

# URL of the XML file
url = "https://webcode.me/users.xml"

# Read the XML data into a DataFrame
df = pd.read_xml(url)

# Display the DataFrame
print(df)
```

--https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/import.md#html-table-to-dataframe

```python
import pandas as pd

# URL of the HTML page containing the table
url = "https://webcode.me/users.html"

# Read the HTML table into a DataFrame
df_list = pd.read_html(url)

# The function returns a list of DataFrames, so we select the first one
df = df_list[0]

# Display the DataFrame
print(df)
```

## PANDAS vs POSTGRES

-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/pandas/import.md#postgresql-to-dataframe

```python
import pandas as pd

# Create the connection string
cs = 'postgresql://postgres:postgres@localhost/testdb'

# Execute a query to fetch data from the 'users' table
query = "SELECT * FROM users"
df = pd.read_sql_query(query, cs)

print(df)

```


