+++
date = "2017-03-05T16:32:00+03:00"
title = "Tekstien käsittely komentorivillä"
weight = 420
+++

Tekstitiedostojen tarkasteluun ja muokkaamiseen löytyy useita komentoja ja ohjelmia.
Tutustutaan tyypillisimpiin.



Tekstin tulostus `echo`
===============================

Komento `echo` tulostaa terminaaliin annetun tekstin.

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

Oletuksena `echo` tulostaa käsketyn tekstin jälkeen lisäksi rivinvaihdon.
Lisäoptio `-n` jättää tämän rivinvaihdoin pois:

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

Tässä esimerkissä käytetyt erikoismerkit ovat: `\t` = tabulaattorimerkki, `\n` = rivinvaihto.



echo ja lainausmerkit
------------------------------

`echo`-komennolla ja yleisestikin bashissa suoritettavissa komennoissa ja ohjelmissa on eroa yksinkertaisilla
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




{{% wrapper class="exercises" %}}
echo (kokeillaan)
-----------------------------------

1. Tulosta teksti: *Linux on ykkönen*
2. Tulosta peräkkäisille riveille tekstit *Ubuntu ja Unity* ja *komentorivi ja Bash*
3. Tulosta muuttujan `$PATH` arvo.

{{% /wrapper %}}





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

> "Less is more"

Lisäksi erikseen asennettavana on kolmas ja vielä `less`-ohjelmaakin monipuolisempi ohjelma
`most`.




{{% wrapper class="exercises" %}}
less ja more (kokeillaan)
-----------------------------

Kokeile katsoa sekä lessillä että morella tiedostoja:

* `/usr/share/doc/emacs/copyright`
* `/usr/share/doc/gzip/TODO`
* `/usr/share/doc/bash/FAQ.gz`
* `/var/log/syslog`


{{% /wrapper %}}

Tiedoston alku ja loppu: `head` ja `tail`
===============================

Tekstitiedoston alusta voidaan tulostaa haluttu määrä rivejä komeenolla `head`.

* `head -n 3 /var/log/syslog` tulostaa tiedoston `/var/log/syslog` kolme ensimmäistä riviä.

Vastaavasti tiedoston lopusta saadaan haluttu määrä rivejä komennolla `tail`.

* `tail -n 3 /var/log/syslog` tulostaa tiedoston `/var/log/syslog` kolme viimeistä riviä.




{{% wrapper class="exercises" %}}
head ja tail (kokeillaan)
---------------------------

Tulosta `head`- ja `tail`-ohjelmia käyttäen:

* tiedostosta `/etc/passwd` viisi ensimmäistä riviä
* tiedostosta `/usr/share/doc/emacs/copyright` kolme viimeistä riviä.

{{% /wrapper %}}


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

Muita tekstipohjaisia tekstieditoreita ovat muun muassa: `vi`, `emacs` ja `jed`.




{{% wrapper class="exercises" %}}
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

{{% /wrapper %}}







Tekstitiedoston koko: `wc`
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




{{% wrapper class="exercises" %}}
wc (kokeillaan)
-------------------

* Montako riviä on tiedostossa `/etc/passwd`?
* Entä tiedostossa `/etc/hosts`?
* Vertaa komentojen `ls /usr/share/doc/wget/copyright` ja
  `wc /usr/share/doc/wget/copyright` tulostuksia.
  Mitä yhteistä niillä on? Miksi?

{{% /wrapper %}}







Rivien järjestäminen: `sort`
===============================

Halutun tiedoston rivit voidaan tulostaa järjestettyinä komennolla `sort`.

* Oletuksena rivit järjestetään aakkosjärjestykseen.
* Lisävalitsimella `-n` rivit järjestetään numeerisesti aakkosjärjestyksen sijaan.
  (Siis esimerkiksi `7 efg` ennen merkkijonoa `12 abc`)

Järjestetään `AUTHORS`-tiedoston nimet aakkosjärjestykseen:
```no-highlight
pesasa@box:~ $ sort /usr/share/doc/eog/AUTHORS
Arik Devens <arik@gnome.org>
Claudio Saavedra <csaavedra@igalia.com>
Federico Mena Quintero <federico@gnome.org>
Felix Riemann <friemann@svn.gnome.org>
Jens Finke <jens@triq.net)
Lucas Rocha <lucasr@gnome.org>
Martin Baulig <baulig@suse.de>
Michael Meeks <michael@ximian.com>
Paolo Borelli <pborelli@katamail.com>
Philip Van Hoof <pvanhoof@gnome.org>
Tim Gerla <tim+gnomebugs@gerla.net>
```

Järjestetään saman tiedoston rivit käänteiseen aakkosjärjestykseen:
```no-highlight
pesasa@box:~ $ sort -r /usr/share/doc/eog/AUTHORS
Tim Gerla <tim+gnomebugs@gerla.net>
Philip Van Hoof <pvanhoof@gnome.org>
Paolo Borelli <pborelli@katamail.com>
Michael Meeks <michael@ximian.com>
Martin Baulig <baulig@suse.de>
Lucas Rocha <lucasr@gnome.org>
Jens Finke <jens@triq.net)
Felix Riemann <friemann@svn.gnome.org>
Federico Mena Quintero <federico@gnome.org>
Claudio Saavedra <csaavedra@igalia.com>
Arik Devens <arik@gnome.org>
```

{{% wrapper class="exercises" %}}
sort (kokeillaan)
-------------------

* Kokeile:<br> `sort /etc/passwd`
* Kokeile, mikä ero on komennoilla:<br> `sort Documents/nano-harjoitus.txt` ja <br>
  `sort -n Documents/nano-harjoitus.txt`
* Selvitä man-sivulta (`man sort`), miten rivit saa järjestettyä käänteisessä
  järjestyksessä.

{{% /wrapper %}}



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
==============================

{{% wrapper class="exercises" %}}
Tehtävät 9
===============================

Kerro jokaisessa kohdassa vastauksen lisäksi, millä komennolla tai komennoilla
suoritit tehtävän. Vastausten palautus tiedostona `tehtava-9.txt`.

1. Kuinka monta riviä on komentohistoriassasi?
2. Mikä on komentorivillä muuttujan `$OSTYPE` arvo?
3. Lataa verkosta tiedosto `http://petrit.net/Linux-kurssi/files/pg37885.txt`
4. Montako riviä tiedostossa on?
5. Tulosta tiedostosta kuusi ensimmäistä ja neljä viimeistä riviä.
6. Miten kuuluu kokonaisuudessaan rivi, jolla esiintyy teksti: *Kuningas vapisi ilosta*?
7. Järjestä tiedoston rivit aakkosjärjestykseen. Miten kuuluu viimeinen rivi?

{{% /wrapper %}}