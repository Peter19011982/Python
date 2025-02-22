-- kod prezencka 3899
-- https://iwww.vse.sk/sys/app/contacts/#/a/es

--rozne skripty hotove mozes pozriet na 
https://github.com/janbodnar/Python-Skolenie/tree/master/scripts

--kniznca na sikovne programovanie
pip instal puncy

```python
vals = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

# for i in vals:
#     for e in i:
#         vals2.append(e)

vals2 = [e for nested in vals for e in nested]

assert vals2 == [1, 2, 3, 4, 5, 6, 7, 8, 9], 'failed'
print('passed')

# ------------------------------------------
data = [1, 2.3, True, 'falcon', 4, -2, False, (1, 2, 3), 9]

data2 = tuple(sorted([e for e in data if type(e) == int]))

assert data2 == (-2, 1, 4, 9), 'failed'
print('passed')

# ------------------------------------------

data = '1,2,3,4,5,6,7,8,9,10'

data2 = ';'.join(reversed(data.split(',')))

assert data2 == '10;9;8;7;6;5;4;3;2;1', 'failed'
print('passed')

# ------------------------------------------

def flatten(mylist):
    return [e for nested in mylist for e in nested]


data = '''
1,2,3,4,5
6,7,8,9,10
11,12,13,14,15
'''

lines = data.splitlines()[1:]
mysum = sum(map(int, flatten(map(lambda e: e.split(','), lines))))

assert mysum == 120, 'failed'
print('passed')


# ------------------------------------------

# Read all users into a list of User objects
# Use data classes
from dataclasses import dataclass

@dataclass
class User:
    first_name: str
    last_name: str
    occupation: str


filename = 'user2.csv'
users = []

with open(filename, 'r') as f:
    
    for line in f:
        cleaned_line = line.strip()
        fname, lname, occupation  = cleaned_line.split(',')
        user = User(fname, lname, occupation)
        users.append(user)


print(users)
#vystup:
# [User(first_name='Peter', last_name=' Sabol', occupation=' IT'), User(first_name='John', last_name=' Travolta', occupation=' Actor'), User(first_name='Miso', last_name=' Hanak', occupation=' IT')]

```


## WEB REQUESTS
https://github.com/janbodnar/Python-Skolenie/blob/master/libs/requests.md
https://github.com/janbodnar/Python-Skolenie/tree/master/libs/requests

-- pip install requests

```python
#!/usr/bin/python


import requests as req
url = "http://webcode.me"
resp = req.get(url)

print(resp.text)
print(resp.headers)
print(resp.status_code)
print(resp.history)
print(resp.url)

resp1 = req.request(method='GET', url="http://webcode.me")
print(resp1.text)
```


-- parsovanie do json

```python
import requests 

resp = requests.get('https://jsonplaceholder.typicode.com/posts')
posts = resp.json()

print(posts)

for post in posts:
    print(f"Id: {post['id']}")
    print(f"Title: {post['title']}")
    print(f"Body: {post['body']}")
```

## Basic standard modules
https://github.com/janbodnar/Python-Skolenie/blob/master/basic_std_modules.md

```python
import subprocess

def show_edit_environment_variables_dialog():
    try:
        # Command to open the System Properties window
        command = "SystemPropertiesAdvanced"

        # Run the command using subprocess
        subprocess.run(command, shell=True)

    except Exception as e:
        print(f"An error occurred: {e}")

if __name__ == "__main__":
    show_edit_environment_variables_dialog()
```

-- ktory python na ntb pouzivam


```python
import sys

print(sys.executable)
```

-- ake moduly su nainstalovane v python  


```python
import sys

print(sys.modules)

for m in sys.modules:
    print(m)

import math, os, random

for m in sys.modules:
    print(m)
```

-- systemove informacie:

```python
import sys

print(sys.argv)
print(sys.byteorder)
print(sys.platform)
print(sys.version)
print(sys.version_info)
print(sys.implementation)
print(sys.path)
```

## JSON
https://github.com/janbodnar/Python-Skolenie/blob/master/basic_std_modules.md#json

--vytvorenie json
```python
#!/usr/bin/python

import json

data = {"name": "Jane", "age": 17}

fname = 'friends.json'
with open(fname, 'w') as f:
    json.dump(data, f)
```





--nacitanie do slovnika
 
```python
#!/usr/bin/python

import json

fname = 'products.json'
with open(fname) as f:

    data = json.load(f)
    print(data)
    # for e in data['products']:
    #     print(e)
```


-- loads zo stringu
```python
#!/usr/bin/python

import json

json_data = '{"name": "Jane", "age": 17}'

data = json.loads(json_data)

print(type(json_data))
print(type(data))

print(data)
```

--pozor funkcia text

```python
import requests
import json

url = 'https://webcode.me/users.json'

resp = requests.get(url)
print(resp.status_code)

data = resp.text
print(type(data))

with open('users.json', 'w') as f:

    f.write(data)
```

-- funkcia json()

```python
import requests, json
url = 'https://webcode.me/users.json'

resp = requests.get(url)
print(resp.status_code)

data = resp.json()

with open('users2.json', 'w') as f:

    json.dump(data, f, sort_keys=True, indent=4 * ' ')
```

## Secrets
https://github.com/janbodnar/Python-Skolenie/blob/master/basic_std_modules.md#secrets
-- generovanie hesiel

```python
#!/usr/bin/python


import string
import secrets

chars = string.ascii_letters + string.digits + string.punctuation
passwd = "".join(secrets.choice(chars) for i in range(8))

print(passwd)
```

## ZIPFILE
https://github.com/janbodnar/Python-Skolenie/blob/master/basic_std_modules.md#zipfile
-- na pozretie .zip file  


```
import zipfile

files_to_zip = ['users2.json', 'users4.json']

with zipfile.ZipFile('pyarchive.zip', 'w') as zip:
    for file in files_to_zip:
        zip.write(file)
```

-- extract zip.file

```
#!/usr/bin/python

import zipfile

with zipfile.ZipFile('pyarchive.zip', 'r') as zip_ref:
    zip_ref.extractall('tmp')
```

-- extact konkretny subor

```
#!/usr/bin/python


import zipfile

with zipfile.ZipFile('output.zip') as zip:

    zip.extract('funs.py', '.')
```


-- zaujimavy skript -- pocty vyskytov slov na strankach - len top stranka


```python

import httpx
import asyncio
import re


async def get_async(url):
    async with httpx.AsyncClient() as client:
        return await client.get(url)

urls = ['https://www.sme.sk', 'https://www.pravda.sk', 'https://www.hlavnespravy.sk',
        'https://hnonline.sk', 'https://www.aktuality.sk',
        'https://dennikn.sk', 'https://www.cas.sk', 'https://www1.pluska.sk']

topics = [{'term': 'Fico', 'pattern': r'Fica|Fico|Ficovi|Ficom', 'count': 0},
          {'term': 'Putin', 'pattern': r'Putin|Putina|Putinovi|Putinom', 'count': 0},
          {'term': 'Trump', 'pattern': r'Trump|Trumpa|Trumpovi|Trumpom', 'count': 0},
          {'term': 'Biden', 'pattern': r'Biden|Biden|Bidenovi|Bidenom', 'count': 0}]


def check_terms(data):

    for html in data:

        for topic in topics:
            pattern = re.compile(topic['pattern'])
            found = re.findall(pattern, html)
            if len(found) > 0:
                topic['count'] += len(found)


async def launch():
    resps = await asyncio.gather(*map(get_async, urls))
    data = [resp.content.decode('utf8') for resp in resps]
    check_terms(data)

    for topic in topics:
        print(topic['term'], topic['count'])

asyncio.run(launch())
```


## XML

https://github.com/janbodnar/Python-Skolenie/tree/master/stdlib/xml

```python
import xml.sax

class ProductHandler(xml.sax.ContentHandler):
    def __init__(self):
        self.current_data = ""
        self.id = ""
        self.name = ""
        self.price = ""
        self.quantity = ""

    # Call when an element starts
    def startElement(self, tag, attributes):
        self.current_data = tag
        if tag == "product":
            print(f"\nProduct ID: {attributes['id']}")

    # Call when an element ends
    def endElement(self, tag):
        if self.current_data == "name":
            print(f"Name: {self.name}")
        elif self.current_data == "price":
            print(f"Price: {self.price}")
        elif self.current_data == "quantity":
            print(f"Quantity: {self.quantity}")
        self.current_data = ""

    # Call when a character is read
    def characters(self, content):
        if self.current_data == "name":
            self.name = content
        elif self.current_data == "price":
            self.price = content
        elif self.current_data == "quantity":
            self.quantity = content

if __name__ == "__main__":
    # Create an XMLReader
    parser = xml.sax.make_parser()
    
    # Turn off namespace
    parser.setFeature(xml.sax.handler.feature_namespaces, 0)
    
    # Override the default ContextHandler
    Handler = ProductHandler()
    parser.setContentHandler(Handler)
    
    # Parse the XML file
    parser.parse("products2.xml")
```


## CSV

https://github.com/janbodnar/Python-Skolenie/blob/master/stdlib/csv/README.md

```python
import csv
vals = []

with open('numbers.csv', 'r') as f:

    reader = csv.reader(f)

    for row in reader:

        for e in row:
            print(e)
            vals.append(int(e))
print(vals)
```

-- delimiter iny 

```python
import csv

with open('items.csv', 'r') as f:

    reader = csv.reader(f, delimiter="|")

    for row in reader:

        for e in row:
            print(e)
```python

--zahlavia csv

```python
import csv

with open('values.csv', 'r') as f:

    reader = csv.DictReader(f)

    for row in reader:
        print(row['min'], row['avg'], row['max'])
```

--basic stats

```python
import csv
import statistics

salaries = []

with open('users.csv', 'r') as f:

    reader = csv.DictReader(f)
    total_salaries = 0

    for row in reader:
        salary = int(row['salary'])
        total_salaries += salary
        salaries.append(salary)

# print(salaries)
print('total:', total_salaries)
print('count:', len(salaries))
print('max:', max(salaries))
print('min:', min(salaries))
print('average:', statistics.mean(salaries))
print('median:',statistics.median(salaries))
```


-- zapisovanie do csv s hlavickou

```python
import csv

with open('names.csv', 'w') as f:

    fnames = ['first_name', 'last_name']
    writer = csv.DictWriter(f, fieldnames=fnames)

    writer.writeheader()
    writer.writerow({'first_name' : 'John', 'last_name': 'Smith'})
    writer.writerow({'first_name' : 'Robert', 'last_name': 'Brown'})
    writer.writerow({'first_name' : 'Julia', 'last_name': 'Griffin'})
```

## fetch csv data

```python
import requests
import csv


def dowload_data():

    url = 'https://webcode.me/users.csv'

    resp = requests.get(url)
    data = resp.text

    filename = 'users3.csv'
    with open(filename, 'w') as f:

        f.write(data)


def read_users():

    users = []

    filename = 'users3.csv'
    with open(filename, 'r') as f:

        reader = csv.DictReader(f)

        for line in reader:
            users.append(line)


    print(users[:11])

# dowload_data()
read_users()
```


## Pythov virtual env

https://github.com/janbodnar/Python-Skolenie/blob/master/venv.md

- virtualne prostredie
  - vytvorit adresar a otvorit ho vo vs code
  - vytvorenie virt. prostredia    py -m venv myenv
  - akivacia                   myenv\Scripts\activate
  - deaktivacia
  - requirements.tx           pip install -r requirements.txt
 
## POSTGRES

https://www.enterprisedb.com/downloads/postgres-postgresql-downloads

![image](https://github.com/user-attachments/assets/eff5c7d2-049f-458a-88f0-0ef3debbeda3)

-- https://github.com/janbodnar/Python-Skolenie/blob/master/data/countries_postgre.sql

-- https://github.com/janbodnar/Python-Skolenie/blob/master/libs/psycopg.md


## funkcy -  practical functional programming tools for Python
https://github.com/janbodnar/Python-Skolenie/blob/master/libs/funcy.md


