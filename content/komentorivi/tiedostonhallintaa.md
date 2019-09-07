---
date: "2016-09-08T21:08:16+03:00"
title: "Tiedostonhallintaa"
weight: 410
---

Seuraavassa luetellaan joitakin usein tarvittuja komentoja. Yhteistä näille on,
että kukin niistä pyrkii tekemään jonkin rajatun asian ja tekemään sen hyvin.
Monimutkaisempia tuloksia saa aikaan yhdistelemällä yksinkertaisia komentoja.

Aloitetaan tiedostojärjestelmän ja tiedostojen käsittelyyn käytettävillä komennoilla ja ohjelmilla.

Työhakemisto: `pwd` ja `cd`
===============================

Komentorivillä käyttäjällä on aina jokin hakemisto niin kutsuttuna *työhakemistona*.
Työhakemisto on se tiedostojärjestelmän hakemisto, johon annetut komennot kohdistuvat
ja josta käsiteltäviä tiedostoja etsitään, ellei käyttäjä erikseen toisin määrää.

Usein sanotaan, että "käyttäjä on hakemistossa xyz", ja sillä tarkoitetaan, että
hänen sen hetkisenä työhakemistona on hakemisto xyz.

* `pwd` tulostaa nykyisen työhakemiston absoluuttisen polun.
* `cd` vaihtaa työhakemistoksi pyydettyyn hakemistoon.
* Hakemisto voidaan antaa `cd`-komennolle:
   * *absoluuttisena* juuresta alkaen (`/`-merkillä alkaen): `/usr/share`
   * *suhteellisena* nykyisen työhakemiston suhteen: `Documents`, `../../usr`
* Erikoishakemistonimet: `.` ja `..`:
   * `.` on "tämä hakemisto". Esim. `/home/./pesasa` on sama kuin `/home/pesasa`
   * `..` yksi hakemisto juuren suuntaan. "Isä hakemisto"




{{% wrapper class="exercises" %}}
pwd ja cd (kokeillaan)
------------------------------

```no-highlight
pesasa@box:~ $ pwd
/home/pesasa
pesasa@box:~ $ cd /etc/cups
pesasa@box:/etc/cups $ pwd
/etc/cups
pesasa@box:/etc/cups $ cd ..
pesasa@box:/etc $ pwd
/etc
pesasa@box:/etc $ cd .
pesasa@box:/etc $ pwd
/etc
```

Huomaa, miten kehotteessa näkyvä työhakemisto muuttuu, kun käyttäjä vaihtaa hakemistoa.

{{% /wrapper %}}





Tiedostojen listaus: `ls`
===============================

Pyydetyn hakemiston sisällön voi tulostaa`ls` -komennolla.
Oletuksena, ellei muuta määrätä, tulostetaan nykyisen työhakemiston sisältö.

`ls Documents`
:    *Documents* -hakemiston sisältö

`ls -l`
:    Työhakemiston sisältö pitkässä tulostusmuodossa. (long)
     (tiedoston tyyppi, oikeudet, kovien linkkien määrä, omistaja, ryhmä, tiedoston koko, muutosaika, nimi)

`ls -a`
:    Työhakemiston sisältö, mukaan lukien pisteellä alkavat **piilotiedostot**.
     (all) (Pisteellä alkavat tiedostot piilotetaan yleensä.)

`ls -lh`
:    Työhakemiston sisältö pitkässä muodossa ja tiedostojen koot "ihmisen luettavassa
     muodossa".
     (human-readable) Tiedostojen kokoja ei näytetä tavuina vaan kilo-, mega- tai
     gigatavuina, jos järkevämpää.

Esimerkkitulosteita:

```no-highlight
pesasa@box:~ $ ls Documents/
Awesome-Tux.svg  komentoja.md  Kurssi.txt  penguin.png  uusihakemisto
pesasa@box:~ $ cd Documents/
pesasa@box:~/Documents $ ls -l
yhteensä 72
-rw-rw-r-- 1 pesasa pesasa 11220 syys  11 18:52 Awesome-Tux.svg
-rw-rw-r-- 1 pesasa pesasa 13469 syys  11 18:51 komentoja.md
-rw-rw-r-- 1 pesasa pesasa     0 syys  11 18:50 Kurssi.txt
-rw-rw-r-- 1 pesasa pesasa 40049 syys  11 18:52 penguin.png
drwxrwxr-x 2 pesasa pesasa  4096 syys  11 18:50 uusihakemisto
pesasa@box:~/Documents $ ls -a
.  ..  Awesome-Tux.svg  komentoja.md  Kurssi.txt  penguin.png  uusihakemisto
pesasa@box:~/Documents $ ls -lh
yhteensä 72K
-rw-rw-r-- 1 pesasa pesasa  11K syys  11 18:52 Awesome-Tux.svg
-rw-rw-r-- 1 pesasa pesasa  14K syys  11 18:51 komentoja.md
-rw-rw-r-- 1 pesasa pesasa    0 syys  11 18:50 Kurssi.txt
-rw-rw-r-- 1 pesasa pesasa  40K syys  11 18:52 penguin.png
drwxrwxr-x 2 pesasa pesasa 4,0K syys  11 18:50 uusihakemisto

```


{{% wrapper class="exercises" %}}

ls (kokeillaan)
----------------------------

1. Montako piilotiedostoa kotihakemistossasi on? Moniko niistä on hakemisto?
2. Mikä on tiedoston `/bin/bash` koko tavuina? Entä ihmisen luettavassa muodossa?
3. Mikä on tiedoston `/etc/profile` muutosaika?

{{% /wrapper %}}





Tiedoston luonti: `touch`
===============================

Tyhjän tiedoston (ei sisältöä, koko 0 tavua) voi luoda komennolla `touch`.

```no-highlight
pesasa@box:~ $ touch testi.txt
pesasa@box:~ $ ls -l testi.txt
-rw-rw-r-- 1 pesasa pesasa 0 maali  5 15:45 testi.txt
```

Jos kyseinen tiedosto on jo olemassa, sitä ei muuteta, mutta sen muokkauspäivämäärä päivitetään vastaamaan
kyseistä hetkeä. (Tai jotain muuta annettua aikaa)




Hakemiston luonti: `mkdir`
===============================

`mkdir` luo uuden hakemiston (make directory).

```no-highlight
pesasa@box:~ $ mkdir Documents/uusihakemisto
pesasa@box:~ $ mkdir /tmp/toinenhakemisto
```

Lisävalitsimella `-p` (parent) komennon saa luomaan polusta mahdollisesti puuttuvat hakemistot.

```no-highlight
pesasa@box:~ $ mkdir -p Documents/joku/monen/puuttuvan/hakemiston/takana/oleva
```







Tiedostojen järjestely: `cp` ja `mv`
===============================

Komentorivillä tiedostoja kopioidaan komennolla `cp` (copy) ja siirretään
komennolla `mv` (move). Tutustutaan näiden käyttöön muutamalla erilaisella esimerkillä.

Kopioi tiedoston `/etc/passwd` nykyisen työhakemiston alla olevaan hakemistoon `Documents`:
```no-highlight
pesasa@box:~ $ cp /etc/passwd Documents/
```


Kopio tiedoston `/etc/passwd` nykyisen työhakemiston alla olevan `Documents`-hakemiston sisältä
löytyvään `uusihakemisto`-nimiseen hakemistoon uudelle nimelle `salasanat`:
```no-highlight
pesasa@box:~ $ cp /etc/passwd Documents/uusihakemisto/salasanat
```


Kopioi tiedoston `/etc/passwd` nykyiseen työhakemistoon:
```no-highlight
pesasa@box:~ $ cp /etc/passwd .
```


Siirtää mykyisessä työhakemistossa olevan tiedoston `passwd` työhakemiston alla olevaan `Documents`-hakemistoon
nimellä `passut.txt`:
```no-highlight
pesasa@box:~ $ mv passwd Documents/passut.txt
```


Siirtää `passut.txt`-nimisen tiedoston työhakemiston alla olevasta `Documents`-hakemistosta työhakemistoon:
```no-highlight
pesasa@box:~ $ mv mv Documents/passut.txt .
```

Useampia tiedostoja voidaan myös kopioida tai siirtää kerralla, jos viimeisenä parametrina, eli kopioinnin
tai siirron kohteena, on hakemisto:
```no-highlight
pesasa@box:~ $ cp /etc/hosts /proc/cpuinfo Documents/uusihakemisto/
```

Kokeile edellä esiteltyjä komentoja.




Hakemiston kopiointi
-------------------------------

Jos halutaan kopioida kokonainen hakemisto sen sisältämine tiedostoineen, pitää kopiointi
tehdä *rekursiivisesti*. ([Rekursio](https://www.google.fi/search?q=recursion))

Kopioi hakemisto `/usr/share/doc/wget` sisältöineen työhakemistoon (`.`)
```no-highlight
pesasa@box:~ $ cp -r /usr/share/doc/wget .
```

Muuten sama, mutta `-a` tarkoittaa "archive", eli kopiointi pyrkii säilyttämään tiedostojen oikeudet,
omistajuudet ja aikaleimat samoina. (Hyödyllisimmillään root-oikeuksilla kopioitaessa, sillä
tavallisella käyttäjällä ei ole oikeutta asettaa tiedostojen omistajuuksia.)

```no-highlight
pesasa@box:~ $ cp -a /usr/share/doc/wget .
```




Tiedostojen poisto: `rm` ja `rmdir`
===============================

Tiedosto poistetaan komennolla `rm` (remove) ja tyhjä hakemosto poistetaan
komennolla `rmdir` (remove directory).

***Muista olla varovainen!***

```no-highlight
pesasa@box:~ $ rm passut.txt
pesasa@box:~ $ rmdir Documents/toinenhakemisto
```

Hakemiston voi poistaa myös `rm`-komennolla käyttämällä lisävalitsinta `-r` (recursive).
Tämä poistaa hakemiston **ja kaiken sen sisällön**. ***Varo!***

```no-highlight
pesasa@box:~ $ rm -r Documents/uusihakemisto
```

Poistokomentojen kanssa ei voi koskaan olla liian varovainen. Usein hyvä tapa onkin ennen
poistoa suorittaa vastaava komentorivi korvaamalla `rm`-komento `ls`-komennolla, jolloin
saa nähtäväkseen, luettelon poistettavista tiedostoista. Jos tiedostot ovat oikeat, voi edellisen
komennon hakea takaisin komentohistoriasta ja vaihtaa tilalle `rm`-komennon.




Tiedostolinkit: `ln`
===============================

`ln`-komennolla luodaan tiedostojärjestelmään linkkejä ja symbolisia linkkejä.

Linkki
:   Levylle on fyysisesti tallennettu vain yksi tiedosto,
    mutta sillä voi tiedostojärjestelmässä olla useampi nimi, jotka sijaitsevat eri
    paikoissa hakemistopuuta.

Symbolinen linkki
:   "vain" viittaus johonkin toiseen, "oikeaan" tiedostoon.

```no-highlight
pesasa$box:~ $ ls -l /etc/printcap
lrwxrwxrwx 1 root root 22 Sep 24 21:30 /etc/printcap -> /var/run/cups/printcap
```

Luodaan työhakemistoon symbolinen linkki, jonka nimi on `copyright` ja joka viittaa
tiedostoon `/usr/share/doc/emacs/copyright`
```no-highlight
pesasa$box:~ $ ln -s /usr/share/doc/emacs/copyright
pesasa$box:~ $ ls -l copyright
lrwxrwxrwx 1 pesasa pesasa 30 maali  5 16:24 copyright -> /usr/share/doc/emacs/copyright
```

Luodaan `Documents`-hakemistoon symbolinen linkki, jonka nimi on oikeudet ja joka viittaa
tiedostoon `/usr/share/doc/emacs/copyright`.
```no-highlight
pesasa$box:~ $ ln -s /usr/share/doc/emacs/copyright Documents/oikeudet
pesasa$box:~ $ ls -l Documents/oikeudet
lrwxrwxrwx 1 pesasa pesasa 30 maali  5 16:27 copyright -> /usr/share/doc/emacs/copyright
```

Symbolista linkkiä voi käyttää useimpiin tarkoituksiin aivan samoin kuin varsinaista
tiedostoakin. Tiedoston luku-, kirjoitus- ja suoritusoikeuksiin koskevat alkuperäisen tiedoston oikeudet.







Tiedostoja verkosta: `wget`
===============================

Komentorivillä tiedostoja voi noutaa verkosta ohjelmalla nimeltä `wget`.

Haetaan kuva osoitteesta <http://petrit.net/Linux-kurssi/images/penguin.png>
komennolla:

`wget http://petrit.net/Linux-kurssi/images/penguin.png`

```no-highlight
pesasa@box:~ $ wget http://petrit.net/Linux-kurssi/images/penguin.png
--2016-09-11 19:31:03--  http://petrit.net/Linux-kurssi/images/penguin.png
Selvitetään osoitetta petrit.net (petrit.net)... 85.17.21.177
Yhdistetään palvelimeen petrit.net (petrit.net)|85.17.21.177|:80... yhdistetty.
HTTP-pyyntö lähetetty, odotetaan vastausta... 200 OK
Pituus: 14493 (14K) [image/png]
Tallennetaan kohteeseen ”penguin.png”

penguin.png              100%[==================================>]  14,15K  --.-KB/s    in 0,03s   

2016-09-11 19:31:03 (422 KB/s) - ”penguin.png” tallennettu [14493/14493]
```

Nimen, jolla tiedosto tallennetaan, voi valita valitsimella `-O` (iso O-kirjain).

`wget -O Documents/Tux.svg http://petrit.net/Linux-kurssi/images/Awesome-Tux.svg`

```no-highlight
pesasa@box:~ $ wget -O Documents/linux.html http://petrit.net/Linux-kurssi/images/Awesome-Tux.svg
--2016-09-11 19:35:34--  http://petrit.net/Linux-kurssi/images/Awesome-Tux.svg
Selvitetään osoitetta petrit.net (petrit.net)... 85.17.21.177
Yhdistetään palvelimeen petrit.net (petrit.net)|85.17.21.177|:80... yhdistetty.
HTTP-pyyntö lähetetty, odotetaan vastausta... 200 OK
Pituus: 1761180 (1,7M) [text/html]
Tallennetaan kohteeseen ”Documents/Tux.svg”

Documents/Tux.svg      100%[==================================>]   1,68M  2,89MB/s    in 0,6s    

2016-09-11 19:35:37 (2,89 MB/s) - ”Documents/Tux.svg” tallennettu [1761180/1761180]

```
