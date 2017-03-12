+++
date = "2016-09-11T20:16:20+03:00"
title = "Bash-harjoituksia"
weight = 450
+++

[Harjoitusten esimerkkiratkaisut](/files/harjoitukset.tar.gz)


Asetustiedostoja
======================

Bash suorittaa muutaman tiedoston käynnistyessään. Näissä määritellään muutamia
asetuksia. Näistä voi olla `/etc/`-hakemistossa versio, joka suoritetaan kaikille
käyttäjille ja käyttäjän kotihakemistossa versio, jota käyttäjä voi itse muokata.
Kotihakemistossa olevien asetustiedostojen nimet alkavat yleensä pisteellä, jolloin ne
ovat *piilotiedostoja*. Ne eivät siis näy oletuksena `ls`-komennolla tai
graafisessa tiedostonhallinnassa.

`.bash_profile`
:   Suoritetaan, jos Bash on *login-shell*. Kaikille suoritettava versio:
    `/etc/profile` sekä hakemiston `/etc/profile.d/`-sisältö.

`.bashrc`
:   Suoritetaan Bashin käynnistyessä. Kaikille suoritettava versio: `/etc/bash.bashrc`

`.bash_aliases`
:   Tiedosto, johon käyttäjä voi lisätä omia aliaksia.

`.bash_logout`
:   Tiedosto, jonka sisältö suoritetaan, kun *login-shell* lopetetaan.





Asetuksia ympäristömuuttujissa
======================

Tiedostossa `.bashrc` asetetaan muun muassa muutamia ympäristömuuttujia, joilla
vaikutetaan Bashin toimintaan.

`$PATH`
:   Muuttuja, jonka sisältö on luettelo hakemistopolkuja eroteltuna kaksoispisteillä (:).
    Kun ohjelmaa yritetään käynnistää (ilman polkua), sitä yritetään etsiä näistä
    hakemistoista tässä järjestyksessä.

`$HISTSIZE`
:   Komentohistorian koko. Ubuntussa oletuksena 1000

`$PS1`
:   Komentokehotteeseen tulostuva teksti. Voi sisältää erilaisia erikoismerkkejä
    päivämäärää, kellonaikaa, nykyistä hakemistoa yms. varten.




`$PATH`-muuttuja
======================

Tee kotihakemistoon hakemisto `bin`

```
cd ~
mkdir bin
```

Lisää tämä hakemisto `$PATH`-muuttujaan. Avaa editoriin tiedosto `.bashrc`, ja lisää
loppuun rivi:

```
PATH=$PATH:~/bin
```

Avaa uusi terminaali ja tarkista `$PATH`-muuttujan arvo:

```
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/pesasa/bin
```

Nyt voit tehdä omia skriptejä tähän hakemistoon ja ne voi käynnistää suoraan nimellä
ilman polkua.


Harjoituksia
=============

{{% wrapper class="exercises" %}}
Harjoitustehtävät
---------------

Tee kolme kappaletta harjoitustehtävistä 1-6 joko yksin taikka kahden tai kolmen ryhmissä.
Toteuta tehtävät joko Bash-skripteinä tai aliaksina.

<!--1. Skripti, joka hakee sivulta http://www.hs.fi päivän nimipäiväsankarien nimet ja
   tulostaa ne. -->
<!--3. Hae Turun tämänhetkinen sää Yahoon palvelusta osoitteesta
   <http://weather.yahooapis.com/forecastrss?w=574224&u=c> ja tulosta se. -->
1. Skripti, joka tulostaa viisi satunnaista lottoriviä. Tulosta rivien numerot
   suuruusjärjestyksessä.
2. Asenna paketit `fortune-mod`, `fortunes` sekä `cowsay`. Tee asetuksiisi
   sellainen muutos, että aina uuden terminaalin avatessa tulostetaan
   `fortune`-ohjelman tuottama teksti `cowsay`-ohjelman tekemässä puhekuplassa.
3. Tee skripti, joka simuloi kahta nopanheittoa, eli tulostaa kaksi lukua väliltä 1-6,
   sekä kysyy käyttäjältä niiden summan ja tarkistaa vastauksen.
4. Kalenteri / TODO-lista
   * Tee skripti `todo`, joka etsii kotihakemistossa olevasta tiedostosta `.todolist`
     muotoa `2012-11-01: Linux-kurssi` olevista riveistä ne, jotka koskevat senhetkistä
     päivää ja tulostaa ne ilman päivämäärää, kaksoispistettä ja välilyöntiä. Lisää tämä
     skripti terminaalin käynnistykseen.
   * Tee skripti `todoadd`, joka lisää kotihakemistossa olevaan tiedostoon `.todolist`
     uuden rivin, joka alkaa nykyisellä päivämäärällä (muodossa 2012-11-01),
     kaksoispisteellä ja välilyönnillä ja jatkuu komentorivillä annetulla tekstillä.
     Toteuta tämä vielä niin, että tiedoston rivit ovat päivämäärän mukaan järjestyksessä.
   * _*_ Tee skripti `todoweek`, joka toimii muuten, kuten `todo`, mutta tulostaa
     seuraavan seitsemän päivän ajalta kaikki TODO-merkinnät sekä päivämäärät
     väliotsikkoina.
5. Skripti, joka arpoo kolme kertaa sadan kolikonheiton sarjan ja tulostaa kunkin sarjan tuloksen. Esimerkiksi:<br>
   `45 klaava`<br>
   `55 kruuna`
6. ...

{{% /wrapper %}}



Vihjeitä
======================

* `tr`-ohjelma korvaa käsketyt merkit toisilla. Esim. `echo 'Moi vaan'| tr 'Moa' 'Hee'`
  tulostaa `Hei veen`.
* `tr`-ohjelmalla voi poistaa pyydetyt merkit. Esim. `echo "Hihhei" | tr -d 'h'`
  tulostaa `Hiei`.
* `sort -R` järjestää syötteen rivit satunnaisesti.
* Muuttuja `$RANDOM` palauttaa satunnaisen kokonaisluvun väliltä 0-32767.
* `cal`-ohjelma tulostaa kalenterin tekstimuodossa. Kokeile `cal`, `cal 2014` ja
  `LC_TIME=fi_FI.UTF-8 cal`




Vihjeitä: tekstirivin poiminta
======================

Monirivisestä tekstistä voi poimia rivin, jolla etsitty hakutermi esiintyy,
ohjelmalla `grep`.

Esimerkiksi:
```
grep nobody /etc/passwd
cat /etc/passwd | grep nobody
```

Tulosteeseen voi pyytää *n* riviä löydetyn rivin edeltä "vivulla" `-B n` (B=before)
ja *m* riviä löydetyn rivin jälkeen "vivulla" `-A m` (A=after).

Esim:
```
 grep -B 1 -A 3 nobody /etc/passwd
```

Haun voi rajoittaa rivin alkuun lisäämällä `^`-merkin hakusanan eteen ja rivin
loppuun lisäämällä `$`-merkin hakusanan perään.

Esim:
```
grep ^no /etc/passwd
grep false$ /etc/passwd
```




Vihjeitä muuttujista
======================

Muuttujassa `$oma` olevaa tekstiä voidaan muuttaa esim. seuraavilla tavoilla:

* `${oma/kaava/teksti}` palauttaa muuttujan `$oma` sisällön niin, että ensimmäinen
  mahdollisimman pitkä tekstin `kaava` kuvaama merkkijono on korvattu merkkijonolla
  ´teksti`. Kaavassa voi käyttää jokerimerkkejä, kuten tiedostonimen täydennyksessä.
* `${oma//kaava/teksti}` toimii samoin, mutta korvaa kaikki löydetyt kaavaan sopivat
  tekstit, ei vain ensimmäistä.
* `${oma#kaava}` palauttaa muuttujan `$oma` sisällön niin, että sen alusta on poistettu
  lyhin kaavaan sopiva merkkijono.
* `${oma##kaava}` palauttaa muuttujan `$oma` sisällön niin, että sen alusta on poistettu
  pisin kaavaan sopiva merkkijono.
* `${oma%kaava}` palauttaa muuttujan `$oma` sisällön niin, että sen lopusta on poistettu
  lyhin kaavaan sopiva merkkijono.
* `${oma%%kaava}` palauttaa muuttujan `$oma` sisällön niin, että sen lopusta on poistettu
  pisin kaavaan sopiva merkkijono.
* `${oma:n}` palauttaa muuttujan `$oma` sisällön *n*:nnestä merkistä alkaen.
  (Numerointi alkaa 0:sta!)
* `${oma:n:k}` palauttaa muuttujan `$oma` sisällöstä *k* merkkiä *n*:nnestä merkistä
  alkaen. (Numerointi alkaa 0:sta!)





Vihjeitä laskentaan
======================

* `$((lauseke))` palauttaa matemaattisen lausekkeen arvon. Käsittelee kokonaislukuina ja
   esimerkiksi jakolaskujen tuloksista katkaistaan desimaaliosa pois. Esim.
```
echo $((5/2))
2
echo $((4+6/2))
7
```




Vihjeitä: päivämäärä
======================

`date`-ohjelmalta voi pyytää päivämäärän halutussa muodossa. Esimerkiksi:
```
date +%Y-%m-%d
2014-03-12
```

Tulostusmallissa: %Y = vuosi, %m = kuukausi, %d = päivä
Lisää ohjeita: `man date`

Date:lta voi pyytää myös muun ajan kuin nykyisen. Esim:
```
date --date="tomorrow"
date --date="3 days"
date --date="5hours"
date --date="6hours 30 minutes"
```





Vihjeitä: komentoriviparametrit
======================

* Komentorivillä skriptille annetut parametrit ovat käytettävissä muuttujina
  `$1`, `$2`,...
* Itse ohjelman / skriptin nimi on `$0`
* Kaikki parametrit yhdessä on `$@`




Vihjeitä: `echo` ja escape-merkit
======================

`echo`-komennolla tulostettaviin merkkijonoihin voi lisätä *escape-merkkejä*,
joilla voi muotoilla tulostusta. Komennolle on annettava lisämääre ´-e´,
jotta se osaa näyttää nämä muotoilut.

* `\n`: rivinvaihto (ja paluu rivin alkuun).
* `\r`: paluu rivin alkuun (vaihtamatta uudelle riville)
* `\t`: sarkain (eli tabulaattori)
* `\v`: pystytabulointi, eli siirtyminen seuraavalle riville menemättä rivin alkuun
* `\b`: backspace, eli siirtyminen yhden merkin vasemmalle (ei pyyhi)

```
echo -e "Moi\thei\vkukkuu\ralussa\ntokstiä\b\b\b\b\b\be"
Moi     hei
alussa     kukkuu
tekstiä
```





Vihjeitä: `echo` ja värejä
======================

`echo`-komennolla voi käyttää myös väreä sopivilla escape-komennoilla.
Tulostukseen voi lisätä tulostuksen väriä vaihtavia komentoja laittamalla värikoodi
tekstin `\033[` perään. Värin käyttö lopetetaan vaihtamalla takaisin oletusväreiksi
merkinnällä: `\033[0m` Esimerkiksi:

```
echo -e "\033[1;31mKukkuu\033[0m kaikille \033[0;32mteille\033[0m"
```

<!-- @@color(red):Kukkuu@@ kaikille @@color(green):teille@@ -->

Käytettävissä olevat värit:
```
 Black       0;30     Dark Gray     1;30
 Blue        0;34     Light Blue    1;34
 Green       0;32     Light Green   1;32
 Cyan        0;36     Light Cyan    1;36
 Red         0;31     Light Red     1;31
 Purple      0;35     Light Purple  1;35
 Brown       0;33     Yellow        1;33
 Light Gray  0;37     White         1;37
```





Tehtäviä
======================

{{% wrapper class="exercises" %}}
Tehtävät 13
======================

Tee edellä luetelluista harjoitustehtävistä ainakin kolme.

Tehtävät voi tehdä yksin taikka kahden tai kolmen opiskelijan ryhmissä.

{{% /wrapper %}}

Linkkejä:

* [Hyödyllisiä Bash-komentoja](http://greeennotebook.com/2010/06/useful-bash-commands/)
* [Bash-ohjelmointi](http://koti.welho.com/jkajaste/bash.html)
* <http://linux.fi/wiki/Bash-skriptaus>
* <http://www.turuxi.org/Tapaaminen_13.01.2011>
* [Linux-pikaopas](http://www.jellona.net/linux/linuxohje.htm)
* [Kattavampi, mutta vaativampi HOWTO](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)