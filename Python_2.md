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
