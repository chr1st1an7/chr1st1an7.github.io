---
layout: post
title: Algoritmi u Pythonu
date: 2023-11-16 20:00 +1000
categories: books
tags: python, notes
---


##  Korisni algoritmi
### Algoritam za određivanje znamenki broja

Da bismo saznali svaku znamenku u broju, dovoljno je konačan broj puta ponoviti sljedeći korak: "odredi zadnu desnu znamenku u broju te broj cjelobrojno podijeli s deset". Broj ponavljanja jednak je broju znamenki.

```python
N = int(input())
brojZnamenki = len(str(N))
for i in range(brojZnamenki):
    zn = N % 10
    print(zn)
    N = N // 10
```

Kako dobiti stotice, desetice i jedinice (s, d, j) nekog broja?

```python
N = 179
j = N % 10
d = (N // 10) % 10
s = N // 100
print(s, d, j)

>>> 1 7 9
```

### Algoritam za određivanje maksimalne vrijednosti

Algoritam za određivanje maksimalne vrijednosti jest prirodan i prati tijek našihmisli. Ideja je pratiti vrijednost trenutačnog maksimuma. Svaki put kad učitani broj bude strogo veći od trenutačnog maksimuma, zamijenimo vrijednost trenutačnog maksimuma učitanim brojem. Varijablu u kojoj pratimo trenutačni maksimum na početku inicijaliziramo na vrijednost koja će u tom trenutku biti najmanja moguća vrijednost koju ćemo razmatrati.

```python
N = int(input())
maks = 1

for i in range(N):
    x = int(input())
    if x  > maks:
        maks = x

print(maks)
```

### Algoritam za određivanje minimalne vrijednosti

U početku definiramo jednu varijablu i nju inicijaliziramo  na vrijednost koja će u tom trenutku biti najveća moguća vrijednost koju ćemo razmatrati. Python za ovu situaciju ima posebnu funkciju **float('inf')** koja vraća "beskonačno velik broj" tako da ga nikad nećemo prijeći prilikom usporedbi. Osim ove sitnice, kod  je isti kao kod određivanja maksimuma uz jednu promjenu relacijskog operatora.

```python
N = int(input())
mini = float('inf') #  vraća "beskonačno velik broj" tako da ga nikad nećemo prijeći prilikom usporedbi

for i in range(N):
    x  = int(input())
    if x < mini:
        mini = x

print(mini)
```

Da ne znamo za funkciju **float('inf')** imali bismo problem kod inicijaliziranja početne vrijednosti minimuma. Kada ne znamo koliko velik broj može biti, koristimo ovu funkciju.

### Djelitelji broja i prosti brojevi

Kako možemo odrediti djelitelje nekog broja x? Djelitelji broja x svi su oni brojevi između 1 i x koji daju **ostatak 0** kad probamo x podijeliti s njima.

```python
for djelitelj in range(1, x + 1):
    if x % djelitelj == 0:
        print(djelitelj)
```

Broj je **prost** ako su jedini njegovi **djelitelji 1 i on sam**.
Broj je **složen** ako ga možemo faktorizirati u obliku *x = a * b*. To jest, ima više djelitelja osim 1 i samoga sebe.

Ako je broj x složen, onda on ima djelitelj koji je manji ili jednak vrijednosti drugoga korijena odx.

```python
from math import * # kako bi mogli koristiti naredbu sqrt()

x = int(input())
prost = True

for djelitelj in range(2, int(sqrt(x)) + 1):
    if x % djelitelj == 0:
        prost = False
        break

if prost:
    print(x, 'je prost')

else:
    print(x, 'je složen')
```

#### U Pythonu možemo kombinirati naredbe *else* i *for*.

Ako se naredba *else* napiše nakon *for*, onda se naredne u dijelu *else* izvode nakon što kontrolna varijabla poprimi zadnju vrijednost iz slijeda. to jest, nakon što for petlja završi.

```python
N = int(input())

for i in range(2, int(sqrt(N)) + 1):
    if N % i == 0:
        print('Broj je složen.')
        break
else:
    print('Broj je prost.')
```
