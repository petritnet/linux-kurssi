+++
date = "2016-09-05T23:03:48+03:00"
title = "Tiedostojärjestelmä"
weight = 105
+++

Linuxissa, kuten muissakin UNIX-tyyppisissä käyttöjärjestelmissä, tiedostojärjestelmä on toteutettu yhtenä
puurakenteena, jolla on yksi *juuri*. Juuresta käytetään merkintää `/`.
Koko muu tiedostojärjestelmä sijoittuu juuren alle *hakemistoista* muodostuvana
puuna. (Windows-ympäristöissä hakemistoista käytetään nimitystä kansio.)

Absoluuttinen polku
===================

{{< figure src="/images/filesystem.png" link="/images/filesystem.png" class="floatright floatimage" title="Tiedostojärjestelmä" caption="Tiedostojärjestelmä on puurakenne, jolla on yksi juuri." >}}

Kunkin tiedoston sijainti tiedostojärjestelmässä voidaan ilmaista sen *absoluuttisena polkuna*,
eli `/`-merkeillä eroteltuna reittinä juuresta hakemistorakenteen läpi itse tiedostoon saakka.
Esimerkiksi, kun tiedostojärjestelmän juuren `/` alla on hakemisto `etc/`, jonka sisällä on
toinen hakemisto `cups/` ja tämän sisällä tiedosto nimeltä `classes.conf`,
niin tämän tiedoston absoluuttinen polku on:

```
/etc/cups/classes.conf
```

Suhteellinen polku
==================

Huomattavaa on, että hakemistorakenteen erotinmerkkinä on kauttaviiva, eli "etukeno", kun Windows-järjestelmissä
erottimena on `\`, eli "takakeno". Jos tiedoston sijainti halutaan ilmaista suhteessa johonkin muuhun
hakemistoon kuin juureen, käytetään *suhteellista polkua*. Esimerkiksi hakemiston `/etc` suhteen edellä
tarkastellun tiedoston sijainti on `cups/classes.conf`. Absoluuttisen ja suhteellisen polun erottaa
siitä, että **absoluuttinen polku alkaa aina juuresta**, eli merkillä `/`.

Jokaisessa hakemistossa on lisäksi kaksi erityistä hakemistoa, `.` ja `..`. Yhdellä pisteellä tarkoitetaan
hakemistoa itseään ja kahdella pisteellä sen "edeltäjää", eli "vanhempaa", eli hakemistoa, joka on yhden askeleen
juuren suuntaan. Siis esimerkiksi hakemistossa `/etc/cups/` yksi piste tarkoittaa tätä hakemistoa itseään.
Toisin sanoen hakemisto `/etc/cups/./` on sama kuin hakemisto `/etc/cups/`. Vastaavasti hakemisto `/etc/cups/../`
on puolestaan sama kuin hakemisto `/etc/`. Näin suhteellisella polulla voidaan viitata mihin tahansa
tiedostojärjestelmän tiedostoon. Esimerkiksi hakemistosta `/etc/cups/` nähden suhteellinen polku
`../X11/rgb.txt` viittaa samaan tiedostoon kuin absoluuttinen polku `/etc/X11/rgb.txt`.



Liittäminen eli "mounttaaminen"
========================

Windowsissa kullekin järjestelmään asennetulle kiintolevylle, optiselle levylle,
usb-muistille tai muulle siirrettävälle medialle annetaan oma levyasematunnus, esimerkiksi
`C:\`, `D:\` jne. Linuxissa ei tällaisia levyasematunnuksia käytetä vaan koko levyn sisältö liitetään
yhtenä puun haarana johonkin kohtaan hakemistopuuta. Esimerkiksi usb-porttiin kytketyn
muistitikun sisältö saatetaan liittää vaikka hakemiston `/media/pesasa/6365-3030/` alle.

* Joku levyosio on tiedostojärjestelmän juurena `/`
* Muut osiot ja mediat, kuten usb-levyt ja optiset levyt *liitetään*, eli *mountataan*, johonkin hakemistoon puussa.
* Ennen, ja joskus nykyäänkin, esimerkiksi `/home` ja `/usr` olivat omilla levyosioillaan tai jopa toisella koneella.
* Hakemistot `/bin`, `/sbin` ja `/lib` ovat siksi juuressa, että ne olisivat järjestelmä käytettävissä vaikka `/usr` 
  ei jostain syystä olisikaan liitettynä.



Vakiohakemistot
========================

Järjestelmässä ovat tietyt vakiohakemistot, joilla ovat omat merkityksensä:

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


| Hakemisto | Merkitys |
|-----------|----------|
| `/`     |  Juurihakemisto. Hakemistopuun juuri. Kaikki tiedostot ja levyt ovat samassa puussa. |
|`bin`    |  Järjestelmän oleellisimmat ajettavat tiedostot. Varmasti käytettävissä. |
|`/boot`  |  Käynnistykseen tarvittavia tiedostoja |
|`/cdrom` |  Paikka johon optinen levy liitetään.  |
|`/dev`   |  Kaikki laitteet ovat tässä hakemistossa edustettuina tiedostoina. Eivät oikeasti levyllä. Esim. /dev/sda on kiintolevy ja /dev/sda1 sen ensimmäinen osio. |
|`/etc`   |  Ohjelmien järjestelmänlaajuiset asetukset. |
|`/home`  |  Käyttäjien kotihakemistot. Esimerkiksi: `/home/pesasa/`, `/home/matti/` |
|`/lib`   |  Oleellisimpia ohjelmakirjastoja, joita ohjelmat hyödyntävät. Varmasti käytettävissä. |
|`/lost+found` | Levyntarkistuksessa löydetyt vaurioituneet tiedostot, joiden oikeaa paikkaa ei tiedetä.|
|`/media` |  Hakemisto, jonka alle siirrettävät levyt, esim. muistitikut liitetään. |
|`/mnt`   |  Satunnaisia hakemistopuuhun liitettäviä tiedostojärjestelmiä varten. |
|`/opt`   |  Paketinhallinnan ulkopuolelta asennettuja ohjelmia. |
|`/proc`  |  Virtuaalisia tiedostoja, jotka edustavat käynnissä olevaa järjestelmää. Esim. /proc/cpuinfo sisältää tietoa prosessorista. |
|`/root`  |  root-käyttäjän kotihakemisto |
|`/run`   |  Käynnissä olevien ohjelmien ja palveluiden tietoja. Esim. palvelinprosessien prosessi-id:itä. |
|`/sbin`  |  Järjestelmän oleellisimmat ajettavat järjestelmätiedostot. Varmasti käytettävissä. |
|`/sys`   |  Virtuaalisia tiedostoja liittyen järjestelmään. |
|`/tmp`   |  Tilapäistiedostoille |
|`/usr`   |  Ohjelmat asentuvan tämän hakemiston alle. |
|`/usr/bin/` | Ajettavat tiedostot |
|`/usr/sbin/`| Ajettavat järjestelmän ylläpidon tiedostot|
|`/usr/lib/` | Kirjastoja |
|`/usr/local/` | Paketinhallinnan ulkopuolelta asennettuja ohjelmia |
|`/usr/share/` | Mm. ohjelmien tiedostot omissa hakemistoissaan  |
|`/usr/share/doc/` | Pakettien dokumentaatioita |
|`/var`   |  Järjestelmän muuttuvia tiedostoja. Esim. www-palvelimen tarjoilemat tiedostot hakemiston `/var/www/` tai `/var/www/html/` alla ja logitiedostot hakemiston `/var/log/` alla. |




Hakemistorakenne
========================

Vaikka yllä oleva lista antaa selityksen, miksi UNIX-järjestelmien hakemistorakenne on sellainen kuin se on,
on olemassa myös vähemmän kullattu selitys hakemistorakenteelle:

* [Kirjoitus Busybox-listalla](http://lists.busybox.net/pipermail/busybox/2010-December/074114.html)
* "Ken Thompsonilla ja Dennis Ritchiellä oli käytössään kaksi 1.5 MB:n kiintolevyä, joista toisessa oli järjestelmä ja toisessa käyttäjien tiedostot (`/usr`-hakemistossa).
   Kun järjestelmälevy tuli täyteen, sen hakemistorakenne (`/bin`, `/lib`, jne.) kopioitiin toiselle levylle `/usr`:n alle.
   Kun tilaa saatiin taas lisää (uusi levy), liitettiin se `/home`:ksi ja siirrettiin käyttäjien tiedostot sinne."
* Jälkikäteen keksittiin selitykset, että `/bin`, `/lib`, `/sbin` jne. sisältävät ensin tarvittavat osat ja `/usr`:n alla ovat vähemmän kriittiset jutut.


