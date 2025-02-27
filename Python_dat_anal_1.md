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

## Praca s viacerymi zdrojmi:


--  https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/test.md#multiple-data-sources

-- 3 zdroje: excel, DB, web

-- 1. vytvorit excel:  pip install openpyxl

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

-- 2. druhy zdroj DB:  sqllitedb (mala suborova databaza)

-- create_db_table.py

```python
import sqlite3

con = sqlite3.connect('test.db')

with con:
    
    cur = con.cursor()    
    cur.execute("CREATE TABLE byty(id INTEGER PRIMARY KEY, typ TEXT, mesto TEXT, cena INT)")
    cur.execute("INSERT INTO byty(typ, mesto, cena) VALUES('1i', 'Bratislava', 99800)")
    cur.execute("INSERT INTO byty(typ, mesto, cena) VALUES('2i', 'Bratislava', 124000)")
    cur.execute("INSERT INTO byty(typ, mesto, cena) VALUES('3i', 'Bratislava', 230000)")
    cur.execute("INSERT INTO byty(typ, mesto, cena) VALUES('1i', 'Bratislava', 119000)")
    cur.execute("INSERT INTO byty(typ, mesto, cena) VALUES('2i', 'Bratislava', 250800)")
    cur.execute("INSERT INTO byty(typ, mesto, cena) VALUES('1i', 'Bratislava', 90800)")
```

-- 3. treti zdroj web https://webcode.me/byty.csv

-- pip install requests

-- hlavy program:

```python
import sqlite3
import openpyxl
import requests
import csv
import uuid
from collections import namedtuple
from itertools import groupby


Byt = namedtuple('Byt', 'id typ mesto cena')

byty = []


def read_db():
    with sqlite3.connect('test.db') as con:
        cur = con.cursor()
        cur.execute("SELECT * FROM byty")
        rows = cur.fetchall()
        for row in rows:
            byty.append(row)


def read_excel():

    workbook = openpyxl.load_workbook('byty.xlsx')
    worksheet = workbook.active

    for row in worksheet.iter_rows(min_row=2, values_only=True):
        byty.append(row)


def fetch_csv():

    url = 'https://webcode.me/byty.csv'
    resp = requests.get(url)

    resp.raise_for_status()

    data = resp.text

    reader = csv.DictReader(data.splitlines())
    byty_csv = [(row['id'], row['typ'], row['mesto'], int(row['cena']))
                for row in reader]

    byty.extend(byty_csv)


read_db()
read_excel()
fetch_csv()

for byt in byty:
    print(byt)

print('---------------------------------')
print('ID cka nie su v poriadku- vysporiadame sa s tym tak, ze tie IDcka budem ignotrovat')
print('---------------------------------')
print('budeme generovat nove IDcka pomocou uuid.uuid4()' )

byty_cleaned = [Byt(uuid.uuid4(), e[1], e[2], e[3]) for e in byty]

sorted_cena = sorted(byty_cleaned, key=lambda x: x.cena)

print('sorted by cena')

for e in sorted_cena:
    print(e)

print('---------------------------------')

print('grouped by mesto')

sorted_mesto = sorted(byty_cleaned, key=lambda x: x.mesto)
grouped_mesto = groupby(sorted_mesto, key=lambda x: x.mesto)

for mesto, group in grouped_mesto:
    print(mesto)
    for e in group:
        print(e)
```


## Nestrukturovane data
-- problem su nestrukturovane data (napr. bazos) - tie ak chcem spracovat ako dataset, tak mame problem... pouzijeme AI


## praca s Databazou Postgres  

-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/psycopg.md

-- pip install "psycopg[binary,pool]"
-- testdb mam vytvorenu

```python
import psycopg

cs = "dbname='testdb' user='postgres' password='postgres'"

# with aj otvori modul aj ho potom uzavrie
with psycopg.connect(cs) as con:

    with con.cursor() as cur:
        
        cur.execute('SELECT version()')

# tu je n-tica vysledkom, cize my potrebujeme len 0-ty prvok zobrazit
        version = cur.fetchone()[0]
        print(version)
```

## Execute funkcia


--https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/psycopg.md#execute

```python
import psycopg


cs = "dbname='testdb' user='postgres' password='postgres'"

with psycopg.connect(cs) as con:

    with con.cursor() as cur:

        cur.execute("DROP TABLE IF EXISTS cars")
        cur.execute("CREATE TABLE cars(id SERIAL PRIMARY KEY, name VARCHAR(255), price INT)")
        cur.execute("INSERT INTO cars(name, price) VALUES('Audi', 52641)")
        cur.execute("INSERT INTO cars(name, price) VALUES('Mercedes', 57127)")
        cur.execute("INSERT INTO cars(name, price) VALUES('Skoda', 9000)")
        cur.execute("INSERT INTO cars(name, price) VALUES('Volvo', 29000)")
        cur.execute("INSERT INTO cars(name, price) VALUES('Bentley', 350000)")
        cur.execute("INSERT INTO cars(name, price) VALUES('Citroen', 21000)")
        cur.execute("INSERT INTO cars(name, price) VALUES('Hummer', 41400)")
        cur.execute("INSERT INTO cars(name, price) VALUES('Volkswagen', 21600)")
```

-- naplnenie DB tabulky z n-tice


```python
import psycopg

cars = (
    (1, 'Audi', 551111),
    (2, 'Mercedes', 57127),
    (3, 'Skoda', 9000),
    (4, 'Volvo', 29000),
    (5, 'Bentley', 350000),
    (6, 'Citroen', 21000),
    (7, 'Hummer', 41400),
    (8, 'Volkswagen', 21600)
)

cs = "dbname='testdb' user='postgres' password='postgres'"

with psycopg.connect(cs) as con:
        
    with con.cursor() as cur:

        cur.execute("DROP TABLE IF EXISTS cars")
        cur.execute(
            "CREATE TABLE cars(id SERIAL PRIMARY KEY, name VARCHAR(255), price INT)")

        query = "INSERT INTO cars (id, name, price) VALUES (%s, %s, %s)"
        cur.executemany(query, cars)
```

-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/psycopg.md#last-row-id

```python
import psycopg

cs = "dbname='testdb' user='postgres' password='s$cret'"

with psycopg.connect(cs) as con:
        
    with con.cursor() as cur:

        cur.execute("DROP TABLE IF EXISTS words")
        cur.execute("CREATE TABLE words(id SERIAL PRIMARY KEY, word VARCHAR(255))")
        cur.execute("INSERT INTO words(word) VALUES('forest') RETURNING id")
        cur.execute("INSERT INTO words(word) VALUES('cloud') RETURNING id")
        cur.execute("INSERT INTO words(word) VALUES('valley') RETURNING id")

        last_row_id = cur.fetchone()[0]

        print(f"The last Id of the inserted row is {last_row_id}")
```




--fetch all

-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/psycopg.md#fetch_all

```python
import psycopg

cs = "dbname='testdb' user='postgres' password='s$cret'"

with psycopg.connect(cs) as con:
        
        with con.cursor() as cur:
    
            cur = con.cursor()
            cur.execute("SELECT * FROM cars")

            rows = cur.fetchall()

            for row in rows:
                print(f"{row[0]} {row[1]} {row[2]}")
```

-- Dictionaly cursor

--https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/psycopg.md#dictionary-cursor

```python
import psycopg

cs = "dbname='testdb' user='postgres' password='s$cret'"

with psycopg.connect(cs) as con:

    with con.cursor(row_factory=psycopg.rows.dict_row) as cur:
        
        cur.execute("SELECT * FROM cars")

        rows = cur.fetchall()

        for row in rows:
            print(f"{row['id']} {row['name']} {row['price']}")
```

-- Paremetriczovane query

--- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/psycopg.md#parameterized-queries

```python
import psycopg

cs = "dbname='testdb' user='postgres' password='s$cret'"

with psycopg.connect(cs) as con:

    uId = 1
    uPrice = 62300

    with con.cursor() as cur:
        cur.execute("UPDATE cars SET price=%s WHERE id=%s", (uPrice, uId))

        print(f"Number of rows updated: {cur.rowcount}")
```

--alebo ako slovnik

```python
import psycopg

uid = 3
cs = "dbname='testdb' user='postgres' password='s$cret'"

with psycopg.connect(cs) as con:

    with con.execute("SELECT * FROM cars WHERE id=%(id)s", {'id': uid}) as cur:
        
        row = cur.fetchone()
        print(f'{row[0]} {row[1]} {row[2]}')
```

-- METADATA - ako zistit ako sa volaju jednotlive stlpce Db tabulky


-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/psycopg.md#metadata

```python
import psycopg

cs = "dbname='testdb' user='postgres' password='s$cret'"

with psycopg.connect(cs) as con:

    with con.execute('SELECT * FROM cars') as cur:

        col_names = [cn[0] for cn in cur.description]
        rows = cur.fetchall()

        print(f'{col_names[0]} {col_names[1]} {col_names[2]}')
```

-- vsetky tabulky v DB

```python
import psycopg

cs = "dbname='testdb' user='postgres' password='s$cret'"

with psycopg.connect(cs) as con:

    with con.execute("""SELECT table_name FROM information_schema.tables
            WHERE table_schema = 'public'""") as cur:

        rows = cur.fetchall()

        for row in rows:
            print(row[0])
```

-- COPY from , COPY to


-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/psycopg.md#copy_to


```python
import psycopg

cs = "dbname='testdb' user='postgres' password='postgres'"

with psycopg.connect(cs) as con:

    with con.cursor() as cur:

        with open('cars.csv', 'wb') as f:

            with cur.copy("COPY cars TO STDOUT WITH CSV HEADER") as copy:

                for row in copy:
                    f.write(row)
```




-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/psycopg.md#copy_to


-- do novej tabulky cars2


```python
import psycopg

cs = "dbname='testdb' user='postgres' password='postgres'"
with psycopg.connect(cs) as con:

    with con.cursor() as cur:

        cur.execute('DROP TABLE IF EXISTS cars2')
        cur.execute('CREATE TABLE cars2(id SERIAL PRIMARY KEY, name VARCHAR(255), price INTEGER)')

        with open('cars.csv', 'r') as f:

            with cur.copy("COPY cars2 FROM STDIN WITH CSV HEADER") as copy:

                for line in f:
                    copy.write(line)
```

-- vygenerovanie users.csv s 150 000 zaznamami a naplnenie DB tabulky users s tymito datami:

--  vygenerovanie users.csv s 150 000 zaznamami


```python
import faker


file_name = 'users.csv'

faker = faker.Faker()

i = 1

with open(file_name, 'w') as fd:

    fd.write(f'id,first_namne,last_name,email\n')

    for _ in range(150_000):
        first_name = faker.first_name()
        last_name = faker.last_name()
        email = faker.email()

        fd.write(f'{i},{first_name},{last_name},{email}\n')
        
        i += 1

    print('file successfully created')
```

--naplnenie DB tabulky users tymito datami

```python
import psycopg

cs = "dbname='testdb' user='postgres' password='postgres'"
with psycopg.connect(cs) as con:

    with con.cursor() as cur:

        cur.execute('DROP TABLE IF EXISTS users')
        cur.execute('CREATE TABLE users(id SERIAL PRIMARY KEY, first_name VARCHAR(255), last_name VARCHAR(255), email VARCHAR(255))')

        with open('users.csv', 'r') as f:

            with cur.copy("COPY users FROM STDIN WITH CSV HEADER") as copy:

                for line in f:
                    copy.write(line)
```


## Get SHMU data


-- nacitanie vysky hladiny zo shmu


```python
import pandas

# pip install pandas lxml 

url = "https://www.shmu.sk/sk/?page=1&id=hydro_vod_all&station_id=5127"

df_list = pandas.read_html(url)

df = df_list[1]

# Display the DataFrame
df.to_csv('shmu.csv', index=False)
```


## mock dada

-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/data/mock_data.csv


-- csv cko, s ktorym budem pracovat

-- do DB
```python
import csv
import psycopg


file_name = 'mock_data.csv'
users = []


with open(file_name, 'r') as fd:

    reader = csv.DictReader(fd)

    for line in reader:

        row = int(line['id']), line['first_name'], line['last_name'], line['active'], line['entries'], line['DoB']

        users.append(row)


cs = "dbname='testdb' user='postgres' password='postgres'"

with psycopg.connect(cs) as con:
        
    with con.cursor() as cur:

        cur.execute("DROP TABLE IF EXISTS users_mock")
        cur.execute(
            "CREATE TABLE users_mock(id SERIAL PRIMARY KEY, first_name VARCHAR(255), last_name VARCHAR(255), active VARCHAR(10), entries VARCHAR(10), DoB VARCHAR(10))")

        query = "INSERT INTO users_mock (id, first_name, last_name, active, entries, dob) VALUES (%s, %s, %s, %s, %s, %s)"
        cur.executemany(query, users)
```

# get username/password from env variables  

--premenne prostredia DB credentions


```python
import os
import psycopg


username = os.environ.get('DB_USERNAME')
password = os.environ.get('DB_PASSWORD')

cs = f"dbname='testdb' user={username} password={password}"

with psycopg.connect(cs) as con:
        
        with con.cursor() as cur:
    
            cur.execute("SELECT * FROM cars")
            rows = cur.fetchall()

            for row in rows:
                print(f"{row[0]} {row[1]} {row[2]}")
```

# SQL 

-- https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/sql.md



## AI

-- https://openrouter.ai/
-- login google ucet


--OPENROUTER_API_KEY: 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
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

--https://github.com/janbodnar/Python-Datovy-Analytik-Skolenie/blob/main/ai.md#openrouter

--- pip install openai
--- time.sleep(3)

```python

import time

from openai import OpenAI
import os

client = OpenAI(
  base_url="https://openrouter.ai/api/v1",
  api_key=os.environ["OPENROUTER_API_KEY"],
)

completion = client.chat.completions.create(
  model="deepseek/deepseek-r1:free",
  messages=[
    {
      "role": "user",
      "content": "What is the meaning of life?"
    }
  ]
)

print(completion.choices[0].message.content)
```
