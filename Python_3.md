-- kod prezencka 3899
-- https://iwww.vse.sk/sys/app/contacts/#/a/es

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
