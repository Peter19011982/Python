## OPAKOVANIE

```python
import funcy

words = ['sky', 'dout', 'war', 'pike', 'now', 'teen']
# words3 = [word for word in words if len(word) == 3]
# words4 = [word for word in words if len(word) == 4]
words3, words4 = funcy.split(lambda word: len(word) == 3, words)

words3 = list(words3)
words4 = list(words4)

assert words3 == ['sky', 'war', 'now'] and words4 == ['dout', 'pike', 'teen'], 'failed'
print('passed')
```

```python
import requests

url = 'https://webcode.me/words.txt'

resp = requests.get(url)
text = resp.text
words = text.split()

number_of_words = len(words)


assert number_of_words == 26, 'failed'
print('passed')
```

data.txt
I quickly followed suit, and descending into the bar-room accosted the grinning 
landlord very pleasantly. I cherished no malice towards him, though he had been 
skylarking with me not a little in the matter of my bedfellow.
However, a good laugh is a mighty good thing, and rather too scarce a good thing; 
the more’s the pity. So, if any one man, in his own proper person, afford stuff for 
a good joke to anybody, let him not be backward, but let him cheerfully allow himself 
to spend and be spent in that way. And the man that has anything bountifully laughable 
about him, be sure there is more in that man than you perhaps think for.

```python
filename = 'data.txt'

with open(filename, 'r') as f:
    ...
    number_of_words = ...

assert number_of_words == 117, 'failed'
print('passed')
```


```python

# write script that reads data from 
# https://webcode.me/users.xml, use copilot
import requests
import xml.etree.ElementTree as ET

# URL of the XML data
url = 'https://webcode.me/users.xml'

# Fetch the XML data
response = requests.get(url)
xml_data = response.content

# Parse the XML data
root = ET.fromstring(xml_data)

# Define the namespace
namespace = {'ns': 'zetcode.com'}

# Iterate through each user and print their details
for user in root.findall('ns:user', namespace):
    user_id = user.get('id')
    firstname = user.find('ns:firstname', namespace).text
    lastname = user.find('ns:lastname', namespace).text
    occupation = user.find('ns:occupation', namespace).text
    
    print(f'User ID: {user_id}')
    print(f'First Name: {firstname}')
    print(f'Last Name: {lastname}')
    print(f'Occupation: {occupation}')
    print('---')
```


## SORTING
-- https://github.com/janbodnar/Python-Skolenie/blob/master/sort.md

```python
words = ['forest', 'wood', 'brisk', 'tree', 'sky', 'cloud', 'rock', 'falcon']
#sorted
sorted_words = sorted(words)
print('Original:', words)
print('Sorted:', sorted_words)

# sort
words = ['forest', 'wood', 'tool', 'arc', 'sky', 'poor', 'cloud', 'rock']

words.sort()
print(words)

words.sort(reverse=True)
print(words)
```


--sortovanie podla kluca
https://github.com/janbodnar/Python-Skolenie/blob/master/sort.md#sort-list-by-element-index

```python
vals = [(4, 0), (0, -2), (3, 5), (1, 1), (-1, 3)]

vals.sort()
print(vals)

vals.sort(key=lambda e: e[1])
print(vals)
```

-- sortovanie podla sumy:

```python
data = [[10, 11, 12, 13], [9, 10, 11, 12], [8, 9, 10, 11], [10, 9, 8, 7],
    [6, 7, 8, 9], [5, 5, 5, 1], [5, 5, 5, 5], [3, 4, 5, 6], [10, 1, 1, 2]]

data.sort()
print(data)

data.sort(key=sum)
print(data)
```

