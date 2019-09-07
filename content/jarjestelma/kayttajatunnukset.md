---
date: "2016-09-06T21:59:51+03:00"
title: "Käyttäjätunnukset"
sectiontitle: "Järjestelmä"
weight: 110
---

Linuxissa, kuten Unixeissa yleensä, on käyttäjähallinta toteutettu käyttäjätunnuksilla
ja käyttäjäryhmillä.

Käyttäjätunnukset
==================

Käyttäjätunnus on käyttäjän tekstimuotoinen "lempinimi". Käyttäjä kirjautuu järjestelmään
käyttäjätunnuksella ja salasanalla.

Järjestelmän sisäisesti käyttäjät tunnistetaan käyttäjänumerolla (`uid`, user id) ja kukin
ihmisten luettavaksi tarkoitettu käyttäjätunnus vastaa jotakin käyttäjänumeroa.
Tiedostossa `/etc/passwd` on lueteltu vastaavuus käyttäjänimien ja -numeroiden välillä.
Tiedostossa on lisäksi muun muassa tieto käyttäjän koko nimestä, kotihakemistosta ja
käyttäjän oletus komentotulkki.
Kunkin käyttäjän tiedot ovat tiedostossa yhdellä rivillä.
Tiedoston rivit ovat muotoa:

```no-highlight
pesasa:x:1000:1000:Petri Salmela,,,:/home/pesasa:/bin/bash
```

Käyttäjien salasanat on oletuksena tallennettu "tiivisteinä" tiedostoon `/etc/shadow`.
Tässä tiedostossa rivit ovat muotoa:

```no-highlight
pesasa:$6$mE/6BCoS$oV7b2d2//73dGtKHL.G9ezHgFQ9/kJcJVmqiP8YRiS7T76uRxU3oxx0P/uuYfwtgHxd4/1015dFRB.wJNYhI/.:15595:0:99999:7:::
```



Käyttäjäryhmät
==================

Käyttäjille voidaan antaa oikeuksia erilaisiin toimintoihin liittämällä heidät ryhmiin,
joilla on kyseinen oikeus. Esimerkiksi Ubuntu-pohjaisissa järjestelmissä ylläpitäjät ovat
ryhmässä nimeltä `sudo`.

Käyttäjä voi olla yhtä aikaa useammassa ryhmässä. Järjestelmä tunnistaa käyttäjäryhmän
sisäisesti ryhmän numerolla (`gid`, group id). Ryhmän nimen ja numeron välinen
kytkentä löytyy tiedostosta `/etc/group`. Tiedostossa on yksi rivi per ryhmä. Samalla
rivillä luetellaan kaikki kyseiseen ryhmään kuuluvat käyttäjät.

Tiedoston rivit ovat muotoa:
```no-highlight
audio:x:29:pulse,timidity
```

Käyttäjätunnuksen ja ryhmän avulla käyttäjälle voidaan antaa oikeuksia toimintoihin ja
tiedostoihin.

Käyttäjätunnuksesta ja ryhmistä saa tietoa komentorivillä komennolla `id`. Esimerkiksi:

```no-highlight
$ id
uid=1000(pesasa) gid=1000(pesasa) ryhmät=1000(pesasa),4(adm),7(lp),24(cdrom),27(sudo),30(dip),46(plugdev),115(lpadmin),130(sambashare)
```
Tulosteessa kerrotaan käyttäjän uid ja käyttäjätunnus sekä ryhmät, jossa käyttäjä on, ryhmänumeroina ja -niminä.





Pääkäyttäjä
=============

Unix-tyyppisissä järjestelmissä on ylin ylläpitovalta on pääkäyttäjällä, jonka
käyttäjätunnus on `root` ja jonka käyttäjänumero on `0`. `root`-käyttäjällä on
täysi oikeus tehdä järjestelmässä mitä tahansa. Normaalisti tavallinen järjestelmän
käyttö tehdään tavallisella ei-`root`-tunnuksella ja `root`-tunnuksella tehdään
vain välttämättömät ylläpitotoimet. Joissain Linux-jakeluissa, kuten Ubuntussa,
on sisäänkirjautuminen `root`-tunnuksella estetty oletuksena kokonaan ja
ylläpitotehtävät suoritetaan tavallisena käyttäjänä, mutta erillistä `sudo`-komentoa
käyttäen.



Sudo
======

Monissa Linux-jakeluissa on käytettävissä `sudo`-komento, jolla tavallinen käyttäjä
voi suorittaa ylläpitotoimia käyttäen väliaikaisesti `root`-käyttäjän oikeuksia.
Komennon nimi tulee sanoista **s**uper **u**ser **do**, eli "tee pääkäyttäjän
oikeuksilla". Tämän komennon käyttö edellyttää, että käyttäjälle on annettu oikeus
sen käyttöön ja määritelty, mitä toimintoja sillä saa tehdä. Tyypillisesti
`sudo`-komennon rajoittamaton käyttöoikeus on annettu niille käyttäjille, jotka
ovat jossain ylläpitäjille tarkoitetussa ryhmässä. Ubuntussa ja sen johdannaisissa
tämä ryhmä on tyypillisesti `sudo`, RedHatin ja Fedoran johdannaisissa puolestaan
`wheel`.

Ylläpitokomentoja annettaessa niiden eteen laitetaan `sudo`-komento, jolloin
järjestelmä tietää, että ne pitää suorittaa `root`-käyttäjänä. Tällainen ylläpitotehtävä
on esimerkiksi sovelluksen asentaminen. Esimerkiksi ohjelman **Inkscape** asennus
Ubuntussa tapahtuu seuraavalla komennolla:

```no-highlight
sudo apt-get install inkscape
```

Tämän jälkeen `sudo` varmistaa käyttäjän henkilöllisyyden kysymällä tämän omaa
salasanaa. Jos salasanan kirjoittaa oikein ja käyttäjällä oli oikeus `sudo`-komennon
käyttöön, suoritetaan käsketty toiminto `root`-käyttäjänä. Onnistuneen
salasanatunnistautumisen `sudo` muistaa oletuksena seuraavat 15 minuuttia eikä
kysy tänä aikana salasanaa uudelleen uusien `sudo`-komentojen yhteydessä.

Tärkeimpiä hyötyjä `sudo`-komennon käytöstä verrattuna `root`-käyttäjänä
kirjautumiseen on se, että vain ehdottomasti ylläpito-oikeuksia tarvitseviin tehtäviin
käytetään pääkäyttäjän oikeuksia. Toinen hyöty tulee siitä, että
ylläpito-oikeuksia voidaan antaa useammalle ylläpitäjälle niin, että he tekevät
ylläpitotoimet kuitenkin omalla identiteetillään ja salasanallaan vahvistaen.
Näin vältytään yhteisen `root`-tunnuksen ja salasanan käytöltä. Esimerkiksi ylläpitäjän
vaihtaessa työpaikkaa, riittää hänen tunnuksensa poistaminen käytöstä.
Käytetyistä `sudo`-komennoista pidetään kirjaa, jolloin tiedetään, kuka on tehnyt mitäkin.
Lisäksi `sudo`-komennolla voidaan käyttäjälle antaa oikeuksia hienovaraisemmin kuin vain
"kaikki `root`-käyttäjän oikeudet". Käyttäjälle voidaan siis antaa vain rajoitetut
ylläpito-oikeudet johonkin järjestelmän osaan.



Käyttäjän lisääminen
==================

{{< figure src="/images/ubuntu-systemsettings.png" link="/images/ubuntu-systemsettings.png" class="floatright floatimage" title="Ubuntun järjestelmäasetukset" caption="Käyttäjätunnuksia lisätään, poistetaan ja muokataan User Accounts -työkalulla." >}}

{{< figure src="/images/ubuntu-addaccount.png" link="/images/ubuntu-addaccount.png" class="floatright floatimage" title="Käyttäjätunnuksen lisääminen" >}}

{{< figure src="/images/ubuntu-changepassword.png" link="/images/ubuntu-changepassword.png" class="floatright floatimage" title="Salasanan asettaminen" >}}

Ubuntussa ja monessa muussa Linux-järjestelmässä käyttäjä, jolla on ylläpito-oikeudet, voi lisätä ja poistaa
käyttäjiä asetustyökalun käyttäjienhallinnalla.

Työkalun lukitus avataan käyttäjän omalla salasanalla, jotta saadaan käyttöön ylläpito-oikeudet. Uutta käyttäjää
lisättäessä:

- Valitaan uuden käyttäjän tyyppi (Standard / Administrator)
    - Käyttäjä lisätään tyypin mukaan tiettyihin ryhmiin.
    - Standard: vain saman niminen ryhmä kuin käyttäjätunnus
    - Administrator: lisäksi ryhmä `sudo`
- Annetaan salasana joko käsin syötettynä tai automaattisesti generoituna.
- Valitaan, halutaanko *Automatic login*, eli halutaanko, että järjestelmä kirjautuu käynnistymisen jälkeen suoraan
  sisään tällä tunnuksella.




Myöhemmin kurssilla käsitellään käyttäjätunnusten hallintaa komentoriviltä käsin.
