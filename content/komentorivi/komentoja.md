+++
date = "2016-09-08T21:08:16+03:00"
title = "Komentoja"
weight = 410
+++

Seuraavassa luetellaan joitakin usein tarvittuja komentoja. Yhteistä näille on,
että kukin niistä pyrkii tekemään jonkin rajatun asian ja tekemään sen hyvin.
Monimutkaisempia tuloksia saa aikaan yhdistelemällä yksinkertaisia komentoja.

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




Hakemiston luonti: `mkdir`
===============================

`mkdir` luo uuden hakemiston (make directory).

```no-highlight
pesasa@box:~ $ mkdir Documents/uusihakemisto
pesasa@box:~ $ mkdir /Documents/tmp/toinenhakemisto
```



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


ls (kokeillaan)
----------------------------

1. Montako piilotiedostoa kotihakemistossasi on? Moniko niistä on hakemisto?
2. Mikä on tiedoston `/bin/bash` koko tavuina? Entä ihmisen luettavassa muodossa?
3. Mikä on tiedoston `/etc/profile` muutosaika?








Tiedostojen järjestely: `cp` ja `mv`
===============================

Komentorivillä tiedostoja kopioidaan komennolla `cp` (copy) ja siirretään
komennolla `mv` (move).

* `cp /etc/passwd Documents/` <br>
   Kopioi tiedoston `/etc/passwd` nykyisen työhakemiston alla olevaan hakemistoon `Documents`
* `cp /etc/passwd Documents/uusihakemisto/salasanat` <br>
   Kopio tiedoston `/etc/passwd` nykyisen työhakemiston alla olevan `Documents`-hakemiston sisältä
   löytyvään `uusihakemisto`-nimiseen hakemistoon nimellä `salasanat`.
* `cp /etc/passwd .`
   Kopioi tiedoston `/etc/passwd` nykyiseen työhakemistoon.
* `mv passwd Documents/passut.txt`
   Kopioi mykyisessä työhakemistossa olevan tiedoston `passwd` työhakemiston alla olevaan `Documents`-hakemistoon
   nimellä `passut.txt`.
* `mv Documents/passut.txt .`
   Siirtää `passut.txt`-nimisen tiedoston työhakemiston alla olevasta `Documents`-hakemistosta työhakemistoon.

Voidaan kopioida tai siirtää myös useampia tiedosto kerrallaan, kun viimeisenä parametrina on hakemisto:

* `cp /etc/hosts /proc/cpuinfo Documents/uusihakemisto/`

Kokeile!




Hakemiston kopiointi
-------------------------------

Jos halutaan kopioida kokonainen hakemisto sen sisältämine tiedostoineen, pitää kopiointi
tehdä *rekursiivisesti*.

* `cp -r /usr/share/doc/wget .`
   * "Kopioi hakemisto `/usr/share/doc/wget` sisältöineen työhakemistoon (`.`)"
* `cp -a /usr/share/doc/wget .`
   * Muuten sama, mutta `-a` tarkoittaa "archive", eli kopiointi pyrkii säilyttämään
     tiedostojen oikeudet ja omistajuudet samoina.
     (Hyödyllinen lähinnä root-oikeuksilla kopioitaessa, sillä tavallisella
      käyttäjällä ei ole oikeutta muuttaa tiedostojen omistajuuksia.)




Tiedostojen poisto: `rm` ja `rmdir`
===============================

Tiedosto poistetaan komennolla `rm` (remove) ja tyhjä hakemosto poistetaan
komennolla `rmdir` (remove directory).

* ***Muista olla varovainen!***
* `rm passut.txt`
* `rmdir Documents/toinenhakemisto`
* Hakemiston voi poistaa myös `rm`-komennolla käyttämällä lisävalitsinta `-r` (recursive).
  Tämä poistaa hakemiston ja kaiken sen sisällön. ***Varo!*** 
* `rm -r Documents/uusihakemisto`




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

* `ln -s /usr/share/doc/emacs/copyright`
   * Luo työhakemistoon symbolisen linkin, jonka nimi on `copyright` ja joka viittaa
     tiedostoon `/usr/share/doc/emacs/copyright`
* `ln -s /usr/share/doc/emacs/copyright Documents/oikeudet`
   * Luo `Documents`-hakemistoon symbolisen linkin, jonka nimi on `oikeudet` ja joka viittaa
     tiedostoon `/usr/share/doc/emacs/copyright`

Symbolista linkkiä voi käyttää useimpiin tarkoituksiin aivan samoin kuin varsinaista
tiedostoakin.






Tekstin tulostus `echo`
===============================

`echo` on komento, joka tulostaa annetun tekstin. 

```no-highlight
pesasa@box:~ $ echo Moikka, maailma
Moikka, maailma
pesasa@box:~ $ echo "Heippa vaan"
Heippa vaan
pesasa@box:~ $ echo 'Linux on pop'
Linux on pop
```

Voidaan tulostaa myös muuttujien arvoja:

```no-highlight
pesasa@box:~ $ echo $HOME
/home/pesasa
```

Lisäoptio `-n` jättää pois rivinvaihdon tulostuksen lopusta:

```no-highlight
pesasa@box:~ $ echo -n "Ei rivinvaihtoa"
Ei rivinvaihtoapesasa@kurssibuntu:~ $
```

Lisäoptio `-e` mahdollistaa erikoismerkkien käytön:

```no-highlight
pesasa@box:~ $ echo -e '1:\tyksi\n2:\tkaksi'
1:    yksi
2:    kaksi
```




echo ja lainausmerkit
------------------------------

`echo`-komennolla ja yleisestikin bashissa suoritettavilla komennoilla ja ohjelmilla on eroa yksinkertaisilla
ja kaksinkertaisilla lainausmerkeillä (`'`) ja (`"`).

* Yksinkertaisilla lainausmerkeillä merkityt merkkijonot käsitellään sellaisinaan.
* Kaksinkertaisilla lainausmerkeillä merkittujen merkkijonojen sisällä olevat muuttujanimet korvataan niiden arvoilla.

```no-highlight
pesasa$box:~ $ echo 'Kotihakemisto: $HOME'
Kotihakemisto: $HOME
```

mutta

```no-highlight
pesasa$box:~ $ echo "Kotihakemisto: $HOME"
Kotihakemisto: /home/pesasa
```

* Yksinkertaisten lainausmerkkien sisällä voidaan käyttää esim. erikoismerkkejä: `\n`
  (rivinvaihto),
  `\t` (vaakasarkain), `\v` (pystysarkain)
* Kaksinkertaisten lainausmerkkien sisällä erikoismerkit täytyy kirjoittaa kahdella
  kenoviivalla: `\\n`, `\\t`, `\\v`




echo (kokeillaan)
-----------------------------------

1. Tulosta teksti: *Linux on ykkönen*
2. Tulosta peräkkäisille riveille tekstit *Ubuntu ja Unity* ja *komentorivi ja Bash*
3. Tulosta muuttujan `$PATH` arvo.







Tekstitiedoston tulostus: `cat`
===============================

Tekstitiedoston sisällön voi tulostaa terminaaliin `cat`-ohjelma.

```no-highlight
pesasa$box:~ $ cat /etc/passwd
 ...
pesasa$box:~ $ cat /etc/hosts
 ...
pesasa$box:~ $ cat /etc/lsb-release
 ...
pesasa$box:~ $ cat .bash_history
```

Kokeile!




Tekstitiedoston lukeminen: `less` (ja `more`)
===============================

Tekstitiedostoa voi lukea selattavassa muodossa komennolla `less`.

* `less /etc/passwd` näyttää tiedoston ja sitä voi selata ylös ja alas nuolinäppäimillä
   sekä PageUp- ja PageDown-näppäimillä.
* Selaaminen lopetetaan **q**-näppäimellä.
* Hakutoiminto **/**-näppäimellä.
* `man` käyttää `less`-ohjelmaa ohjesivujen näyttämiseen/sivuttamiseen.
* `less` osaa näyttää myös `gz`-pakatut tekstitiedostot.

Ohjelma nimeltä `more` on `less`-ohjelman edeltäjä. Se osaa vain sivuttaa, mutta
ei rullata taaksepäin.

* "Less is more"




less ja more (kokeillaan)
-----------------------------

Kokeile katsoa sekä lessillä että morella tiedostoja:

* `/usr/share/doc/emacs/copyright`
* `/usr/share/doc/gzip/TODO`
* `/usr/share/doc/bash/FAQ.gz`
* `/var/log/syslog`




Tiedoston koko: `wc`
===============================

Tekstitiedoston koon voi tarkistaa komennolla `wc`. (word count)

* Ohjelma tulostaa rivien, sanojen ja merkkien määrät sekä tiedoston nimen.
* Ohjelmalta saa pyydettyä erikseen tavujen (`-c`), merkkien (`-m`), sanojen (`-w`) tai
  rivien (`-l`) määrän.
* Jos kysytään useamman tiedoston kokoja, ne kerrotaan omilla riveillään sekä lisäksi
  kokonaiskoko.
  
```no-highlight
pesasa@box:~ $ wc /var/log/syslog
555  6339 42655 /var/log/syslog
pesasa@box:~ $ wc -l /var/log/syslog
555  6339 42655 /var/log/syslog
pesasa@box:~ $ wc /var/log/syslog /var/log/dmesg
  555   6339  42655 /var/log/syslog
  944   8554  64176 /var/log/dmesg
 1499  14893 106831 total
pesasa@box:~ $ wc -c /var/log/syslog /var/log/dmesg
42655 /var/log/syslog
64176 /var/log/dmesg
106831 total
```




wc (kokeillaan)
-------------------

* Montako riviä on tiedostossa `/etc/passwd`?
* Entä tiedostossa `/etc/hosts`?
* Vertaa komentojen `ls /usr/share/doc/wget/copyright` ja
  `wc /usr/share/doc/wget/copyright` tulostuksia.
  Mitä yhteistä niillä on? Miksi?




Tiedoston alku ja loppu: `head` ja `tail`
===============================

Tekstitiedoston alusta voidaan tulostaa haluttu määrä rivejä komeenolla `head`.

* `head -n 3 /var/log/syslog` tulostaa tiedoston `/var/log/syslog` kolme ensimmäistä riviä.

Vastaavasti tiedoston lopusta saadaan haluttu määrä rivejä komennolla `tail`.

* `tail -n 3 /var/log/syslog` tulostaa tiedoston `/var/log/syslog` kolme viimeistä riviä.




head ja tail (kokeillaan)
---------------------------

Tulosta `head`- ja `tail`-ohjelmia käyttäen:

* tiedostosta `/etc/passwd` viisi ensimmäistä riviä
* tiedostosta `/usr/share/doc/emacs/copyright` kolme viimeistä riviä.




Tekstin muokkaus: `nano`
===============================

Ohjelma nimeltä `nano` on yksinkertainen tekstieditori. Se on ulkoasultaan
ja käytettävyydeltään varsin yksinkertainen. Sen yleisimmin käytettävien
toimintojen pikanäppäimet on lueteltu näytön alareunassa.

```no-highlight
  GNU nano 2.5.3                   Tiedosto: Kurssi.txt                                 Muokattu  

Hiukan esimerkkitekstiä...
















^G Ohjeita    ^O Kirjoita   ^W Etsi       ^K Leikkaa   ^J Tasaa    ^C Sijainti   ^Y Ed. sivu
^X Lopeta     ^R Lue tied.  ^\ Korvaa     ^U Liitä     ^T Oikolue  ^_ Rivinumero ^V Seur. sivu
```

* Käynnistetään komennolla: `nano` tai `nano tiedostonnimi`.
* `nano`:n toiminnot on lueteltu ruudun alareunassa control-näppäinyhdistelminä.
* **ctrl-x** sulkee nanon ja tarvittaessa kysyy, tallennetaanko.
* **ctrl-o** tallentaa käsitellyn tiedoston.
* **ctrl-r** avaa tiedoston.

Nano on vapaa toteutus aiemmasta ei-vapaalla lisenssillä jaellusta ohjelmasta nimeltä `pico`.





nano (kokeillaan)
------------------------

Harjoittele nanon käyttöä ja kirjoita sillä hakemistossa `Documents` sijaitsevaan
tiedostoon `nano-harjoitus.txt`
seuraava teksti:

```
Aku Ankka
Mikki Hiiri
3 ankanpoikaa
2 litraa mansikoita
purkillinen mustikoita
300 euroa rahaa pankissa
```

Lisää ankanpoikien jälkeen rivi:

```
 3 karhukoplan konnaa
```





Rivien järjestäminen: `sort`
===============================

Halutun tiedoston rivit voidaan tulostaa järjestettyinä komennolla `sort`.

* Oletuksena rivit järjestetään aakkosjärjestykseen.
* Lisävalitsimella `-n` rivit järjestetään numeerisesti aakkosjärjestyksen sijaan.
  (Siis esimerkiksi `7 efg` ennen merkkijonoa `12 abc`)
* Kokeile: `sort /etc/passwd`
* Kokeile, mikä ero on komennoilla: `sort Documents/nano-harjoitus.txt` ja
  `sort -n Documents/nano-harjoitus.txt`
* Selvitä man-sivulta (`man sort`), miten rivit saa järjestettyä käänteisessä
  järjestyksessä.




Tiedostoja verkosta: `wget`
===============================

Komentorivillä tiedostoja voi noutaa verkosta ohjelmalla nimeltä `wget`.

Haetaan kuva osoitteesta <http://petrit.net/Linux-kurssi/penguin2.png>
komennolla:

`wget http://petrit.net/Linux-kurssi/penguin2.png`

```no-highlight
pesasa@box:~ $ wget http://petrit.net/Linux-kurssi/penguin2.png
--2016-09-11 19:31:03--  http://petrit.net/Linux-kurssi/penguin2.png
Selvitetään osoitetta petrit.net (petrit.net)... 85.17.21.177
Yhdistetään palvelimeen petrit.net (petrit.net)|85.17.21.177|:80... yhdistetty.
HTTP-pyyntö lähetetty, odotetaan vastausta... 200 OK
Pituus: 14493 (14K) [image/png]
Tallennetaan kohteeseen ”penguin2.png”

penguin2.png              100%[==================================>]  14,15K  --.-KB/s    in 0,03s   

2016-09-11 19:31:03 (422 KB/s) - ”penguin2.png” tallennettu [14493/14493]
```

Nimen, jolla tiedosto tallennetaan, voi valita valitsimella `-O` (iso O-kirjain).

`wget -O Documents/linux.html http://petrit.net/Linux-kurssi/index.html`

```no-highlight
pesasa@box:~ $ wget -O Documents/linux.html http://petrit.net/Linux-kurssi/index.html
--2016-09-11 19:35:34--  http://petrit.net/Linux-kurssi/index.html
Selvitetään osoitetta petrit.net (petrit.net)... 85.17.21.177
Yhdistetään palvelimeen petrit.net (petrit.net)|85.17.21.177|:80... yhdistetty.
HTTP-pyyntö lähetetty, odotetaan vastausta... 200 OK
Pituus: 1761180 (1,7M) [text/html]
Tallennetaan kohteeseen ”Documents/linux.html”

Documents/linux.html      100%[==================================>]   1,68M  2,89MB/s    in 0,6s    

2016-09-11 19:35:37 (2,89 MB/s) - ”Documents/linux.html” tallennettu [1761180/1761180]

```





Tekstin etsintä tiedostosta: `grep`
===============================

Tekstitiedostosta voi etsiä annettuun hakulausekkeeseen täsmäävää tekstiä sisältävät
rivit komennolla `grep`.

Hakulausekkeena pelkkä sana:
```no-highlight
pesasa@box:~ $ grep free /usr/share/doc/bash/copyright
Bash is free software; you can redistribute it and/or modify it under
```

Valitsin `-i` (ignore) käskee olla erottelematta suuria ja pieniä kirjaimia.
```no-highlight
pesasa@box:~ $ grep -i free /usr/share/doc/bash/copyright
Copyright (C) 1987-2014 Free Software Foundation, Inc.
Bash is free software; you can redistribute it and/or modify it under
the terms of the GNU General Public License as published by the Free
The Free Software Foundation has exempted Bash from the requirement of
 Copyright (c) 1988-2014 Free Software Foundation, Inc.
 ...
```

Valitsin `-v` muuntaa valinnan käänteiseksi. Se etsii kaikki rivit, joilla hakulauseke
__ei__ esiinnyt.
```no-highlight
pesasa@swan:~ $ grep -v ank Documents/nano-harjoitus.txt 
Aku Ankka
Mikki Hiiri
2 litraa mansikoita
purkillinen mustikoita
```

Jos haku sisältää välilyöntejä, kannattaa se laittaa yksinkertaisten lainausmerkkien
`'` sisään.

Hakuja voi tehdä myös monipuolisemmin käyttämällä niin sanottuja säännöllisiä lausekkeita
(regular expressions, regexp). Niistä voit lukea lisää seuraavista osoitteista.

* http://linux.fi/wiki/Säännöllinen_lauseke
* http://cs.stadia.fi/~kuivanen/linux/regexp.php
* Ja vähän tieteellisemmästä kulmasta: http://fi.wikipedia.org/wiki/Säännöllinen_lauseke





Tehtäviä
===============================

Kerro jokaisessa kohdassa vastauksen lisäksi, millä komennolla tai komennoilla
suoritit tehtävän.

1. Kuinka monta riviä on komentohistoriassasi?
2. Mikä on komentorivillä muuttujan `$OSTYPE` arvo?
3. Lataa verkosta tiedosto `http://petrit.net/Linux-kurssi/pg37885.txt`
4. Montako riviä tiedostossa on?
5. Tulosta tiedostosta kuusi ensimmäistä ja neljä viimeistä riviä.
6. Miten kuuluu kokonaisuudessaan rivi, jolla esiintyy teksti: *Kuningas vapisi ilosta*?
7. Järjestä tiedoston rivit aakkosjärjestykseen. Miten kuuluu viimeinen rivi?
