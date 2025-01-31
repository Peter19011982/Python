```python
# 3916 prezencne

# print message John Doe is a gardener and live in 
# in New York
name = 'John Doe'
occupation = 'gardener'
city = 'New York'

msg = f'{name} is a {occupation} and lives in {city}'
print(msg)


# calculate sum
# split, int
data = "1,2,3,4,5,6,7,8,9,10"

mysum = 0
fields = data.split(',')

print(fields)

for field in fields:
    mysum += int(field)

print(mysum)


# calculate sum
mysum2 = 0
data2 = ((1, 2, 3), (4, 5, 6), (7, 8, 9), (10, 11, 12))

for nested in data2:
    for e in nested:
        mysum2 += e

print(mysum2)

# create a new tuple that contains words starting with w or c
# startswith
words = ['small', 'cup', 'war', 'water', 'cloud', 'warm', 'atom']
words_w_c = []

for word in words:
    if word.startswith(('w', 'c')):
        words_w_c.append(word)

words_final = tuple(words_w_c)
print(words_final)

# read file words.txt and calculate the number 
# of all ascii characters of all words
# open

file_name = 'words.txt'
ascii_chars = 0

with open(file_name, 'r') as f:

    for line in f:
        word = line.rstrip()
        ascii_chars += len(word)

    print(ascii_chars)
```

https://github.com/janbodnar/Python-Skolenie/blob/master/terms.md

https://github.com/janbodnar/Python-Skolenie/blob/master/functions.md

```python
#!/usr/bin/python

def fn():
    return [1, 2, 3, 4, 5, 6]

a, b, c, d, e, f = fn()
print(a, b, c, d, e, f)

a, *mid, b = fn()
print(a, mid, b)

a, b, c, _, _, _ = fn()
print(a, b, c)

a, b, *_ = fn()
print(a, b)

a, b, c, *d = fn()
print(a, b, c, d)

*a, b, c, d = fn()
print(a, b, c, d)
```

--Function redefinition

```python
#!/usr/bin/python

# redefinition.py

from time import gmtime, strftime


def showMessage(msg):

    print(msg)


showMessage('Ready.')


def showMessage(msg):

    print(strftime('%H:%M:%S', gmtime()))
    print(msg)


showMessage('Processing.')

```

-- funkciu musis najprv zadefinovat a az potom volat


https://github.com/janbodnar/Python-Skolenie/blob/master/functions.md#collection-of-functions

-- Funkcie map a filter
- priamo implementovane build-in

```python
#map
#filter
negative_vals = []
vals=[-3,4,0,2,-1,0,9,-9]

# for val in vals:
#     if val <0:
#         negative_vals.append(val)

def is_negative(e):
    if e<0:
        return True
    
negative_vals = list(filter(is_negative,vals))
print(negative_vals)


def is_positive(e):
    if e>0:
        return True

positive_vals = list(filter(is_positive,vals))
print(positive_vals)
```

-- LAMBDA funkcia da sa pouzit len raz, ak ju chcem viackrat pouzit vzdy ju musime znova zadefinovat ...negative_vals = list(filter(lambda e: e< 0,vals))
```python
#map
#filter
negative_vals = []
positive_vals = []
vals=[-3,4,0,2,-1,0,9,-9]

# for val in vals:
#     if val <0:
#         negative_vals.append(val)

# def is_negative(e):
#     if e<0:
#         return True
    
# negative_vals = list(filter(is_negative,vals))
# print(negative_vals)

#LAMBDA - anonymim vnorena funkcia
negative_vals = list(filter(lambda e: e< 0,vals))
print(negative_vals)

def is_positive(e):
    if e>0:
        return True

positive_vals = list(filter(is_positive,vals))
print(positive_vals)
```

-- bezna def funkcia vs lambda 

```python
words = ['apple','word','wrap','peter', 'jozo', 'cela']


def starts_with_w(word):
    if word[0] == 'w':
        return True

words_w= list(filter(starts_with_w, words))
print(words_w)
words_w=list(filter(lambda w: w[0]=='w', words ))
print(words_w)

words_w_c=list(filter(lambda w: w[0]=='w' or w[0]=='c', words ))
print(words_w_c)

words_w_c=list(filter(lambda w: w[0]  in ('w' ,'c'), words ))
print(words_w_c)
```

-- pouzitie map

```python
def twice(x):
    return x*2

vals = [1,11,2,3,3]

vals2 = list(map(twice,vals))
print(vals)
print(vals2)

vals3 = list(map(lambda e: e*2,vals))
print(vals3)
```


```python
data = '1,2,3,4,5,6,7,8,9,10'
fields = data.split(',')
#pretypovat
map(int, fields)
my_sum= sum(map(int, fields))
print(my_sum)
```


```python
file_name = 'words.txt'
with open(file_name, 'r') as f:
    data = f.readlines()
    print(data)
# (map(str.rstrip, data)  odstrani zo zonamu znak dalsi riadok
    words = list(map(str.rstrip, data))
    print(words)
```

-- funkcia faker   (pip install faker) - vie vytvarat testovacie data

```python
import faker 
faker = faker.Faker()

first_name = faker.first_name()
last_name = faker.last_name()

print(first_name,last_name)
```



---automaticky vygenerovany zoznam




```python
from dataclasses import dataclass
import requests

@dataclass(frozen=True)
class User:
    id: int
    first_name: str
    last_name: str
    occupation: str

url = 'https://webcode.me/users.csv'

resp = requests.get(url)
content = resp.content.decode('utf8')

lines = content.splitlines()

users = []

for line in lines[1:-1]:
    fields = line.split(',', 3)
    fields_cleaned = fields[0], fields[1], fields[2], fields[3].replace('"', '')

    u = User(*fields_cleaned)
    users.append(u)


for user in users:
    print(user)
```

```python
import faker

faker = faker.Faker()

first_name = faker.first_name()
last_name = faker.last_name()
city = faker.city()
state = faker.state()
email = faker.email()

print(first_name, last_name, city, state, email)

file_name = 'users.csv'

with open(file_name, 'w') as f:
    f.write('first_name,last_name,city,state,email\n')
    for _ in range(1000):
        first_name = faker.first_name()
        last_name = faker.last_name()
        city = faker.city()
        state = faker.state()
        email = faker.email()

        f.write(f'{first_name},{last_name},{city},{state},{email}\n')
```

-- citanie testovacich dat upravene
```python
file_name = 'users.csv'
with open(file_name, 'r') as f:
    for line in f:
        
        fields = line.rstrip().split(',')
        print(fields)

```

--Filtering users in file

```python
Filtering users in file
file_name = 'users.csv'

all = []
users_w = []

with open(file_name, 'r') as f:

    for line in f:
        fields = line.rstrip().split(',')
        all.append(fields)
        if fields[1].startswith('W'):
            users_w.append(fields)


    print(users_w)

    filtered = list(filter(lambda x: x[1].startswith('W'), all))
    # filtered = list(filter(lambda x: x[1][0] == 'W', all))
    print(filtered)

    print(users_w == filtered)
```

-- https://github.com/janbodnar/Python-Skolenie/blob/master/modules.md
-- modul je .py subor
- moduly do vacsich celkov packages
- empty.py moze byt nejaky dokumentacny modul a v main.py ho mozes importovat a potom otvorit ctrl+klik a pristupit k empty.py 


![image](https://github.com/user-attachments/assets/2bbb9d22-b034-4613-baf8-3bde28bc2b70)

![image](https://github.com/user-attachments/assets/9526a884-5e77-4052-b392-bb308ada27c5)

--dokumentacne retazce

```python
import empty
import sys
import math

print(empty.__name__)
print(empty.__doc__)

print(math.ceil.__doc__)
```

-- kde python prehladava moduly

```
import sys
# kde sa prehladavaju moduly
print(sys.path)
```







-- This is dirfun module
-- Python dir function
-- The built-in dir function gives a sorted list of strings containing the names defined by a module.

```python
import math, sys

version = 1.0

names = ["Paul", "Frank", "Jessica", "Thomas", "Katherine"]

def show_names():

   for i in names:
      print(i)

print(dir())
```

-- ImportError

```python
try:
    # Non-existent module
    import numpy12
except ImportError:
    print('Module not found')
```


--import modulu a odkaz na funckiu z ineho modulu

```python
import utils
words= ['cat','blue','skies','dog']

print(utils.filter_len_4(words))

--main.py
# import sys
# # kde sa prehladavaju moduly
# print(sys.path)

# import empty
# import sys
# import math

# print(empty.__name__)
# print(empty.__doc__)

# print(math.ceil.__doc__)
```

--utils.py

```python
def filter_len_4(words):
    return list(filter(lambda word: len(word) == 4, words))
```


![image](https://github.com/user-attachments/assets/7bcd057f-fad1-4b7f-b831-7cd5a6cee286)



--DATABAZA  SQL
https://github.com/janbodnar/Python-Skolenie/tree/master/stdlib

https://github.com/janbodnar/Python-Skolenie/blob/master/stdlib/smtplib/README.md

novy modul nainstalovat: sqlite viewer  - len na zobrazenie
ak chcem aj zapis, tak stiahnem a nainstalujem
https://sqlitebrowser.org/dl/

```python
import sqlite3
import sys

con = sqlite3.connect('test.db')

with con:
    
    cur = con.cursor()    
    cur.execute('SELECT SQLITE_VERSION()')
    
    version = cur.fetchone()
    
    print("SQLite version: {}".format(version[0]))
```

--vytvorenie tabulky a naplnenie

```python
import sqlite3

con = sqlite3.connect('test.db')

with con:
    
    cur = con.cursor()  
    #cur.execute("DROP TABLE IF EXISTS cities")  
    cur.execute("CREATE TABLE cities(id INTEGER PRIMARY KEY, name TEXT, population INT)")
    cur.execute("INSERT INTO cities(name, population) VALUES('Bratislava', 432000)")
    cur.execute("INSERT INTO cities(name, population) VALUES('Budapest', 1759000)")
    cur.execute("INSERT INTO cities(name, population) VALUES('Prague', 1280000)")
    cur.execute("INSERT INTO cities(name, population) VALUES('Warsaw', 1748000)")
    cur.execute("INSERT INTO cities(name, population) VALUES('Los Angeles', 3971000)")
    cur.execute("INSERT INTO cities(name, population) VALUES('New York', 8550000)")
    cur.execute("INSERT INTO cities(name, population) VALUES('Edinburgh', 464000)")
    cur.execute("INSERT INTO cities(name, population) VALUES('Suzhou', 4327066)")
    cur.execute("INSERT INTO cities(name, population) VALUES('Zhengzhou', 4122087)")
    cur.execute("INSERT INTO cities(name, population) VALUES('Berlin', 3671000)")
```


```python
import sqlite3
import sys

con = sqlite3.connect('test.db')

with con:
    
    cur = con.cursor()    
    cur.execute('SELECT SQLITE_VERSION()')
    cur.execute('SELECT * from cities')
    
    version = cur.fetchone()
    rows = cur.fetchall()
    
    print("SQLite version: {}".format(version[0]))
    for row in rows:
        print(row)
```

--CVICENIE filter a map

```python
# create a list of integers only
vals = [1, 2, 3, 4, 5, "12", 4, "21", -1, "3"]

filtered = list(filter(lambda x: isinstance(x, int), vals))
vals_cleaned = list(map(int,vals))
print(filtered)
print(vals_cleaned)


# filter numbers from the list
mixed = [True, False, 1, 0, "True", "False", "1", "0", -1, "1", 11.5, 12, 1.2]
filtered1 = list(filter(lambda x: isinstance(x,(int)), mixed))
print(filtered1)
vals_cleaned2 = list(filter(lambda x: type(x) == int or type(x) == float, mixed))
print(vals_cleaned2)

# filter tuples with sum > 10
data = ((3, 4, 2), (3, 3, 4), (4, 4, 4), (3, 3, 3), (1, 1, 1), (1, 2, 3))
filtered3= list(filter(lambda e: sum(e)>10, data))
print(filtered3)

# transform the list into lowercased strings
words = ["apple", "Banana", "cherry", "orangE", "KIWI", "maNgo"]
words_lower= list(map(lambda e: e.lower(), words))
print(words_lower)

# filter users with age > 40
users = [
    {"first_name": "John", "last_name": "Doe", "age": 30},
    {"first_name": "Jane", "last_name": "Doe", "age": 25},
    {"first_name": "John", "last_name": "Smith", "age": 43},
    {"first_name": "Jane", "last_name": "Smith", "age": 35},
    {"first_name": "John", "last_name": "Doe", "age": 20},
    {"first_name": "Paul", "last_name": "Black", "age": 55},
    {"first_name": "John", "last_name": "Smith", "age": 60},
    {"first_name": "Robert", "last_name": "Smith", "age": 5},
]

users_only_40 = list(filter(lambda user: user["age"] > 40, users))
print(users_only_40)
```

-- OBJEKTY
https://github.com/janbodnar/Python-Skolenie/blob/master/oop.md


--trieda class
```python
#!/usr/bin/python

# first_object.py
#toto je nedokoncena trieda - prazdna
class First:
    pass

#vytvorenie objektu z triedy
fr = First()

print(type(fr))
print(type(First))
```

-- Object initialization
-- ak je funkcia zadefinoavna v triede, vzy musi mat prve: def __init__(self):

```python
#!/usr/bin/python

# object_initialization.py

class Being:

    def __init__(self):
        print("Being is initialized")

Being()
```

--KONSTRUKTOR sa vola vtedy, ked chceme inicializovat hodnotu

```python
#!/usr/bin/python

# object_initialization.py

class Being:

    def __init__(self):
        print("Being is initialized")

b1 = Being()
b2 = Being()
b3 = Being()
b4 = Being()
```
-- PREFEROVANY sposob cez konstruktor definicie premennej
```python
#!/usr/bin/python

# attributes.py

class Cat:

    def __init__(self, name):

        self.name = name

missy = Cat('Missy')
lucky = Cat('Lucky')

print(missy.name)
print(lucky.name)
```
--nepreferovany sposom definicie premennej

```python
class Person:
    pass

p = Person()
p.age = 24
p.name = "Peter"
p.occupation = "teacher"

print("{0} is {1} years old an is a {2}".format(p.name, p.age, p.occupation))

p2 = Person()
p2.age = 44
p2.name = "Jozef"
p2.occupation = "programmer"

print("{0} is {1} years old an is a {2}".format(p2.name, p2.age, p2.occupation))
```



--GETre a SETre
```python
#!/usr/bin/python

# methods.py

class Circle:

    pi = 3.141592

    def __init__(self, radius=1):
        self.radius = radius

    def area(self):
        return self.radius * self.radius * Circle.pi

    def setRadius(self, radius):
        self.radius = radius

    def getRadius(self):
        return self.radius


c = Circle()

c.setRadius(5)
print(c.getRadius())
print(c.area())
```

## Rectangle

```
class Rectangle:
    
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height
    
    def set_width(self, width):
        self.width = width
    
    def set_height(self, height):
        self.height = height

    def get_width(self):
        return self.width

    def get_height(self):
        return self.height


r1 = Rectangle(10, 20)
print(r1.area())

r1.set_width(30)
r1.set_height(40)

print(r1.area())
```

## Object quality

```
class User:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    # def __eq__(self, other):
    #     if isinstance(other, User):
    #         return self.name == other.name and self.age == other.age
    #     return False

u1 = User("John Doe", 35)
u2 = User("John Doe", 35)

u3 = u1

print(u1 == u2)  #false - ak eq nieje definovane
print(u1 == u3)  #True - ak eq nieje definovane
```

## Equals metoda ak chcem porovnat HODNOTY

```python
class User:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __eq__(self, other):
        if isinstance(other, User):
            return self.name == other.name and self.age == other.age
        return False

u1 = User("John Doe", 35)
u2 = User("John Doe", 35)

u3 = u1

print(u1 == u2)  # True - ak je eq metada definovana - zistuje ci maju rovanke hodnoty
print(u1 == u3)  # True - ak je eq metada definovana
```

