+++
date = "2016-09-06T21:59:51+03:00"
title = "Käyttäjätunnukset"
sectiontitle = "Järjestelmä"
weight = 110
+++

Linuxissa, kuten Unixeissa yleensä, on käyttäjähallinta toteutettu käyttäjätunnuksilla
ja käyttäjäryhmillä.

Käyttäjätunnukset
==================

Käyttäjätunnus on tekstimuotoinen "lempinimi" käyttäjälle. Käyttäjä kirjautuu järjestelmään
käyttäjätunnuksella ja salasanalla.

Järjestelmän sisäisesti käyttäjät tunnistetaan käyttäjänumerolla (uid, User id) ja kukin
ihmisten luettavaksi tarkoitettu käyttäjätunnus on kytketty johonkin käyttäjänumeroon.
Tiedostossa `/etc/passwd` on lueteltu vastaavuus käyttäjänimien ja -numeroiden välillä.
Lisäksi tiedostossa on muun muassa tieto käyttäjän koko nimestä, kotihakemistosta ja
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
sisäisesti ryhmän numerolla (gid, Group id). Ryhmän nimen ja numeron välinen
kytkentä löytyy tiedostosta `/etc/group`. Tiedostossa on yksi rivi per ryhmä ja samalla
rivillä luetellaan lisäksi kaikki kyseiseen ryhmään kuuluvat käyttäjät.

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
