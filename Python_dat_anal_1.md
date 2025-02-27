## Python datova analyza 1
https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie

## modul statistics
https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/statistics.md

```python
import statistics

scores = [89, 93, 94, 99, 83, 81, 90, 78, 87, 98, 93, 92]

mean = statistics.mean(scores)
print(mean)
```

--median - nie je nachylna na nizke resp. vysoke hodnoty
```python
import statistics


salaries = [980, 770, 890, 1120, 1000, 990, 1200, 1320, 1110, 980, 5600, 7800]

mean = statistics.mean(salaries)
print(mean)

mean = statistics.median(salaries)
print(mean)

medh = statistics.median_high(salaries)
print(medh)

medl = statistics.median_low(salaries)
print(medl)

print(sorted(salaries))
```

--vazeny priemer  Weighted mean

--https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/statistics.md#weighted-mean

```python
import statistics

u1 = {'name': 'Paul', 'scores': {'math': 98, 'biology': 65, 'English': 89, 'chemistry': 71}}
u2 = {'name': 'John', 'scores': {'math': 88, 'biology': 81, 'English': 88, 'chemistry': 99}}
u3 = {'name': 'Boris', 'scores': {'math': 90, 'biology': 93, 'English': 70, 'chemistry': 100}}

users = [u1, u2, u3]

class_w = {'math': 0.6, 'biology': 0.1, 'English': 0.3, 'chemistry': 0.1}

for u in users:
    data = [u['scores'][subject] for subject in class_w.keys()]
    weights = class_w.values()
    total_score = statistics.fmean(data, weights=weights)
    print(total_score)
```

--standardna odchylka  Standard deviation
--https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/statistics.md#standard-deviation

```python
import statistics

scores = [89, 93, 94, 99, 83, 81, 90, 78, 87, 98, 93, 92]
#rozptyl ma vztah k hodnotam
stdev = statistics.stdev(scores)
print(stdev)

# rozptyl dat nema vztah k hodnotam.. sluzi na porovnavanie napr. medzi mestami, statmi atd
var = statistics.variance(scores)
print(var)
```

-- korelacia (napr medzi vekom a platom)

--https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/statistics.md#correlation

```python
# predtym  vytvorit data.csv
import statistics
import csv

# orbital_period = [88, 225, 365, 687, 4331, 10_756, 30_687, 60_190]    # days
# dist_from_sun = [58, 108, 150, 228, 778, 1_400, 2_900, 4_500] # million km

user_age = []
user_income = []

filename = 'data.csv'

with open(filename, 'r') as fd:

    reader = csv.DictReader(fd)

    for row in reader:
        age = int(row['Age'])
        income = int(row['Income($)'])

        user_age.append(age)
        user_income.append(income)

print(user_age)
print(user_income)

cor = statistics.correlation(user_age, user_income, method='ranked')
print(cor)
```

--  https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/test.md#multiple-data-sources

-- 1. vytvorit excel:

```python
import openpyxl
# vytvori novy excel byty.xlsx subor a vyplni ho datami
# Create a new workbook and select the active worksheet 
workbook = openpyxl.Workbook()
worksheet = workbook.active

# Set the headers
headers = ["id", "typ", "mesto", "cena"]
worksheet.append(headers)

# Add the data
data = [
    [1, "1i", "Košice", 69000],
    [2, "2i", "Michalovce", 74500],
    [3, "1i", "Prešov", 87000],
    [4, "3i", "Košice", 120000],
    [5, "4i", "Košice", 140000],
    [6, "2i", "Bardejov", 87000]
]

for row in data:
    worksheet.append(row)

# Save the workbook
workbook.save("byty.xlsx")
print("Excel file 'byty.xlsx' created successfully!")
```
