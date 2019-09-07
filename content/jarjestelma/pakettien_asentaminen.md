---
date: "2016-09-05T23:03:37+03:00"
title: "Pakettien asentaminen"
sectiontitle: "Järjestelmä"
weight: 140
---

Linuxeissa paketinhallinnan kautta ohjelmat asennetaan ja poistetaan kätevästi.

Paketinhallintaan käytettävät graafiset ohjelmat toimivat vastaavasti kuin monista
muista järjestelmistä tutut sovelluskaupat, joista voi valita asennettavia ohjelmia.
Paketinhallinta on käytettävissä myös komentoriviltä komennoilla *apt-get* (Debian-johdannaiset),
*yum* (RedHat-/Fedora-johdannaiset) tai *zypper* (OpenSUSE).

Asennetaan esimerkiksi komentoriviltä tarralappujen tai käyntikorttien suunnitteluun sopiva Glabels-ohjelma:
```bash
sudo apt-get install glabels
```

Snap-pakettien asentaminen tapahtuu komentoriviltä ohelmalla nimeltä *snap*.

Esimerkiksi Spotify-ohjelman asentaminen snap-pakettina tapahtuu seuraavasti:
```bash
sudo snap install spotify
```



Pakettivarasto
========================

Pakettivarasto, eli pakettilähde, eli repository, on jakelun tekijän palvelimilla (sekä peilipalvelimilla
ympäri maailmaa) oleva kokoelma ohjelmapaketteja.

Esimerkiksi:

* Ubuntun pakettivaraston suomalainen peilipalvelin: <br> <http://fi.archive.ubuntu.com/ubuntu/>
* Version 18.04 pakettilista:<br> <http://fi.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-amd64/>
* Paketit:<br> <http://fi.archive.ubuntu.com/ubuntu/pool/>
* Pakettivaraston asetus tiedostossa `/etc/apt/sources.list` riveillä, jotka ovat muotoa:<br>
  `deb http://fi.archive.ubuntu.com/ubuntu/ bionic main restricted`

Paketit on jaoteltu jakelun version mukaan (bionic) ja sen alla muutamaan "tärkeysluokkaan"
(main, universe, multiverse, restricted)

* *main*: jakelun itse ylläpitämät,
* *universe*: yhteisön ylläpitämät,
* *restricted*: suljettuja ajureita yms.,
* *multiverse*: tekijänoikeuksien, patenttien yms. takia rajoitettuja paketteja

Lisäksi on tarjolla käyttäjien / kehittäjien omia repositoryja: Personal Package Archives - PPA

* https://launchpad.net/ubuntu/+ppas
* http://ppa.launchpad.net/

Pakettivarasto voi olla myös esim. asennus-cd:llä tai -usb:llä, jos se
tarvitsee toimittaa verkon ulottumattomiin.




Paketti
========================

Ohjelmistopaketti on käytännössä:

* Kokoelma tiedostoja
* pre-install -skripti, joka suoritetaan ennen paketin asennusta
* post-install -skripti, joka suoritetaan paketin asennuksen jälkeen
* pre-rm -skripti, joka suoritetaan ennen paketin poistoa
* post-rm -skripti, joka suoritetaan paketin poiston jälkeen
* riippuvuudet
* Paketin kuvausteksti
* mahdollisesti paketoijan allekirjoitus, jonka paketinhallinta voi tarkistaa




Esimerkkinä `abiword`-paketin sisältö:

```bash
$ dpkg -L abiword
/.
/usr
/usr/bin
/usr/bin/abiword
/usr/lib
/usr/lib/i386-linux-gnu
/usr/lib/i386-linux-gnu/abiword-2.9
/usr/lib/i386-linux-gnu/abiword-2.9/plugins
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/aiksaurus.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/applix.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/babelfish.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/bmp.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/clarisworks.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/collab.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/command.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/docbook.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/eml.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/epub.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/freetranslation.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/garble.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/gdict.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/gimp.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/google.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/hancom.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/hrtext.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/iscii.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/kword.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/latex.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/loadbindings.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/mht.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/mif.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/mswrite.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/opendocument.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/openwriter.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/openxml.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/opml.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/ots.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/paint.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/passepartout.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/pdb.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/pdf.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/presentation.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/s5.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/sdw.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/t602.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/urldict.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/wikipedia.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/wmf.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/wml.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/wordperfect.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/wpg.so
/usr/lib/i386-linux-gnu/abiword-2.9/plugins/xslfo.so
/usr/lib/mime
/usr/lib/mime/packages
/usr/lib/mime/packages/abiword
/usr/share
/usr/share/applications
/usr/share/applications/abiword.desktop
/usr/share/pixmaps
/usr/share/pixmaps/abiword_48.png
/usr/share/pixmaps/abiword.xpm
/usr/share/doc
/usr/share/doc/abiword
/usr/share/doc/abiword/readme.abw.gz
/usr/share/doc/abiword/copyright
/usr/share/doc/abiword/AUTHORS.gz
/usr/share/doc/abiword/readme.txt.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/abiword.1.gz
/usr/share/menu
/usr/share/menu/abiword
/usr/share/doc/abiword/changelog.Debian.gz}}}
```




Paketinhallintajärjestelmät
========================

Eri Linux-järjestelmissä käytetään elilaisessa muodossa olevia paketteja. Tyypillisimmät
paketointimuodot ovat:

|Tiedoston pääte |    |
|----------------|----|
|.deb            |    Peräisin Debianista. (Debian, Ubuntu, Mint, ...) |
|.rpm            |    Peräisin Red Hat Linuxista. (Red Hat/Fedora, Mandriva, openSUSE,...)|





Graafinen paketinhallinta
========================

{{< figure src="/images/ubuntu-software-center.png" link="/images/ubuntu-software-center.png" class="floatright floatimage" title="Ohjelmistovalikoima" caption="Ubuntun Software centerillä voi selata ohjelmistotarjontaa ja asentaa ohjelmia." >}}

Linux-jakeluissa on yleensä tarjolla jokin graafinen, eli ikkunoitu ja hiirellä käytettävä,
työkalu ohjelmistojen asennukseen. Ubuntussa tämä on Ubuntun Sovellusvalikoima (Ubuntu Software),
joka toimii mobiililaitteista tuttujen sovelluskauppojen tapaan. Siitä voi valita asennettavia
ohjelmistoja ja se hoitaa niitä vastaavien ohjelmistopakettien noutamisen pakettivarastosta ja niiden
asentamisen. Ohjelmien asentaminen vaatii ylläpito-oikeudellisen käyttäjän salasanan ennen pakettien
asentamista.

Graafiset paketinhallintaohjelmat on tarkoitettu helppokäyttöisiksi ja niillä voidaan helpohkosti:

* Selata ohjelmia *kategorioina*
* Hakea *hakusanalla*
* Selata *suositeltuja ohjelmia*
* *Asentaa* ja *poistaa* ohjelmia
* Päivittää ohjelmia
* Hallita ohjelmalähteitä eli pakettivarastoja (repository)
* Ubuntun *Software Center* sisältää myös joitain maksullisia ohjelmia ja lehtiä, jotka tulevat eri reittiä.

{{< figure src="/images/ubuntu-pakettivarastot.png" link="/images/ubuntu-pakettivarastot.png" class="floatright floatimage" title="Pakettivarastojen aktivointi" caption="Ubuntun pakettivarastoja ja niiden osioita voi aktivoida ja deaktivoida Sovellusvalikoiman asetuksista. Kuvassa aktivoituina main-, universe- ja restricted-osiot." >}}

Graafisissa paketinhallintaohjelmissa, kuten Ubuntun Sovellusvalikoimassa (Ubuntu Software) on yleensä
keino lisätä uusia pakettivarastoja sekä aktivoida tai deaktivoida olemassa olevia.

Ubuntun Sovellusvalikoima keskittyy tarjoamaan keinon ikkunoitujen suurelle yleisölle suunnattujen
sovellusten asentamiseen ja postamiseen. Sovellusvalikoima on valikotu eikä se näytä luetteloissaan
kaikkia saatavilla olevia paketteja.
*Synaptic* on toisenlainen graafinen paketinhallintaohjelma, jolla käyttäjä pystyy selaamaan, asentamaan
ja poistamaan kaikkia yksittäisiä paketteja, mukaan lukien komentoriviohjelmat ja kirjastot.



Matalan tason pakettienhallintaa komentorivillä
========================

"Matalan tason" paketinhallintaohjelma hoitaa ohjelmistopakettien todellisen
asentamisen. Debianissa ja sen jälkeläisissä (Ubuntu, Mint, ElementaryOS, jne.) matalan tason
paketinhallintaohjelma on `dpkg` ja RedHat-pohjaisissa järjestelmissä puolestaan `rpm`.

Näistä `dpkg`-ohjelmalla asennetaan `.deb`-päätteisiä ohjelmistopaketteja ja
`rpm`-ohjelmalla `.rpm`-päätteisiä paketteja. Paketinhallintaohjelmaa voi käyttää joko suoraan
komentoriviltä tai jollain korkeamman tason paketinhallintaohjelmalla.

Paketin asentaminen ja poistaminen vaativat ylläpito-oikeudet, eli esimerkiksi Ubuntussa
`dpkg`-ohjelman käyttäminen komentoriviltä vaatii `sudo`-komentoa. Esimerkit paketin asentamisesta
(install), poistamisesta (remove) ja poistamisesta myös asetustiedostot poistaen (purge):

```
sudo dpkg -i paketti.deb
sudo dpkg -r paketti
sudo dpkg -P paketti
```

Näiden lisäksi paketista voidaan esimerkiksi luetteloida paketin sisältö ja näyttää siitä tietoja.



Korkean tason pakettienhallintaa komentorivillä
========================

"Korkeamman tason" paketinhallintaohjelmat osaavat käsitellä paketteja monipuolisemmin.

* .deb-paketeille `apt` ja `aptitude`
* .rpm-paketeille `yum` ja `zypper`
* esim. `apt install inkscape`
* Tunnistavat paketin sen nimellä, ei tiedostonimellä
* Osaavat hakea paketin pakettivarastosta verkosta.
* Osaa selvittää tarvittavat riippuvuudet ja riippuvuuksien riippuvuudet, eli mitä muita
  paketteja on asennettava ja missä järjestyksessä.
* Osaavat ratkoa konflikteja, jos esimerkiksi paketin asentaminen vaatii toisen paketin poistamisen.
* Lisäksi: pakettien poistaminen, tietojen ja statuksen selaaminen, päivittäminen
    * Pakettilistan päivitys: `apt update`
    * Haetaan ja asennetaan paketit, joista on pakettivarastossa pakettilistan mukaan uudempi versio: `apt upgrade`
    * Pakettien etsiminen hakusanoilla: `apt search music player`
    * Paketin tilan tarkistaminen: `apt policy inkscape`
Myös näillä välineillä asentaminen (ja poistaminen) vaatii ylläpito-oikeudet, eli *sudo*-komennon käytön:

```bash
sudo apt install inkscape
sudo apt remove inkscape
```

Sekä graafiset paketinhallintaohjelmat että komentoriviltä suoritettavat korkeamman tason paketinhallintaohjelmat
ovat helppokäyttöisempiä käyttäliittymiä matalan tason paketinhallintaohjelmille.

Ubuntun ja Debianin käyttämän apt-paketinhallinnan komentoja:

| Tehtävä                         | Komento                                |
|---------------------------------|----------------------------------------|
| Asennus                         | `sudo apt install <pakettien nimet>`    |
| Poisto                          | `sudo apt remove <pakettien nimet>`     |
| Pakettilistan päivitys          | `sudo apt update`                       |
| Asennettujen pakettien päivitys | `sudo apt upgrade`                      |
| Haku                            | `apt search <hakusanoja>`        |
| Paketin tila                    | `apt policy <paketin nimi>`      |
| Paketin tiedot                  | `apt show <paketin nimi>`        |

Näistä järjestelmään muutoksia tekevät komennot tarvitsevat
ylläpito-oikeuksia, joten niiden edessä pitää olla komento `sudo`.

Snap
=====

Snap-paketoidut ohjelmat asennetaan `snap`-työkalulla. Se toimii hyvin samalla
tavalla kuin `apt`-komento.

| Tehtävä                         | Komento                               |
|---------------------------------|---------------------------------------|
| Haku                            | `snap find <hakusanoja>`              |
| Asennus                         | `sudo snap install <paketin nimi>`    |
| Poisto                          | `sudo snap remove <paketin nimi>`     |
| Paketin tiedot                  | `snap info <paketin nimi>`            |
| Luettele asennetut              | `snap list`                           |
| Päivitä valittu tai kaikki      | `sudo snap refresh [paketin nimi]`    |

AppImage
=========

AppImage-paketteina jaettavat ohjelmat eivät vaadi varsinaista asentamista.
Paketti vain ladataan omalle koneelle, siihen annetaan käyttäjälle suoritusoikeus
ja sen jälkeen sen voi käynnistää.

Esimerkki tällä tavalla ladattavasta ohjelmast on avoimen lähdekoodin
videoeditointiohjelma [OpenShot](https://www.openshot.org/).
OpenShot löytyy myös esimerkiksi Ubuntun omasta pakettivarastosta, mutta
AppImagena ladattavissa on usein uudempi versio.

Ero muihin käyttöjärjestelmiin
========================

* Windows
    * Ohjelmat asentuvat *c:\Program Files\\&lt;ohjelman nimi&gt;* -kansioon.
    * Ohjelmapaketit sisältävät kaikki omat tarpeensa käyttöjärjestelmän tarjoamia palveluita
      lukuun ottamatta.
    * Osa asennuspaketeista itse ajettavia .exe-tiedostoja, ei vain paketteja.
* MacOS
    * Ohjelmapaketit levykuvina
    * Ohjelmat asentuvat hakemistoon */Applications/ohjelma.app/* tai käyttäjän kotihakemistossa
      olevaan vastaavaan hakemistoon.
    * Ohjelmapaketit sisältävät kaikki omat tarpeensa käyttöjärjestelmän tarjoamia palveluita
      lukuun ottamatta.
    * Ohjelmia suoritetaan "hiekkalaatikossa".
* Linux (paketinhallinta)
    * Paketin tiedostot asentuvat eri puolille tiedostojärjestelmää
    * Paketinhallinta pitää kirjaa paketeista ja niihin liittyvistä tiedostoista
    * Tiedostojen paikat eivät määräydy paketin vaan merkityksensä mukaan.
    * Ohjelman asennus on pilkottu usein useampaan pakettiin, sillä osa tarvittavista kirjastoista
      voi olla yhteisiä monen muun ohjelman kanssa.
* Linux (snap)
    * Ohjelmapaketit levykuvina ja asentuu levyllä yhteen paikkaan.
    * Ohjelmat asentuvat keskitetystä [Snapcraft](https://snapcraft.io)-ohjelmavarastosta.
    * Ohjelmapaketit sisältävät kaikki omat tarpeensa käyttöjärjestelmän tarjoamia peruspalveluita
      lukuun ottamatta.
    * Ohjelmat suoritetaan oletuksena "hiekkalaatikossa".
* Linux (AppImage)
    * Ohjelmapaketit levykuvina
    * Käyttäjä voi kopioida mihin haluaa
    * Ohjelmapaketit sisältävät kaikki omat tarpeensa käyttöjärjestelmän tarjoamia peruspalveluita
      lukuun ottamatta.
    * Voi olla useampia versioita (tiedostoja) yhtä aikaa.

Kun ohjelmien tarvitsemat osat on pilkottu useampaan pakettiin, voivat eri ohjelmat käyttää yhteisiä osia
mainitsemalla ne omassa paketissaan riippuvuutena. Tämä on mahdollista avoimen lähdekoodin vuoksi.
Tästä on **hyötyä**:

- Ohjelmistot vievät levyltä vähemmän tilaa, kun kirjastot eivät ole moninkertaisesti eri ohjelmien mukana.
- Päivitykset, myös tietoturvapäivitykset, ovat yksinkertaisempia, kun tarvitsee päivittää vain
  rikkinäisen kirjaston paketti, ei kaikkia sitä käyttäviä paketteja. (Esimerkiksi Zlib-kirjaston
  haavoittuvuus)

**Haittoina** puolestaan voidaan mainita:

- Ohjelmistopakettien ylläpito täytyy olla koordinoidumpaa, jotta ohjelmistot toimivat esimerkiksi kirjaston
  saman version kanssa.
- Virallisten pakettivarastojen ulkopuolisten pakettien ylläpito voi olla hankalampaa, ellei
  tee niistä "itseriittoisia" ja samalla suurempia.



Tehtäviä
========================

{{% wrapper class="exercises" %}}
Tehtävät 5
===========

Käynnistä jokin työpöytä-Linux ja tee tehtävät siinä.
Kuvakaappauksen voi ottaa *PrintScreen*-näppäimellä.
Vastaa tiedostoon `tehtava-5.odt`.

1. Asenna vektoripiirto-ohjelma Inkscape. (graafisesti tai komentoriviltä) Käynnistä se ja ota siitä kuvakaappaus.
2. Tutki, löytyykö pakettivarastosta peli nimeltä *Frozen-Bubble*.
    - Jos ei löydy, avaa sovellusvalikoiman (Ubuntu Software) valikosta kohta "Ohjelmistot ja päivitykset"
      (Software & Updates) ja lisää sieltä *universe*-pakettivarasto. Tämän jälkeen sovellusvalikoima päivittää
      pakettilistan ja voit etsiä uudelleen Frozen-Bubblea. (paketin nimi `frozen-bubble`)
    - Asenna Frozen-Bubble, käynnistä se ja ota käynnissä olevasta pelistä kuvakaappaus.
    - (Jos ohjelmaa ei vieläkään löydy sovellusvalikoimasta, käytä asentamiseen komentorityökaluja.)
3. Löytyvätkö valitsemastasi jakelusta ohjelmat Geary, Marble, Clementine ja Hugin? Mitä ohjelmia ne ovat?
4. Selvitä pakettien dokumentaatiohakemistosta, montako tekijää (author) on merkitty ohjelmalle
   *eog* (Eye of Gnome). Mistä löysit tiedon?
    Jos ohjelmaa *eog* ei ole asennettuna, tutki sen sijaan ohjelmaa *wget*.
5. Etsi `snap`-työkalulla laivanupotuspeli (hakusana: "battleship") ja asenna se. Käynnistä ja ota kuvakaappaus.

{{% /wrapper %}}
