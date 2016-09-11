+++
date = "2016-09-11T17:24:38+03:00"
title = "Komentorivi"
weight = 11
type = "index"
menu = ["main"]
+++

Komentorivi on tehokas tapa laittaa kone töihin tekemään automaattisesti
rutiininomaisia tehtäviä. Komentoriviksi sanotaan tekstipohjaista käyttöliittymä,
eli komentotulkkia. Siitä käytetään myös nimitystä *shell* (kuori).

* Linux- ja Unix-ympäristöissä yleisimmin käytetty komentotulkki on
  `bash` (Bourne again shell)
    * Aiemman Bourne shellin (`sh`) jälkeläinen
* Komentotulkissa on käytettävissä sen sisäisiä komentoja sekä erillisiä ohjelmia.
    * Näyttävät käyttäjälle samanlaisilta

Linuxissa komentorivin voi saada eteensä useammalla tavalla. Helpoimmin sen saa
käyttöönsä avaamalla (valikosta) jonkin tarjolla olevista terminaaliohjelmista.
Terminaali aukeaa tyypillisesti omaan ikkunaansa.

Komentorivin saa käyttöönsä myös, jos tietokonetta käyttää tekstitilassa ilman
graafista ikkunointia tai jos siihen ottaa komentorivietäyhteyden (ssh) joltain
toiselta koneelta esimerkiksi Putty-ohjelmalla.

Esimerkiksi terminaaliohjelmassa on käynnissä Bash-ohjelma, joka oletuksena näyttää
käyttäjälle suurin piirtein tältä:

```bash
pesasa@box:~ $ _
```

Tätä sanotaan *komentorivikehotteeksi* (prompt) ja se tarkoittaa sitä, että Bash kehottaa
käyttäjää antamaan jonkin komennon. Kehotteen sisältämä tekstisisältö on käyttäjän
muokattavissa, mutta oletuksena se näyttää useimmiten yllä olevan kaltaiselta.
Yllä oleva kehote koostuu seuraavista osista:

* `pesasa` on käyttäjän oma käyttäjätunnus
* `box` on kyseisen tietokoneen nimi
* Kaksoispisteen jälkeen tulee tällä hetkellä käytössä oleva työhakemisto,
  joka tässä esimerkissä on käyttäjän omaa kotihakemistoa symbolisoiva `~`.
* Lopuksi kehotteessa on `$`-symboli, joka tarkoittaa, että käyttäjällä
  ovat tavallisen käyttäjän oikeudet. Jos kyseessä olisi `root`-käyttäjä, olisi tämän
  tilalla `#`-symboli.

Komennot syötetään komentoriville kirjoittamalla ja ne suoritetaan painamalla
**enter**-näppäintä. Sillä ei ole väliä, missä kohtaa tekstikursori on enteriä
painettaessa.

Muutama pikanäppäin
===============================

Ennen komentorivikomentojen antamista on hyvä tutustua muutamaan pikanäppäimeen,
jotka helpottavat sen käyttöä. Erityisesti on hyvä tietää, miten käynnisstetyt
ohjelmat saa pysäytettyä.

ctrl-c
:    Ohjelman suorituksen pysäyttäminen

ctrl-s
:    Tulostuksen keskeyttäminen. Jos näyttää, että komentorivi ei reagoi,
     olet saattanut vahingossa painaa tätä.
     ([Miksi?](http://unix.stackexchange.com/questions/137842/what-is-the-point-of-ctrl-s))

ctrl-q
:    Tulostuksen jatkaminen. Tämä palauttaa tulostuksen **ctrl-s**:n jälkeen.

ctrl-d
:    Komentotulkin lopettaminen. Sama kuin `exit` tai `logout`
:    Toimii myös syötteen lopetusmerkkinä tietyissä tilanteissa. (Tutustutaan myöhemmin.)

ctrl-a
:    Siirry komentorivin alkuun.

ctrl-e
:    Siirry komentorivin loppuun.

Komentorivillä voi siirtyä eteen ja taakse nuolinäppäimillä.



Komentohistoria
===============================

Bash tallentaa kirjoittamasi komennot komentohistoriaan, josta niitä voi hakea
uudelleenkäytettäväksi.

Kokeile:

1. Kirjoita komentoriville `ls` ja paina enter. Kirjoita `pwd` ja paina enter.
2. Paina nuoli ylös näppäintä selataksesi vanhoja komentoja.
3. Paina nuoli alas näppäinä selataksesi takaisin uudempiin komentoihin päin.
4. Komentoa voi muokata
5. Enter suorittaa valitun komennon uudelleen.
6. `history` -komento luettelee tallessa olevat komennot.
7. `!<numero>` suorittaa `history`-komennon antaman listan mukaisen komennon.
8. **ctrl-r** aloittaa *reverse-i-search* -toiminnon, jolla voi hakea historiasta
   kirjoittamalla hakua. Uusi **ctrl-r** hakee seuraavan täsmäävän.

Osa `history`-komennon tulostetta:

```no-highlight
 1435  man ls
 1436  info nano
 1437  echo Moikka, maailma
 1438  echo "Heippa vaan"
 1439  echo 'Linux on pop'
 1440  echo $HOME
 1441  history
 1442  ls
 1443  history
 1444  echo Moikka, maailma
 1445  history
```



Ohjeet
===============================

Ennen kuin aloitetaan komentorivin käyttö, katsotaan vielä, mistä löytyvät ohjeet.

`man`-komento käynnistää pyydetyn ohjelman ohjeen. Esimerkiksi: `man ls` tai `man man`.
Tukoksena on seuraavan kaltainen näkymä, joka kertoo komennon nimen, missä muodossa
komento ja sen tarvitsemat lisäparametrit annetaan sekä kuvauksen, miten
komento ja sen parametrit toimivat.

```no-highlight
LS(1)                              User Commands                             LS(1)

NAME
       ls - list directory contents

SYNOPSIS
       ls [OPTION]... [FILE]...

DESCRIPTION
       List  information about the FILEs (the current directory by default).  Sort
       entries alphabetically if none of -cftuvSUX nor --sort is specified.

       Mandatory arguments to long options are mandatory for short options too.

       -a, --all
              do not ignore entries starting with .

       -A, --almost-all
              do not list implied . and ..

       --author
              with -l, print the author of each file

       -b, --escape
              print C-style escapes for nongraphic characters

 Manual page ls(1) line 1 (press h for help or q to quit)
```


Ohjetta voi selata ylös ja alas nuolinäppäimillä sekä
**PageUp**- ja **PageDown**-näppäimillä. Man lopetetaan painamalla `q`.

Linuxeissa on myös toinen ohjetoiminto, joka voi olla joidenkin ohjelmien kohdalla
kattavampi. `info`-komento käynnistää pyydetyn info-sivun.
Esimerkiksi: `info info` tai `info nano`. Komennon tuloste näyttää tältä:

```no-highlight
Next: Introduction,  Up: (dir)

nano
****

This manual documents GNU 'nano', a small and friendly text editor.

* Menu:

* Introduction::
* Invoking::
* Command-line Options::
* Editor Basics::
* Built-in Help::
* Feature Toggles::
* Nanorc Files::
* The File Browser::
* Pico Compatibility::
* Building and Configure Options::






-----Info: (nano.info.gz)Top, 20 lines --All-----------------------------------------
```

Info-sivua voi selata ylös ja alas sekä valita tähdellä merkittyjä "linkkejä" painamalla
enteriä. Sivulta toiselle pääsee liikkumaan myös pikanäppäimillä **n** (next, seuraava),
**p** (previous, edellinen), **u** (up, ylempi taso). Jos info-sivua ei ole,
Info näyttää pyydetyn komennon man-sivun.



