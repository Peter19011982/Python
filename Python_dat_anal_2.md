## Python_dat_anal_2.den

## PANDAS

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
