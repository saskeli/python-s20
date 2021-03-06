---
path: '/osa-3/1-ehdot-silmukoissa'
title: 'Ehdot silmukoissa'
hidden: false
---

<text-box variant='learningObjectives' name='Oppimistavoitteet'>

Tämän osion jälkeen

- Osaat tehdä while-silmukan, jonka alkurivillä on ehto
- Tiedät, mikä merkitys alustuksella, ehdolla ja muutoksella on silmukassa
- Osaat käyttää erilaisia ehtoja silmukoissa

</text-box>

Viime osan lopussa opimme käyttämään `while True` -silmukkaa koodin toistamiseen. Tässä tapauksessa silmukan ehtona on `True`, mikä on aina tosi. Yleisemmin voimme käyttää silmukkaa näin:

```python
while <ehtolauseke>:
    <lohko>
```

Ideana on, että silmukka vuorotellen tarkastaa ehdon ja suorittaa lohkossa olevan koodin, jos ehto pätee. Sitten kun ehto ei päde, ohjelman suoritus jatkuu silmukan jälkeiseltä riviltä.

<img src="3_1_1.png">

Esimerkiksi seuraavassa silmukassa ehtona on `luku < 10` eli silmukan koodi suoritetaan, jos luku on alle 10.

```python
luku = int(input("Anna luku: "))

while luku < 10:
    print(luku)
    luku += 1

print("Suoritus valmis.")
```

Ohjelman tulostus voi olla seuraava:

<sample-output>

Anna luku: **4**
4
5
6
7
8
9
Suoritus valmis.

</sample-output>

Koska ehto tarkastetaan aina ennen silmukan koodin suoritusta, on mahdollista, ettei koodia suoriteta kertaakaan. Esimerkiksi:

<sample-output>

Anna luku: **12**
Suoritus valmis.

</sample-output>

Koska 12 ei ole pienempi kuin 10, ohjelma ei tulosta mitään lukua:

## Alustus, testaus ja muutos

Monessa silmukassa on kolme osaa: alustus, testaus ja muutos.

_Alustus_ tarkoittaa silmukassa käytettävän muuttujan tai muuttujien alkuarvojen antamista. Tämä vaihe tehdään ennen silmukkaa. _Testaus_ kirjoitetaan silmukan alkuun, ja se määrittelee ehdon, jonka ollessa tosi silmukka suoritetaan. Joka kierroksella tapahtuva _muutos_ vie silmukan askeleen lähemmäs sen loppumista. Esimerkiksi:

<img src="3_1_2.png">

Jos jokin kolmesta osasta puuttuu, silmukka ei toimi oikein. Yksi tyypillinen virhe on muutoksen unohtaminen:

```python
luku = 1

while luku < 10:
    print(luku)

print("Suoritus valmis.")
```

Koska muuttujan `luku` arvo ei koskaan muutu, jää ohjelma suoritettaessa ikuiseen silmukkaan eli toistaa samaa koodia, kunnes käyttäjä katkaisee ohjelman suorituksen (esimerkiksi painamalla `CTRL` + `C`):

<sample-output>

1
1
1
1
1
(tämä jatkuu ikuisesti...)

</sample-output>


## Ehdoista tarkemmin

Silmukan ehtona voidaan käyttää mitä tahansa ehtolauseketta. Esimerkiksi seuraava ohjelma tulostaa lukuja kolmen välein niin kauan kun luku on pienempi kuin 100 eikä se ole jaollinen 5:llä:

```python
luku = int(input("Anna luku: "))

while luku < 100 and luku % 5 != 0:
    print(luku)
    luku += 3
```

Kaksi esimerkkitulostusta eri syötteillä:

<sample-output>

Anna luku: **28**
28
31
34
37
...

</sample-output>

<sample-output>

Anna luku: **96**
96
99

</sample-output>

Luvun 28 kohdalla silmukka päättyy lukuun 37, koska seuraava luku 40 on jaollinen 5:llä. Luvun 96 kohdalla silmukka päättyy lukuun 99, koska seuraava luku 102 ei ole alle 100.

Silmukan ehtoa kirjoittaessa on tärkeä varmistua siitä, että silmukan suoritus päättyy. Esimerkiksi seuraava ohjelma on joko päättyvä tai ei-päättyvä riippuen alkuarvosta:

```python
luku = int(input("Anna luku: "))

while luku != 10:
    print(luku)
    luku += 2
```

Jos syötteeksi parillinen luku, joka on enintään 10, silmukan suoritus päättyy:

<sample-output>

Anna luku: **4**
4
6
8

</sample-output>

Muissa tapauksissa silmukka on kuitenkin ikuinen, koska muuttuja ei koskaan saavuta arvoa 10. Tällaisia syötteitä ovat esimerkiksi 3 ja 12.
