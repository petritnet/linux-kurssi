+++
date = "2016-09-08T21:08:16+03:00"
title = "Komentorivi"
weight = 11
+++


Komentorivi
===============================

Tehokas tapa laittaa kone töihin. Tekstipohjainen käyttöliittymä, eli komentotulkki, eli shell (kuori).

* Yleisimmin käytetty komentotulkki: `bash` (Bourne again shell)
    * Aiemman Bourne shellin (`sh`) jälkeläinen
* Komentotulkin sisäisiä komentoja sekä erillisiä ohjelmia.
    * Näyttävät käyttäjälle samanlaisilta



Muutama pikanäppäin
===============================

ctrl-c
:    Ohjelman suorituksen pysäyttäminen

ctrl-s
:    Tulostuksen keskeyttäminen. Jos näyttää, että komentorivi ei reagoi, olet saattanut vahingossa painaa tätä.

ctrl-q
:    Tulostuksen jatkaminen. Tämä palauttaa tulostuksen ctrl-s:n jälkeen.

ctrl-d
:    Komentotulkin lopettaminen. Sama kuin `exit` tai `logout`
:    Toimii myös syötteen lopetusmerkkinä tietyissä tilanteissa. (Tutustutaan myöhemmin.)

ctrl-a
:    Siirry komentorivin alkuun.

ctrl-e
:    Siirry komentorivin loppuun.




Komentohistoria
===============================

Bash tallentaa kirjoittamasi komennot komentohistoriaan, josta voi hakea niitä uudelleenkäytettäväksi.

* Kirjoita komentoriville `ls` ja paina enter. Kirjoita `pwd` ja paina enter.
* Paina nuoli ylös näppäintä selataksesi vanhoja komentoja.
* Paina nuoli alas näppäinä selataksesi takaisin uudempiin komentoihin päin.
* Komentoa voi muokata
* Enter suorittaa valitun komennon uudelleen.
* `history` -komento luettelee tallessa olevat komennot.
* `!<numero>` suorittaa `history`-komennon antaman listan mukaisen komennon.
* **ctrl-r** aloittaa *reverse-i-search* -toiminnon, jolla voi hakea historiasta kirjoittamalla hakua. Uusi **ctrl-r**
   hakee seuraavan täsmäävän.




Ohjeet
===============================

Ennen kuin aloitetaan komentorivin käyttö, katsotaan, mistä löytyvät ohjeet.

* `man`-komento käynnistää pyydetyn ohjelman ohjeen. Esimerkiksi:
   * `man ls` tai `man man`
* Ohjetta voi selata ylös ja alas nuolinäppäimillä sekä **PageUp**- ja **PageDown**-näppäimillä.
* Man lopetetaan painamalla `q`.

Linuxeissa on myös toinen ohjetoiminto, joka voi olla joidenkin ohjelmien kohdalla kattavampi:

* `info`-komento käynnistää pyydetyn info-sivun.
   * `info info` tai `info nano`
* Sivua voi selata ylös ja alas sekä valita tähdellä merkittyjä "linkkejä" painamalla enteriä.
* Sivulta toiselle myös pikanäppäimillä **n** (next), **p** (previous), **u** (up)
* Jos info-sivua ei ole, näytetään man-sivu.




echo
===============================

`echo` on komento, joka tulostaa annetun tekstin. 

* `echo Moikka, maailma`
* `echo "Heippa vaan"`
* `echo 'Linux on pop'`

Voidaan tulostaa myös muuttujien arvoja:

* `echo $HOME`

```
 /home/pesasa
```

Lisäoptio `-n` jättää pois rivinvaihdon tulostuksen lopusta:

* `echo -n "Ei rivinvaihtoa"`
```
Ei rivinvaihtoapesasa@kurssibuntu:~ $
```

Lisäoptio `-e` mahdollistaa erikoismerkkien käytön:

* `echo -e '1:\tyksi\n2:\tkaksi'`
```
1:    yksi
2:    kaksi
```




echo ja lainausmerkit
------------------------------

`echo`-komennolla ja yleisestikin bashissa suoritettavilla komennoilla ja ohjelmilla on eroa yksinkertaisilla
ja kaksinkertaisilla lainausmerkeillä (`'`) ja (`"`).

* Yksinkertaisilla lainausmerkeillä merkityt merkkijonot käsitellään sellaisinaan.
* Kaksinkertaisilla lainausmerkeillä merkittujen merkkijonojen sisällä olevat muuttujanimet korvataan niiden arvoilla.

```
 echo 'Kotihakemisto: $HOME'
 Kotihakemisto: $HOME
```

mutta

```
 echo "Kotihakemisto: $HOME"
 Kotihakemisto: /home/pesasa
```

* Yksinkertaisten lainausmerkkien sisällä voidaan käyttää esim. erikoismerkkejä: `\n` (rivinvaihto),
  `\t` (vaakasarkain), `\v` (pystysarkain)
* Kaksinkertaisten lainausmerkkien sisällä erikoismerkit täytyy kirjoittaa kahdella kenoviivalla: `\\n`, `\\t`, `\\v`




echo (kokeillaan)
-----------------------------------

* Tulosta teksti: *Linux on ykkönen*
* Tulosta peräkkäisille riveille tekstit *Ubuntu ja Unity* ja *komentorivi ja Bash*
* Tulosta muuttujan `$PATH` arvo.




ls
===============================

`ls` -komento tulostaa pyydetyn hakemiston sisällön. Oletuksena nykyinen työhakemisto.

`ls Documents` 
:    *Documents* -hakemiston sisältö

`ls -l`
:    Työhakemiston sisältö pitkässä tulostusmuodossa. (long)
     (tiedoston tyyppi, oikeudet, kovien linkkien määrä, omistaja, ryhmä, tiedoston koko, muutosaika, nimi)

`ls -a`
:    Työhakemiston sisältö, mukaan lukien pisteellä alkavat **piilotiedostot**.
     (all) (Pisteellä alkavat tiedostot piilotetaan yleensä.)

`ls -lh`
:    Työhakemiston sisältö pitkässä muodossa ja tiedostojen koot "ihmisen luettavassa muodossa".
     (human-readable) Tiedostojen kokoja ei näytetä tavuina vaan kilo-, mega- tai gigatavuina, jos järkevämpää.




ls (kokeillaan)
----------------------------

* Montako piilotiedostoa kotihakemistossasi on? Moniko niistä on hakemisto?
* Mikä on tiedoston `/bin/bash` koko tavuina? Entä ihmisen luettavassa muodossa?
* Mikä on tiedoston `/etc/profile` muutosaika?




pwd ja cd
===============================

* `pwd` tulostaa nykyisen työhakemiston
* `cd` vaihtaa työhakemiston pyydettyyn hakemistoon.
* Hakemisto voidaan antaa antaa `cd`-komennolle:
   * absoluuttisena juuresta alkaen (`/`-merkillä alkaen): `/usr/share`
   * suhteellisena nykyisen työhakemiston suhteen: `Documents`, `../../usr`
* Erikoishakemistonimet: `.` ja `..`:
   * `.` on "tämä hakemisto". Esim. `/home/./pesasa` on sama kuin `/home/pesasa`
   * `..` yksi hakemisto juuren suuntaan. "Isä hakemisto"




pwd ja cd (kokeillaan)
------------------------------

```
 $ pwd
 /home/pesasa
 $ cd /etc/cups
 $ pwd
 /etc/cups
 $ cd ..
 $ pwd
 /etc
 $ cd .
 $ pwd
 /etc
```





mkdir
===============================

`mkdir` luo uuden hakemiston (make directory).

* `mkdir Documents/uusihakemisto`
* `mkdir Documents/toinenhakemisto`




cp ja mv
===============================

`cp` kopioi tiedoston (copy) ja `mv` siirtää sen (move).

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

Jos halutaan kopioida kokonainen hakemisto sen sisältämine tiedostoineen, pitää kopiointi tehdä *rekursiivisesti*.
* `cp -r /usr/share/doc/wget .`
   * "Kopioi hakemisto `/usr/share/doc/wget` sisältöineen työhakemistoon (`.`)"
* `cp -a /usr/share/doc/wget .`
   * Muuten sama, mutta `-a` === "archive", eli pyrkii säilyttämään tiedostojen oikeudet ja omistajuudet samoina.
   (Hyödyllinen lähinnä root-oikeuksilla kopioitaessa.)




rm ja rmdir
===============================

`rm` poistaa tiedoston (remove), `rmdir` poistaa tyhjän hakemiston (remove directory).

* ***Muista olla varovainen!***
* `rm passut.txt`
* `rmdir Documents/toinenhakemisto`
* Hakemiston voi poistaa myös `rm`-komennolla käyttämällä lisävalitsinta `-r` (recoursive).
  Tämä poistaa hakemiston ja kaiken sen sisällön. ***Varo!*** 
* `rm -r Documents/uusihakemisto`




ln
===============================

`ln`-komennolla luodaan tiedostojärjestelmään linkkejä ja symbolisia linkkejä.

* Linkki: Yksi ja sama tiedosto levyllä, mutta voi olla useampi nimi ja eri paikoissa hakemistopuuta.
* Symbolinen linkki: "vain" viittaus johonkin toiseen, "oikeaan" tiedostoon.

```
 $ ls -l /etc/printcap
 lrwxrwxrwx 1 root root 22 Sep 24 21:30 /etc/printcap -> /var/run/cups/printcap
```

* `ln -s /usr/share/doc/emacs/copyright`
   * Luo työhakemistoon symbolisen linkin, jonka nimi on `copyright` ja joka viittaa
     tiedostoon `/usr/share/doc/emacs/copyright`
* `ln -s /usr/share/doc/emacs/copyright Documents/oikeudet`
   * Luo `Documents`-hakemistoon symbolisen linkin, jonka nimi on `oikeudet` ja joka viittaa
     tiedostoon `/usr/share/doc/emacs/copyright`

Symbolista linkkiä voi käyttää useimpiin tarkoituksiin aivan samoin kuin varsinaista tiedostoakin.




cat
===============================

`cat` on ohjelma, jolla tulostetaan (teksti)tiedoston sisältö.

```
 cat /etc/passwd
 ...
 cat /etc/hosts
 ...
 cat /etc/lsb-release
 ...
 cat .bash_history
```

Kokeile!




less (ja more)
===============================

`less` näyttää (teksti)tiedoston selattavassa muodossa.

* `less /etc/passwd` näyttää tiedoston ja sitä voi selata ylös ja alas nuolinäppäimillä
   sekä PageUp- ja PageDown-näppäimillä.
* Selaaminen lopetetaan **q**-näppäimellä.
* Hakutoiminto **/**-näppäimellä.
* `man` käyttää `less`-ohjelmaa ohjesivujen näyttämiseen/sivuttamiseen.
* `less` osaa näyttää myös `gz`-pakatut tekstitiedostot.

`more` on `less`-ohjelman edeltäjä. Vain sivuttaa, ei osaa rullata eteen ja taakse.

* "Less is more"




less ja more (kokeillaan)
-----------------------------

Kokeile katsoa sekä lessillä että morella tiedostoja:

* `/usr/share/doc/emacs/copyright`
* `/usr/share/doc/gzip/TODO`
* `/usr/share/doc/bash/FAQ.gz`
* `/var/log/syslog`




wc
===============================

`wc` kertoo tiedoston koon. (word count)

* Tulostaa rivien, sanojen ja merkkien määrät sekä tiedoston nimen.
* Ohjelmalta saa pyydettyä erikseen tavujen (`-c`), merkkien (`-m`), sanojen (`-w`) tai rivien (`-l`) määrän.
* Jos kysytään useamman tiedoston kokoja, ne kerrotaan omilla riveillään sekä lisäksi kokonaiskoko.

```
 $ wc /var/log/syslog
 555  6339 42655 /var/log/syslog
 $ wc -l /var/log/syslog
 555  6339 42655 /var/log/syslog
 $ wc /var/log/syslog /var/log/dmesg
   555   6339  42655 /var/log/syslog
   944   8554  64176 /var/log/dmesg
  1499  14893 106831 total
 $ wc -c /var/log/syslog /var/log/dmesg
 42655 /var/log/syslog
 64176 /var/log/dmesg
106831 total
```




wc (kokeillaan)
-------------------

* Montako riviä on tiedostossa `/etc/passwd`?
* Entä tiedostossa `/etc/hosts`?
* Vertaa komentojen `ls /usr/share/doc/wget/copyright` ja `wc /usr/share/doc/wget/copyright` tulostuksia.
  Mitä yhteistä niillä on? Miksi?




head ja tail
===============================

`head` tulostaa pyydetyn tekstitiedoston alusta pyydetyn määrän rivejä.

* `head -n 3 /var/log/syslog` tulostaa tiedoston `/var/log/syslog` kolme ensimmäistä riviä.

`tail` ohjelma näyttää tekstitiedostosta lopusta vain pyydetyn määrän rivejä.

* `tail -n 3 /var/log/syslog` tulostaa tiedoston `/var/log/syslog` kolme viimeistä riviä.




head ja tail (kokeillaan)
---------------------------

Tulosta `head`- ja `tail`-ohjelmia käyttäen:

* tiedostosta `/etc/passwd` viisi ensimmäistä riviä
* tiedostosta `/usr/share/doc/emacs/copyright` kolme viimeistä riviä.




nano
===============================

`nano` on yksinkertainen tekstieditori.

* Käynnistetään komennolla: `nano` tai `nano tiedostonnimi`.
* `nano`n toiminnot on lueteltu ruudun alareunassa control-näppäinyhdistelminä.
* **ctrl-x** sulkee nanon ja tarvittaessa kysyy, tallennetaanko.
* **ctrl-o** tallentaa käsitellyn tiedoston.
* **ctrl-r** avaa tiedoston.

Nano on vapaa toteutus aiemmasta ei-vapaalla lisenssillä jaellusta ohjelmasta `pico`.





nano (kokeillaan)
------------------------

Harjoittele nanon käyttöä ja kirjoita sillä hakemistossa `Documents` sijaitsevaan tiedostoon `nano-harjoitus.txt`
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





sort
===============================

`sort` tulostaa pyydetyn tiedoston rivit järjestettynä.

* Oletuksena järjestää aakkosjärjestykseen.
* Lisävalitsimella `-n` järjestää rivit numeerisesti aakkosjärjestyksen sijaan.
  (Siis `7 efg` ennen merkkijonoa `12 abc`)
* `sort /etc/passwd`
* Kokeile, mikä ero on komennoilla: `sort Documents/nano-harjoitus.txt` ja `sort -n Documents/nano-harjoitus.txt`
* Selvitä man-sivulta (`man sort`), miten rivit saa järjestettyä käänteisessä järjestyksessä.




wget
===============================

`wget`-ohjelmalla voi noutaa verkosta tiedoston komentorivillä.

* `wget http://petrit.net/Linux-kurssi/images/penguin2.png`

Nimen, jolla tiedosto tallennetaan, voi valita valitsimella `-O` (iso O-kirjain).

* `wget -O Ubuntu-logo.svg http://upload.wikimedia.org/wikipedia/commons/3/3a/Logo-ubuntu_no%28r%29-black_orange-hex.svg`
* `wget -O Documents/linux.html http://petrit.net/Linux-kurssi/index.html`





grep
===============================

`grep` ohjelma etsii annetusta tekstitiedostosta kaikki rivit, joilla pyydetty hakulauseke esiintyy.

* `grep free /usr/share/doc/bash/copyright`
* `grep -i free /usr/share/doc/bash/copyright` (ei erottele suuria ja pieniä kirjaimia)
* `grep -v ank Documents/nano-harjoitus.txt` (tulostaa kaikki rivit, joilla __ei__ esiinny merkkijonoa `ank`.
* Jos haku sisältää välilyöntejä, kannattaa se laittaa yksinkertaisten lainausmerkkien (`'`) sisään.
* Hakuja voi tehdä myös monipuolisemmin käyttämällä niin sanottuja säännöllisiä lausekkeita
  (regular expressions, regexp). Niistä voit lukea lisää seuraavista:
   * http://linux.fi/wiki/Säännöllinen_lauseke
   * http://cs.stadia.fi/~kuivanen/linux/regexp.php
   * Ja vähän tieteellisemmästä kulmasta: http://fi.wikipedia.org/wiki/Säännöllinen_lauseke





Tehtäviä
===============================

Palautus tiedostona `vastaus-9.odt` Moodleen.
Kerro jokaisessa kohdassa vastauksen lisäksi, millä komennolla tai komennoilla suoritit tehtävän.

1. Kuinka monta riviä on komentohistoriassasi?
2. Mikä on komentorivillä muuttujan `$OSTYPE` arvo?
3. Lataa verkosta tiedosto `http://petrit.net/Linux-kurssi/pg37885.txt`
4. Montako riviä tiedostossa on?
5. Tulosta tiedostosta kuusi ensimmäistä ja neljä viimeistä riviä.
6. Miten kuuluu kokonaisuudessaan rivi, jolla esiintyy teksti: *Kuningas vapisi ilosta*?
7. Järjestä tiedoston rivit aakkosjärjestykseen. Miten kuuluu viimeinen rivi?
