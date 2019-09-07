---
date: "2019-08-31T19:48:00+03:00"
title: "Ohjelmistopaketit"
sectiontitle: "Järjestelmä"
weight: 130
---

Ohjelmia Linux-järjestelmiin voidaan asentaa useammalla eri tavalla.

| Paketointityyppi        | Mitä tarkoittaa                                         | Esimerkiksi             | Työkalut         |
|-------------------------|---------------------------------------------------------|-------------------------|------------------|
| Jakelun paketinhallinta | Joukko paketteja, joilla on keskinäisiä riippuvuuksia.  | deb, rpm                | apt, yum, zypper |
| Riippumattomat paketit  | Paketteja, jotka sisältävät kaiken tarvitsemansa.       | Snap, AppImage, Flatpak | snap             |
| "Villit" paketit        | Purettava paketti, jossa ohjelmisto pakattuna.          | tar.gz, tar.bz, zip     | tar, unzip       |
| Lähdekoodipaketit       | Purettava paketti, jossa lähdekoodi, joka pitää kääntää.| tar.gz, tar.bz, zip     | tar, unzip       |

Paketinhallinta
================

Perinteisesti käytössä on jakelun keskitetty *pakettienhallinta*, jonka kautta
tyypillisesti itse järjestelmää sekä avoimen lähdekoodin sovelluksia
asennetaan ja päivitetään. Linux-jakelut ylläpitävät *pakettivarastoa*, eli
niin kutsuttua *"repositorya"*, josta paketit ovat asennettavissa. pakettivarastosta
saatavilla olevat ohjelmat ovat pääasiassa vapaita avoimen lähdekoodin ohjelmia.
Paketinhallinta huolehtii pakettien välisistä
*riippuvuuksista*. Tämä tarkoittaa, että jos useampi ohjelmisto käyttäää samoja
ohjemistokomponentteja, eli jaettuja kirjastoja, ei kirjastoa tarvitse sisällyttää
näihin kaikkii paketteihin vaan kirjastosta voidaan muodostaa oma pakettinsa.
Ohjelmistoja asennettaessa, sen riippuvuutena tarvitsemat kirjastot asennetaan
myös. Paketit varastoidaan Linux-jakelun omalla palvelimella ja asennetaan
sieltä järjestelmän omilla työkaluilla.

Paketinhallinnan hyödyt
----------------------------------
Tämän lähestymistavan hyötynä on muun muassa keskitetty ohjelmavarasto sekä
*levytilan ja muistin säästyminen*, kun samoja toiminnallisuuksia ei tarvitse
tallentaa ja ladata muistiin erikseen jokaista sitä tarvitseevaa ohjelmaa
varten. Lisäksi ohjelmistoja asennettaessa tai päivitettäessä niiden *asennuspaketit
ovat pienempiä*, mikä säästää verkkokaistaa ja aikaa.

Varsinkin Linux-jakelun järjestelmäkomponenteille tämä paketointitapa
ja pakettien jakelu sopii hyvin.

Paketinhallinnan haasteet
--------------------------
Jaettujen kirjastopakettien käytön hankaluutena on se, että eri ohjelmistot on
pitänyt kääntää käyttämään *samaa jaetun kirjaston versiota*. Perinteisesti tämä
ei ole ollut Linux-järjestelmien mukana tulevien ohjelmien
kannalta suuri ongelma, koska paketinhallinnan kautta asennettavat ohjelmat ovat
olleet käytännössä kaikki avointa lähdekoodia ja jakelupaketin ylläpito on
hoitanut ohjelmien kääntämisen ja riippuvuuksien ratkomisen.

Suuremmaksi ongelmaksi ovat kuitenkin muodostuneet toisaalta *suljettua lähdekoodia*
olevien ja *kaupallisten ohjelmistojen* sekä *nopeasti kehittyvien* avoimen lähdekoodin
ohjelmien paketointi. Kun eri Linux-jakeluissa on ollut pohjalla eri versioita samoista
jaetuista kirjastoista, on ohjelmiston kehittäjä joutunut käytännössä kääntämään
ja paketoimaan ohjelmansa erikseen niille kaikille. Toisinaan Linux-käyttäjät
ovat tämän takia joutuneet tyytymään jakelun mukana paketoituun vanhempaan versioon.


Riippumattomat paketit
======================

Linux-jakeluissa uudempi tapa paketoida ja jakaa joitakin ohjelmistoja on
niiden paketointi "iteriittoisiksi" niin, että paketti sisältää kaikki tarvittavat
komponentit, eikä se riipu muista paketeista. Tämä sopii erityisesti
Linux-jakelun ulkopuolisten tahojen kehittämien ohjelmien jakelemiseen,
koska sama paketti toimii periaatteessa Linux-jakelusta ja sen versiosta riippumatta.

Tämä vastaa jonkin verran MacOS-järjestelmän tapaa asentaa ohjelmia.

Paketointitoteutuksia on useampia. Niiden välille löytyy erilaisia vertailuja, esimerkiksi:

- [TechNixin vertailu][TechNix]
- [AppImagen vertailu][AppImageComparison]

Snap
-----
Snap on kehitetty alkujaan Ubuntun palvelin-, puhelin- ja IoT-järjestelmiin,
mutta on nyt käytettävissä Ubuntun lisäksi myös monissa muissa jakeluissa.

Snap-pakettien jakeluun on keskitetty varasto, [Snapcraft],
josta asennustyökalu pystyy noutamaan paketteja.

Snap-paketoinnin tärkeitä ominaisuuksia ovat:

- Paketti sisältää kaiken tarvittavan, joten se ei riipu muista paketeista ja
  sama paketti sopii eri jakeluihin.
- Asentaminen ja päivitykset keskitetystä [pakettivarastosta][Snapcraft] asennustyökalulla
  ja automaattisesti.
- Päivitykset tapahtuvat osissa, jolloin koko pakettia ei tarvitse päivittää
  vaan vain muuttuvat osat.
- Laaja tuki eri Linux-järjestelmille ja useille eri ohjelmille.
- Snap-sovellukset voidaan suorittaa "hiekkalaatikossa" niin, että ne eivät
  pääse häiriköimään muuta järjestelmää. Tämä on tärkeää varsinkin, jos
  käytetään suljetun lähdekoodin ohjelmia, joiden toimintaa ei ole voitu tarkistaa.


AppImage
---------

AppImage eroaa Snap-paketoinnista siten, että yksi AppImage-ohjelma on käytännössä
yksi suoritettava tiedosto. Teknisesti AppImage on levykuva, joka sisältää
kaikki ohjelman suorittamiseen tarvittavat tiedostot sisällään. AppImage ehdoton
etu on siinä, että ohjelman kehittäjä voi antaa yhden tiedoston ladattavaksi ja
käyttäjä voi lataamisen jälkeen suorittaa sen ilman erillistä paketin purkamista.

AppImagen ominaisuuksia:

- Yksi suoritettava tiedosto, joka sisältää kaiken tarvittavan ei riippuvuuksia.
- Toimii kaikissa Linux-jakeluissa, joissa on tuki. (kaikissa merkittävimmissä)
- Ei pääkäyttäjän oikeuksia vaativaa asentamista.
- Ei keskitettyä pakettivarastoa, josta asennus ja päivitykset tapahtuisivat
  käsin tai automaattisesti.
- Uusi versio hankitaan lataamalla uusi tiedosto. Ei voi päivittää osissa.
- Samasta ohjelmasta voi olla rinnakkain useita versioita. (eri tiedostot)
- Helppo käyttää "portable"-ohjelmana, eli vaikka usb-tikulta.


flatpak
-------

Flatpak-paketoidut ohjelmat ovat edellisten tavoin jakeluriippumattomia.

Flatpakin ominaisuuksia ovat:

- Riippumattomat paketit
- Keskitetty pakettivarasto, [Flathub], josta ohjelmat ovat asennettavissa ja
  päivitettävissä.
- Mahdollisuus käyttää muitakin pakettivarastoja.
- Hyvä integroituvuus työpöytäympäristöihin.
- Tiukempi "hiekkalaatikko", joka estää sovellusta pääsemästä käsiksi muuhun
  järjestelmään, mutta voi joissain tilanteissa aiheuttaa käyttäjälle hankaluutta.



ZIP-paketit
===========

Kolmas tapa jakaa ohjemistoja on niiden jakaminen "raakana" **zip**-, **tar.gz**-
**tar.bz**-pakettina. Nämä ovat pelkkiä tiivistettyjä tiedostopaketteja ilman
mitään paketinhallinnallista toiminnallisuutta. Käyttäjä purkaa tiedoston
minne haluaa ja käyttää, miten haluaa. Paketin sisällä voi olla valmis
suoritettava ohjelmisto ja ohjeet tiedostojen asentamisesta tai kopioinnista
sopivaan paikkaan. Paketin sisällä voi vaihtoehtoisesti olla ohjelman
raaka lähdekoodi, joka täytyy kääntää ennen käyttöä.

Useimmiten on helpompaa asentaa ohjelmisto valmiina joko paketinhallinnan kautta
taikka riippumattomana pakettina.

[Snapcraft]: https://snapcraft.io/ (Snapcraft)
[Flathub]: https://flathub.org/home (Flathub)
[TechNix]: https://www.ostechnix.com/linux-package-managers-compared-appimage-vs-snap-vs-flatpak/ (Linux Package Managers Compared – Appimage vs Snap vs Flatpak)
[AppImageComparison]: https://github.com/AppImage/AppImageKit/wiki/Similar-projects#comparison (AppImage, Snap, Flatpak)
