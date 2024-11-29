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
