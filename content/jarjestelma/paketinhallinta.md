+++
date = "2016-09-05T23:03:37+03:00"
title = "Paketinhallinta"
sectiontitle = "Järjestelmä"
weight = 130
+++

Linuxeissa on tyypillisesti käytössä paketinhallinta, jonka kautta ohjelmat asennetaan ja poistetaan kätevästi.

Koska Linux-jakelut koostuvat pääasiassa vapaista avoimen lähdekoodin ohjelmista, voidaan niitä jaella
keskitetysti jakelun tekijän palvelimelta *pakettivarastosta*, eli niin kutsutusta *"repositorysta"*.

Asennuspakettien välillä voi olla *riippuvuuksia*, mikä tarkoittaa sitä, että yhden paketin
asentaminen voi vaatia jonkin toisen paketin asentamisen riippuvuuden takia. Näin on esimerkiksi
silloin, jos ohjelma tarvitsee toimiakseen jotain jaettua kirjastoa, eli jotain ohjelmistokomponenttia,
joka on yhteinen muiden ohjelmien kanssa. Riippuvuutena olevan kirjaston poistaminen poistaa myös
siitä riippuvan ohjelmiston. Pakettien joukossa voi olla myös *meta-paketteja*, eli sellaisia
paketteja, jotka eivät itse sisällä mitään tiedostoja vaan ainoastaan riippuvuuksia muihin paketteihin.
Tällaisen asentamalla voi asentaa suurempia ohjelmistokokonaisuuksia kerralla.
Tällainen on esimerkiksi `kubuntu-desktop`-paketti, jonka asentamalla Ubuntuun voi asentaa kaikki
KDE-työpöytäympäristön käyttämiseen tarvittavat paketit.

Paketinhallintaan käytettävät graafiset ohjelmat ovat tyypillisesti kuin joistain muista järjestelmistä
tutut sovelluskaupat, joista voi valita asennettavat ohjelmat. Paketinhallinta on käytettävissä myös
komentoriviltä komennoilla *apt-get* (Debian-johdannaiset), *yum* (RedHat-/Fedora-johdannaiset) ja
*zypper* (OpenSUSE).

Asennetaan esimerkiksi komentoriviltä tarralappujen tai käyntikorttien suunnitteluun sopiva Glabels-ohjelma:
```bash
sudo apt-get install glabels
```




Pakettivarasto
========================

Pakettivarasto, eli repository, on jakelun tekijän palvelimilla (sekä peilipalvelimilla ympäri maailmaa)
oleva kokoelma ohjelmapaketteja. Varastossa on lisäksi luettelo tarjolla olevista paketeista.

* `deb http://fi.archive.ubuntu.com/ubuntu/ saucy main restricted`
* http://fi.archive.ubuntu.com/ubuntu/
* Pakettilista: http://fi.archive.ubuntu.com/ubuntu/dists/saucy/main/binary-amd64/
* Paketit: http://fi.archive.ubuntu.com/ubuntu/pool/
* Paketit on jaoteltu jakelun version mukaan (saucy) ja sen alla muutamaan "tärkeysluokkaan"
  (main, universe, multiverse, restricted)
    * main: jakelut itse ylläpitämät,
    * universe: yhteisön ylläpitämät,
    * restricted: suljettuja ajureita yms.,
    * multiverse: tekijänoikeuksien, patenttien yms. takia rajoitettuja paketteja
* Käyttäjien / kehittäjien omia repositoryja: Personal Package Archives - PPA
    * https://launchpad.net/ubuntu/+ppas
    * http://ppa.launchpad.net/
* Pakettivarasto voi olla myös esim. asennus-cd:llä tai -usb:llä.




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
|--------------|----|
|.deb |    Peräisin Debianista. (Debian, Ubuntu, Mint, ...) |
|.rpm |    Peräisin Red Hat Linuxista. (Red Hat/Fedora, Mandriva, openSUSE,...)|
|.tar.gz / .tgz |   Pelkkä paketti ilman paketinhallinnan rakenteita. (kuten zip)|





Graafinen paketinhallinta
========================

{{< figure src="/images/ubuntu-software.png" link="/images/ubuntu-software.png" class="floatright floatimage" title="Ohjelmistovalikoima" caption="Ubuntun Software centerillä voi selata ohjelmistotarjontaa." >}}

Vaatii ylläpito-oikeudellisen käyttäjän salasanan ennen pakettien asentamista. Graafiset
paketinhallintaohjelmat on tarkoitettu helppokäyttöisiksi ja niillä voidaan helpohkosti:

* Selata ohjelmia *kategorioina*
* Hakea *hakusanalla*
* Selata *suositeltuja ohjelmia*
* *Asentaa* ja *poistaa* ohjelmia
* Päivittää ohjelmia
* Hallita ohjelmalähteitä eli pakettivarastoja (repository)
* Ubuntun *Software Center* sisältää myös joitain maksullisia ohjelmia ja lehtiä, jotka tulevat eri reittiä.




Matalan tason pakettien hallintaa komentorivillä
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



Korkean tason pakettien hallintaa komentorivillä
========================

"Korkeamman tason" paketinhallintaohjelmat osaavat käsitellä paketteja monipuolisemmin.

* .deb-paketeille `apt-get` ja `aptitude`
* .rpm-paketeille `yum` ja `zypper`
* esim. `apt-get install inkscape`
* Tunnistavat paketin sen nimellä, ei tiedostonimellä
* Osaavat hakea paketin pakettivarastosta verkosta.
* Osaa selvittää tarvittavat riippuvuudet ja riippuvuuksien riippuvuudet, eli mitä muita
  paketteja on asennettava ja missä järjestyksessä.
* Osaavat ratkoa konflikteja, jos esimerkiksi paketin asentaminen vaatii toisen paketin poistamisen.
* Lisäksi: pakettien poistaminen, tietojen ja statuksen selaaminen, päivittäminen
    * Pakettilistan päivitys: `apt-get update`
    * Haetaan ja asennetaan paketit, joista on pakettivarastossa pakettilistan mukaan uudempi versio: `apt-get upgrade`
    * Pakettien etsiminen hakusanoilla: `apt-cache search music player`
    * Paketin tilan tarkistaminen: `apt-cache policy inkscape`
Myös näillä välineillä asentaminen (ja poistaminen) vaatii ylläpito-oikeudet, eli *sudo*-komennon käytön:

```bash
sudo apt-get install inkscape
sudo apt-get remove inkscape
```

Sekä graafiset paketinhallintaohjelmat että komentoriviltä suoritettavat korkeamman tason paketinhallintaohjelmat
ovat helppokäyttöisempiä käyttäliittymiä matalan tason paketinhallintaohjelmille.


Ero muihin käyttöjärjestelmiin
========================

* Windows
    * Ohjelmat asentuvat *c:\Program Files\\&lt;ohjelman nimi&gt;* -kansioon
    * Osa asennuspaketeista itse ajettavia .exe-tiedostoja, ei vain paketteja.
* Mac OS X
    * Ohjelmapaketit levykuvina
    * Ohjelmat asentuvat hakemistoon */Applications/ohjelma.app/* tai käyttäjän kotihakemistossa
      olevaan vastaavaan hakemistoon.
* Linux
    * Paketin tiedostot asentuvat eri puolille tiedostojärjestelmää
    * Paketinhallinta pitää kirjaa paketeista ja niihin liittyvistä tiedostoista
    * Tiedostojen paikat eivät määräydy paketin vaan merkityksensä mukaan.

    
    
    
Vertaus: Solukämppä
========================
Pekka, Matti ja Jorma asuvat kolmen hengen opiskelijasolussa. Heillä on yhteinen keittiö. Miltä jääkaappi näyttää?

* Pekalla ylähylly, Matilla keskihylly ja Jormalla alahylly
* Jokaisella hyllyllä purkki maitoa tai tuoremehua, rasiallinen leviterasvaa, juustoa ja/tai makkaraa, ketsuppia/sinappia + sekalaisia eineksiä
* Jokainen käyttää aineksia omalta hyllyltään
* Tilaa menee hukkaan, kun jokaisella on esim. oma leviterasia.
Toimii samoin kuin ohjelmat Windows- ja Mac OS X -alustoilla.




Vertaus: Kolmen hengen perhe
========================

Isä, äiti ja teinitytär asuvat asunnossa. Miltä jääkaappi näyttää?

* Ovessa juomat (maito, tuoremehu, Cola-pullo)
* Hyllyllä yksi leviterasia, juustoa, kinkkurasia, rasiallinen tähteitä
* Toisella hyllyllä hillopurkki, sinapp, ketsuppi
* Kolmannella hyllyllä leivontamargariinia, kananmunia, ...
Kuten Linux-jakeluissa: Ainekset lajiteltu tyypin mukaan, ei omistajan/käyttäjän.


Tehtäviä
========================

{{% wrapper class="exercises" %}}
Tehtävät 5
===========

Käynnistä jokin työpöytä-Linux ja tee tehtävät siinä.
Kuvakaappauksen voi ottaa *PrintScreen*-näppäimellä.
Palautus tiedostona `tehtava-5.odt`.

1. Asenna peli nimeltä *Frozen-Bubble*, käynnistä se ja ota käynnissä olevasta pelistä kuvakaappaus.
2. Löytyvätkö valitsemastasi jakelusta ohjelmat Geary, Marble, Clementine ja Hugin? Mitä ohjelmia ne ovat?
3. Selvitä pakettien dokumentaatiohakemistosta, montako tekijää (author) on merkitty ohjelmalle
   *eog* (Eye of Gnome). Mistä löysit tiedon?
    Jos ohjelmaa *eog* ei ole asennettuna, tutki sen sijaan ohjelmaa *wget*.

{{% /wrapper %}}

