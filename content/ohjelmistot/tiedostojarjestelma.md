+++
date = "2016-09-05T23:03:48+03:00"
title = "Tiedostojärjestelmä"
weight = 320
+++

Tiedostojärjestelmä
========================

Järjestelmässä ovat tietyt vakiohakemistot:

```
/
/bin
/boot
/cdrom
/dev
/etc
/home
/lib
/lost+found
/media
/mnt
/opt
/proc
/root
/run
/sbin
/sys
/tmp
/usr
/var
```


Hakemistot
========================

`/`
:   Juurihakemisto. Hakemistopuun juuri. Kaikki tiedostot ja levyt ovat samassa puussa.

`bin`
:   Järjestelmän oleellisimmat ajettavat tiedostot. Varmasti käytettävissä.

`/boot`
:   Käynnistykseen tarvittavia tiedostoja

`/cdrom`
:   Paikka johon optinen levy liitetään.

`/dev`
:   Kaikki laitteet ovat tässä hakemistossa edustettuina tiedostoina. Eivät oikeasti levyllä. Esim. /dev/sda on kiintolevy ja /dev/sda1 sen ensimmäinen osio.

`/etc`
:   Ohjelmien järjestelmänlaajuiset asetukset.

`/home`
:   Käyttäjien kotihakemistot. Esimerkiksi: ///home/pesasa//, ///home/matti//

`/lib`
:   Oleellisimpia ohjelmakirjastoja, joita ohjelmat hyödyntävät. Varmasti käytettävissä.

`/lost+found`
:   Levyntarkistuksessa löydetyt vaurioituneet tiedostot, joiden oikeaa paikkaa ei tiedetä.

`/media`
:   Hakemisto, jonka alle siirrettävät levyt, esim. muistitikut liitetään.

`/mnt`
:   Satunnaisia hakemistopuuhun liitettäviä tiedostojärjestelmiä varten.

`/opt`
:   Paketinhallinnan ulkopuolelta asennettuja ohjelmia.

`/proc`
:   Virtuaalisia tiedostoja, jotka edustavat käynnissä olevaa järjestelmää. Esim. /proc/cpuinfo sisältää tietoa prosessorista.

`/root`
:   root-käyttäjän kotihakemisto

`/run`
:   Käynnissä olevien ohjelmien ja palveluiden tietoja. Esim. palvelinprosessien prosessi-id:itä.

`/sbin`
:   Järjestelmän oleellisimmat ajettavat järjestelmätiedostot. Varmasti käytettävissä.

`/sys`
:   Virtuaalisia tiedostoja liittyen järjestelmään.

`/tmp`
:   Tilapäistiedostoille

`/usr`
:   Ohjelmat asentuvan tämän hakemiston alle.
    * `/usr/bin/` - ajettavat tiedostot
    * `/usr/sbin/` - ajettavat järjestelmän ylläpidon tiedostot
    * `/usr/lib/` - kirjastoja
    * `/usr/local/` - paketinhallinnan ulkopuolelta asennettuja ohjelmia
    * `/usr/share/` - mm. ohjelmien tiedostot omissa hakemistoissaan
    * `/usr/share/doc/` - pakettien dokumentaatioita

`/var`
:   Järjestelmän muuttuvia tiedostoja. Esim. www-palvelimen tarjoilemat tiedostot hakemiston `/var/www/` alla, logitiedostot hakemiston `/var/log/` alla.




Hakemistorakenne
========================

Vähemmän kullattu selitys hakemistorakenteelle:

* [Kirjoitus Busybox-listalla](http://lists.busybox.net/pipermail/busybox/2010-December/074114.html)
* "Ken Thompsonilla ja Dennis Ritchiellä oli käytössään kaksi 1.5 MB:n kiintolevyä, joista toisessa oli järjestelmä ja toisessa käyttäjien tiedostot (`/usr`-hakemistossa).
   Kun järjestelmälevy tuli täyteen, sen hakemistorakenne (`/bin`, `/lib`, jne.) kopioitiin toiselle levylle `/usr`:n alle. Kun tilaa saatiin taas lisää,
   liitettiin se `/home`:ksi ja siirrettiin käyttäjien tiedostot sinne."
* Jälkikäteen keksittiin selitykset, että `/bin`, `/lib`, `/sbin` jne. sisältävät ensin tarvittavat osat ja `/usr`:n alla ovat vähemmän kriittiset jutut.




Liittäminen eli "mounttaaminen"
========================

Linuxissa (ja Unixeissa) ei ole levyasematunnuksia, kuten Windowsissa (c:\, d:\, ...), vaan kaikki tallennusmediat ovat samassa puussa.

* Joku levyosio tiedostojärjestelmän juurena `/`
* Muut osiot ja mediat, kuten usb-levyt ja optiset levyt liitetään, eli mountataan, johonkin hakemistoon puussa.
* Ennen esimerkiksi `/home` ja `/usr` olivat omilla levyosioillaan tai jopa toisella koneella.
* Hakemistot `/bin`, `/sbin` ja `/lib` siksi juuressa, että järjestelmä käytettävissä vaikka `/usr` ei jostain syystä olisi liitettynä.



{{% wrapper class="exercises" %}}
Tehtäviä
========================
Käynnistä jokin dvd-levyn työpöytä-Linux ja tee tehtävät siinä.
Kuvakaappauksen voi ottaa *PrintScreen*-näppäimellä. Tiedostot voit tallentaa erilliselle usb-tikulle tai lähettää ne itsellesi sähköpostilla.

1. Asenna peli nimeltä *Frozen-Bubble*, käynnistä se ja ota käynnissä olevasta pelistä kuvakaappaus. Palauta Moodleen.
2. Löytyvätkö valitsemastasi jakelusta ohjelmat Geary, Marble, Clementine ja Hugin? Mitä ohjelmia ne ovat?
3. Selvitä pakettien dokumentaatiohakemistosta, montako tekijää (author) on merkitty ohjelmalle *eog* (Eye of Gnome). Mistä löysit tiedon? Jos ohjelmaa *eog*
   ei ole asennettuna, tutki sen sijaan ohjelmaa *wget*.
4. Selvitä tiedostosta `/proc/cpuinfo` käyttämäsi koneen prosessorin merkki/malli.
5. Tiedostossa `/etc/passwd` luetellaan järjestelmässä olevat käyttäjätunnukset. Etsi rivi, jolla on tunnus nimeltä `nobody`.
   Mikä on nobodyn käyttäjänumero? (Rivin ensimmäinen numero kahden `:`-merkin välissä.)

{{% /wrapper %}}