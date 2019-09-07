---
date: "2017-03-19T22:24:38+03:00"
title: "Työkalut"
weight: 600
type: "index"
menu:
    main:
        weight: 600
---

Linux-järjestelmiin löytyy paljon erilaisia järjestelmien ja verkon
ylläpitoon, analysointiin ja pelastamiseen soveltuvia työkaluja.
Erilaisten palautus ja diagnostiikkatyökalujen ympärille on tehty
myös omia Linux-jakeluita ja live-käynnistyslevyjä, jotka voivat olla
käteviä myös taskussa kannettavalla usb-tikulla. Seuraavassa
esitellään muutamia.



SystemRescueCD
=============

Järjestelmän pelastamiseen käytettävä Linux-CD tai -tikku.

- <http://www.system-rescue-cd.org/>

Levy sisältää työkalut esimerkiksi:

- Levyn osiointiin ja osioiden koon muuttamiseen
    - GNU Parted (osiointiohjelma, komentorivi)
    - GParted (edellisen graafinen käyttöliittymä)
- Datan kopiontiin ja levykuvan kloonaamiseen jopa osittain vioittuneelta levyltä
    - FSArchiver (Datan kopiointi ja arkostointi)
    - Partimage (Levykuvien luonti ja palautus)
    - Ddrescue (Vioittuneen levyn kopiointi)
- Tiedostojen palautukseen vioittuneelta levyltä (esim. kuvat kameran/puhelimen muistikortilta)
    - PhotoRec
    - Magicrescue

Levy sisältää myös verkkotyökalut, joilla tiedostot voi kopioida verkon yli
talteen useammallakin eri tavalla.




Levyn kopiointi
=============

Jos levy, esimerkiksi puhelimen muistikortti, on vioittunut ja sieltä pitäisi palauttaa
tai varmuuskopioida tiedostoja talteen ennen niiden katoamista, voi levystä kannattaa
ottaa ensimmäiseksi **levykuva** ja alkaa palauttaa tiedostoja vasta levykuvalta.
Näin vältetään jo rikkoutuneen tai rikkoutumassa olevan levyn ylimääräinen rasittaminen.
Varotaan myöskin kirjoittamasta alkuperäiselle levylle, ettei dataa mene hukkaan ylikirjoittamisen vuoksi.
Jos levy on rikki tai menossa rikki, voi jokainen luku/kirjoitus rikkoa sitä lisää.
Levykuvan voi levystä ottaa vaikka dd-ohjelmalla:

```no-highlight
dd if=/dev/sdb conv=sync,noerror bs=64K of=levykuva.img
```

Tässä:

- `if="input file"`, syötteenä yleensä levyn laitetiedosto
- `of="output file"`,
- `bs="block size"`,
- `noerror="älä välitä virheistä"`

Levykuvan voi halutessaan myös pakata, jolloin se vie vähemmän tilaa.

```no-highlight
dd if=/dev/hda conv=sync,noerror bs=64K | gzip -c  > levykuva.img.gz
```

[Levykuvan](/files/disk.img) kanssa voi harjoitella seuraavien työkalujen käyttöä datan palauttamiseksi.


Levykuvan liittäminen
=============

Levykuvan voi liittää osaksi hakemistopuuta siinä missä minkä tahansa levylaitteenkin.

Ladataan [levykuva](/files/disk.img) liitetään tiedostojärjestelmään ja tutkitaan sitä.
Sen jälkeen kokeillaan pelastustyökaluja datan löytämiseksi levykuvasta.

```no-highlight
sudo mount -o loop disk.img /mnt
```

Levykuva voi olla järkevää liittää read-only -tilassa, jolloin estetään se, että vahingossa kirjoitettaisiin
jotain pelastettavien tiedostojen päälle. Tämä tapahtuu lisäämällä `mount`-komentoon lisäparametri
`-o ro`.

```no-highlight
sudo mount -o loop -o ro disk.img /mnt
```

Tämän jälkeen levykuvan sisältämä tiedostojärjestelmä on liitetty osaksi hakemistopuuta hakemiston
`/mnt/` alle ja sen sisältöä voi tutkia esimerkiksi `ls`-komennolla.





Magicrescue
=============

Ohjelma tiedostojen palauttamiseen poistamisen jälkeen tai levyltä, jonka tiedostojärjestelmä on vioittunut.

- Lukee laitetiedostoa (esim. /dev/sda, /dev/sdb1, disk.img,...) suoraan datana välittämättä tiedostojärjestelmästä.
- Toimii hyödyntäen reseptejä, jotka kertovat, miltä tietyn tyyppisen tiedoston raakadatan pitäisi näyttää.
- Valmiita reseptejä mm. avi, jpeg-exif, jpeg-jfif, mp3-id3v1, mp3-id3v2, msoffice, png, zip
- Reseptejä voi tehdä myös itse, jos osaa.
- Reseptit löytyvät hakemistosta `/usr/share/magicrescue/recipes/`.

Seuraava komento etsii annetusta levykuvasta, `disk.img`, jpeg-kuvia ja tallentaa ne pyydettyyn hakemistoon.
Koska tiedostoja etsitään suoraan raakadatana, ei ohjelma tiedä niiden tiedostonimiä vaan tallentaa ne
satunnaisen näköisillä nimillä.

```no-highlight
magicrescue -d hakemisto -r jpeg-jfif disk.img
```



Recoverjpeg
=============

Toinen työkalu tiedostojen palauttamiseen levyltä.

- Vain jpeg-kuville
- Oletuksena hakee korkeintaan 6 MiB:n kokoisia kuvia, mutta rajaa voi kasvattaa.

```no-highlight
recoverjpeg -m 20M disk.img
```

Komento tuottaa työhakemistoon joukon jpg-tiedostoja, jotka on nimetty juoksevasti: `image00000.jpg`, `image00001.jpg` ja niin edelleen.



Photorec
=============

Kolmas työkalu tiedostojen palauttamiseen.

- Kysyy toimintoja valikolla
- Etsii automaattisesti kaikkia tuntemiaan tiedostomuotoja, joita on melko paljon. Muun muassa:<br>
  avi, wav, bmp, c, doc, html, jpg, mov, mp3, pdf, png, rtf, wma, zip, ...
- Voi pyytää etsimään vain levyn varaamattomasta tilasta, eli poistettuja tiedostoja, tai koko levyltä.

```no-highlight
photorec disk.img
```

Palautettavia tiedostoja etsittäessä voi kannattaa käyttää rinnakkain useampaa palautusohjelmaa,
koska joku niistä saattaa löytää tiedostoja, joita jokin toinen ei osaa löytää.




Dupemap
===========

Dupemap on ohjelma, joka vertaa annettuja hakemistoja ja osaa poistaa niistä samojen tiedostojen duplikaatit.

- Käy läpi luetelluissa hakemistoissa olevia tiedostoja ja vertailee niitä keskenään sekä poistaa ylimääräiset.
- Voi olla hyödyllinen myös palautettuja tiedostoja tutkittaessa, sillä palautus saattaa löytää saman
  tiedoston useammasta kohtaa levyä. Löydetyt tiedostot on yleensä myös nimetty satunnaisilla nimillä,
  jolloin vertailu tallessa oleviin tiedostoihin auttaa paljasamaan hukassa olleet.

```no-highlight
dupemap delete,report hakemisto
```

Poistaa ja raportoi hakemistosta `hakemisto` kaikki useamman kertaa esiintyvät tiedostot.

```no-highlight
dupemap -d hakem.map scan hakemisto1
dupemap -d hakem.map delete,report hakemisto2
```

Tästä komentoparista ensimmäinen käy läpi hakemiston `hakemisto1` kaikki tiedostot ja kirjoittaa niiden
tiedot tietokantaan `hakem.map`. Toinen komento puolestaan käy läpi hakemiston `hakemisto2` sisällön
ja vertaa sitä tietokantaan sekä poistaa sieltä kaikki tiedostot, jotka löytyvät jo hakemistosta `hakemisto1`.




Clonezilla
=============

Työkalu tietokoneen kiintolevyn kloonaamiseen ja palauttamiseen.

- Käynnistetään cd-/dvd-levyltä tai usb-tikulta
- Voidaan kloonata jokin tietokoneen kiintolevyistä tai osioista levykuvaksi
- Kuva voidaan tallentaa kiintolevylle, usb-levylle tai verkon yli toiselle koneelle
- Levykuva voidaan palauttaa takaisin kiintolevylle
- Kätevä puhtaan asennuksen palauttamisessa saastuneen tai muuten vioittuneen järjestelmälevyn tilalle.
- Käytännöllinen, kun pitää asentaa samanlainen järjestelmä usealle identtiselle koneelle (esim. mikroluokkaan).




Kali Linux
=============

[Kali Linux](https://www.kali.org/) tietoturvatestaukseen tarkoitettu Linux-jakelu. Krakkerin ja testaajan "sveitsinlinkkari", joka
sisältää suurin piirtein kaikki mahdolliset avoimen lähdekoodin murto- ja analysointityökalut.

Kali Linuxin kohdalla täytyy muistuttaa, että ***sitä saa käyttää vain omassa hallussa olevien
järjestelmien tietoturvan testaamiseen ja murtamiseen***. Muiden järjestelmien murtamisessa
ollaan hyvin pian rikollisissa puuhissa.

Kali Linuxin live-levykuvan voi ladata projektin kotisivuilta osoitteesta: <https://www.kali.org/>



Metasploitable
===============

[Metasploitable](https://sourceforge.net/projects/metasploitable/) on tarkoituksella haavoittuvaksi tehty Linux-virtuaalikone. Se on tarkoitettu
turvallisuusharjoitteluun ja turvallisuustyökalujen testaamiseen.

Metasploitablen kanssa on erittäin tärkeää, että sitä ei altisteta ei-luotetulle verkolle, eli
virtuaalikonetta on syytä siten, että vain isäntäkoneelta pääsee siihen käsiksi.


Tails
======

[Tails](https://tails.boum.org/) on live-käyttöjärjestelmä, joka on suunnattu yksityisyyden ja tietoturvan
erityistarpeisiin. Se on siirrettävältä levyltä (usb-tikku, dvd, sd-kortti) käynnistettävä Linux-järjestelmä,
jonka tarkoituksena on suojata yksityisyyttä ja anonymiteettiä.

- Sillä voi käyttää internetiä anonyymisti ja kiertää sensuurirajoituksia
- Se kierrättää kaiken liikenteen [Tor-verkon](https://www.torproject.org/) kautta.
- Live-levynä se ei jätä jälkiä käytetylle tietokoneelle, ellei erikseen ole tarkoitus.
- Se tarkoaa käyttöön viimeisimmät kryptografiset työkalut tiedostojen, sähköpostin ja pikaviestinnän
  salaamiseen.
