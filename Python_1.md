# Python

![image](https://github.com/user-attachments/assets/e5f0648e-3e85-4b22-96c1-c2143d763bd2)

instalacia:

https://www.python.org/downloads/
![image](https://github.com/user-attachments/assets/a116c9f3-ac09-4318-93c4-5c1c8f0858e7)

Python Docs:
![image](https://github.com/user-attachments/assets/a1f82eb8-1e5d-40ea-8b03-cc169b487c51)


- studium: Try it Yourself - vies si vyskusat nejake veci
https://www.w3schools.com/python/default.asp

- softver na organizaciu kodu 
  -  Visual Studiou Code
  -  PyCharm

- mu editor: pre zaciatocnikov vhodny
https://codewith.mu/

- blaho python
https://python.input.sk/


- operatory:
  https://www.w3schools.com/python/python_operators.asp

- datove typy:
  https://www.w3schools.com/python/python_datatypes.asp

- boolean typ
  https://www.w3schools.com/python/python_booleans.asp
  https://www.w3schools.com/python/python_numbers.asp

- niektore vstavane funkcie
https://www.w3schools.com/python/python_ref_functions.asp

- pretypovanie: int(), float(), str()
https://www.w3schools.com/python/python_casting.asp

- klucove slova:
https://www.w3schools.com/python/python_ref_keywords.asp


```python
# tento prikaz retazec na obrazovku
a = 4
print("IT learning", a, end="@")
print()
print("Bratislava") # aj tento prikaz
print("Bratislava","Trnava","Kosice", sep="*")
```

- Python if...else
https://www.w3schools.com/python/python_conditions.asp

```python
# Napíšte program, ktorý pomocou príkazu input prečíta meno študenta
# a jeho vek.
# Potom to vypíše pomocou príkazu print a tiež vypíše informáciu jeho veku
# o rok a aj o 10 rokov. 
#Po spustení programu môžete dostať takýto výpis:

## zadaj meno: Ema
## zadaj vek: 17

## Ema má 17 rokov
## Ema bude mať o rok 18
## Ema bude mať o 10 rokov 27

meno= input("Zadaj meno studenta: ")
vek= int(input("Zadaj vek sudenta: "))
if meno != None:
    print(meno, " ma ", vek," rokov")
    print(meno, " bude mat o rok ", vek+1," rokov")
    print(meno, " bude mat o 10 rokov ", vek+10," rokov")
```


```python
a=int(input("Vloz 1. cislo: "))
b=int(input("Vloz 2. cislo> " ))

if a > b:
    print("cislo",a,"je vacsie ako ",b )
elif b>a:
    print("cislo",a,"je mensie ako ",b )
else:
    print("cislo ",a,"je rovne ",b )
```

- for cyklus
```python
# vypis vedla seba n- krat lubovolny tetazec oddeleny memdzerou
retazec=input("Zadaj opakujuci sa retazec: ")
pocet=int(input("Zadaj pocet: "))
'''
if retazec != None:
    print(pocet * retazec)
'''
for i in range(pocet):
    print(retazec, end=" ")
print("\nKonec programu")
```

```python
# vypis vedla seba n- krat lubovolny tetazec oddeleny memdzerou
retazec=input("Zadaj opakujuci sa retazec: ")
pocet=int(input("Zadaj pocet: "))
'''
if retazec != None:
    print(pocet * retazec)
'''
# ak ma range 1 parameter ide od 0 do n-1
# ak ma range 2 parametre ide od a do n-1  range(a,n)
# ak ma range 3 parametre ide od a do n-1, v kroku b range(a,n,b)

for i in range(pocet):
    if i< pocet-1:
        print(i, retazec, end=" ")
    else:
        print(i, retazec)
print("\nKonec programu")
```

- importovanie kniznic
import ramdom
import time
- alias
import time as t

potom volanie funkcie sleep napr.:
t.sleep(2)


```python
# vypis vedla seba n- krat lubovolny tetazec oddeleny memdzerou
import random
import time as t
retazec=input("Zadaj opakujuci sa retazec: ")
'''
pocet=int(input("Zadaj pocet: "))

if retazec != None:
    print(pocet * retazec)
'''
pocet = random.randint(5,20)
print("Pocet je: ", pocet)
# ak ma range 1 parameter ide od 0 do n-1
# ak ma range 2 parametre ide od a do n-1  range(a,n)
# ak ma range 3 parametre ide od a do n-1, v kroku b range(a,n,b)

for i in range(pocet):
    if i< pocet-1:
        print(i, retazec, end=" ")
        t.sleep(2)
    else:
        print(i, retazec)
print("\nKonec programu")
```


https://www.w3schools.com/python/python_while_loops.asp

![image](https://github.com/user-attachments/assets/a1fa4d8b-1a9e-43b2-acad-e469a9bc7867)


- stvorec + obdlznik
```python
'''

napíšte program, ktory vytvori stvorec so zadanym poctom hviezdiciek
Môžete dostať takýto výstup:
zadaj a: 5
*****
*****
*****
*****
*****

'''
#stvorec1
a = int(input("Zadaj dlzku strany stvorca: "))
print()
for i in range(a):
    print(a * "* ")

print()
#stvorec 2:
for m in range(a):
    for n in range(a):
        print("*", end=" ")
    print()

# obdlznik
a= int(input("Zadaj dlzku strany obdlznika: ") )
b= int(input("Zadaj sirku strany obdlznika: "))

#obdlznik1
print()
for i in range(b):
    print(a * "* ")

#obdlznik2
print()
for m in range(b):
    for n in range(a):
        print("*", end=" ")
    print()
```

```python
# trojuholnik rovnoramenny pravouhly
a= int(input("Zadaj dlzku strany trojuholnika: ") )
print()
print()
for i in range(a+1):
    print(i * "* ")

print()
for i in range(a,0,-1):
    print(i * "* ")
```

- Vynimky
  https://www.w3schools.com/python/python_try_except.asp

- list - editovatelne
https://www.w3schools.com/python/python_lists.asp
```python
thislist = ["apple", "banana", "cherry"]
print(thislist)
```

- tuple - needitovatelne
https://www.w3schools.com/python/python_tuples.asp

- built-in funkcie list
https://www.w3schools.com/python/python_ref_list.asp 
![image](https://github.com/user-attachments/assets/7a01d7bb-9bb5-4571-87b9-814ca2fcc4d9)


```python
thistuple = ("apple", "banana", "cherry")
print(thistuple)
```

- funkcie:
https://www.w3schools.com/python/python_functions.asp

```python
# hadzeme kockou 20 krat
# zapiseme do zoznamu a vypiseme ho
# zistit kolkokrat pdla 6

import random
#prazdny zoznam
#pokusy = list()
pokusy = []
for i in range(20):
    pokusy.append(random.randint(1,6))
print(pokusy)
print("cislo 6 padlo: ", str(pokusy.count(6))," krat")

# parne neparne cisla hodene kockou
def parne(cislo):
    if cislo%2==0: return True
    else: return False

for item in pokusy:
    if parne(item):
        print(item, " je parne")
    else:
        print(item, " nie je parne")
```

```python
'''

Napiste program, ktory ponukne pouzivatelovi 10-krat zadat cislo
a po kazdom zadani mu "vylosuje" cislo v rozsahu 1-6.
Spocitajte spravne aj nespravne pokusy.

'''
import random
#prazdny zoznam
#pokusy = list()


n=0
t=0
cislo=0
cislop=0
for i in range(10):
    cislo = int(input("Zadaj cilo od 1 po 6: "))
    cislop = random.randint(1,6)
    if cislo==cislop:
        print("Bomba! Tvoje cislo ", cislo, " je rovnake ako moje")
        t+=1
    else:
        print("netrafil si!  Tvoje cislo ", cislo, " je ine ako moje", cislop)
        n+=1
print("Trafil si to" , t, " krat")
print("NEtrafil si to" , n, " krat")
```
