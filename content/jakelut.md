+++
date = "2016-09-04T19:26:39+03:00"
title = "Jakelut"
weight = 3
+++



Linux-jakelu
==================================
* Useita erilaisia jakelupaketteja
* Koostuvat Linux-ytimestä, järjestelmälle oleellisista ohjelmista, jostain (tai useammista) työpöytäjärjestelmistä sekä sovelluksista
* Muodostavat usein sukupuita:
    * Debianista periytyy mm. Ubuntu. Ubuntusta useita versioita (Kubuntu, Xubuntu, Lubuntu,...). Ubuntusta periytyy mm. Linux Mint ja ElementaryOS
    * RedHatista periytyviä OpenSUSE, Fedora, CentOS, Mandriva,...




Live-CD / Live-DVD
==================================
* CD- tai DVD-levy, jolta voi käynnistää toimivan Linux-järjestelmän
* Käytettävissä kuin kiintolevyltä paitsi:
    * Tallennukset eivät säily, ellei erikseen siirrä esim. usb-tikulle
    * Asennetut ohjelmat eivät säily
* Voidaan tehdä myös live-usb-tikkuja



DVD-levyltä löytyvät jakelut
==================================
* Linux Mint 17.1 (Cinnamon-työpöytä)
* Ubuntu 14.10 (Unity-käyttöliittymä)
* Kubuntu 14.10 (KDE-työpöytä)
* Lubuntu 14.10 (LXDE-työpöytä)
* ElementaryOS Luna
* Fedora 21
* Damn Small Linux
* System Rescue CD
* Clonezilla
* TinyCore
Kaikki levyllä olevat jakelut ovat 64-bittisiä versioita.



Työpöytiä
==================================
* KDE
* Gnome
Varsinaisia työpöytäympäristöjä oli ensin tarjolla nämä kaksi.
Gtk-käyttöliittymäkirjastoon perustuva Gnome oli vastaus KDE:hen, joka perustuu Qt-kirjastoon, joka ei aluksi ollut "tarpeeksi vapaa".

Työpöydän ominaisuuksia:

* Ohjelmia, joilla yhtenäinen ulkoasu
   * Ikonit, ikkunat, työkalupalkit, paneelit, "widgetit" eli sovelmat
* Työpöytä-metafora, taustakuva
* Drag-n-drop (kommunikointi) ohjelmien välillä



Työpöytiä
==================================
* KDE
* Gnome
* Xfce
    * Kevyempi vaihtoehto Gnomelle. Käyttää myös gtk-kirjastoa.
Moni alkoi kysyä, miksi kehitetään useampaa työpöytäympäristöä. Miksi ei yhdistetä voimia yhden tekemiseen?



Työpöytiä
==================================
* KDE 4
* Gnome 3
* Xfce
    * Kevyempi vaihtoehto Gnomelle. Käyttää myös gtk-kirjastoa.
* Unity
    * Ubuntun oma käyttöliittymä Gnome 3 -työpöytään
* Cinnamon
    * Linux Mintille kehitetty työpöytä
* LXDE
    * Kevyt työpöytävaihtoehto
* MATE
    * Edelleen kehitetty versio Gnome 2 -työpöydästä
* Pantheon desktop
    * Elementary OS:n työpöytä. Käyttää gtk-kirjastoa.
* Trinity desktop
    * KDE:n 3.x-versioihin perustuva vaihtoehto KDE:lle.
* Razor-qt
    * Kevyempi vaihtoehto KDE:lle. Käyttää myös Qt-kirjastoa.
* Enlightenment

Nyt työpöytävaihtoehtoja on jo paljon.
Moni niistä syntyi, kun KDE ja Gnome siirtyivät seuraavaan major-versioonsa ja osa käyttäjistä/kehittäjistä ei tykännyt uudesta suunnata/tyylistä.



Hajaannus vai integrointi
==================================
Monen mielestä ei ole hyvä, että pirstaloidutaan useaan erilaiseen työpöytäymäristöön, jotka toteuttavat samoja asioita.

* "Menee resursseja hukkaan, kun rakennetaan samaa pyörää uudelleen ja uudelleen"

Toisaalta, on hyvä, että kehitys tapahtuu tutkivasti moneen eri suuntaan yhtä aikaa

* "Veitsenteräkehityksen" takana tapahtuu kokoajan myös standardointia
* Parhaimmat toiminnallisuudet jäävät eloon ja kopioituvat muihinkin työpöytiin
* Tehdään yhteisiä taustatoiminnallisuuksia, joihin työpöytäympäristöt toteuttavat vain käyttöliittymän oman tyylinsä mukaisesti.


Esimerkkejä
==================================
Pikaviestintä:

* Useita pikaviestimiä sekä KDE:lle että Gnomelle
* Viimeisimpänä suuntana yhteinen Telepathy-kirjasto, joka hoitaa viestiliikenteen ja sille on erilaisia käyttöliittymiä: Empathy (Gnome), KDE Telepathy (KDE)

Salasanasäilöt:

* Gnomella oma keyring, KDE:llä wallet
* Osa ohjelmista käyttää toista, osa toista
* Toinen integroituu käytettyyn työpöytään, toinen ei
* Kehitteillä yhteinen backend, johon työpöytäympäristöt toteuttavat käyttöliittymän.

Tiedostohallinnat:

* Eri työpöydillä on omat tiedostohallintaohjelmansa
* Pieniä eroja esim. toiminnoissa ja keveydessä/raskaudessa
* Käyttöliittymän ulkoasut kuitenkin hioutuneet melko samanlaisiksi



Virtuaalityöpöydät
==================================
Virtuaalityöpöydät/workspacet olivat käytössä ikkunamanagereissa jo ennen työpöytäympäristöjä

* Nykyään käytännössä kaikissa (Unix-tyyppisissä) työpöytäympäristöissä.
* Osassa kiinteä käyttäjän valitsema määrä työpöytiä, osassa dynaamisesti kasvava ja pienenevä määrä
* Rivissä tai ruudukkona
* Erilaisia visualisointeja:
    * Kun 3D-efektit tulivat käyttöön, oli jonkin aikaa muotia laittaa työpöydät kuution sivuille



Kaikki avoimet ikkunat näyttävä näkymä
==================================
Mac OS X esitteli Exposén, eli näkymän, jossa kaikki avoimet ikkunat skaalataan näkymään rinnakkain ikkunan valintaa varten.

* Toiminto ilmestyi myös suureen osaan vapaita työpöytäympäristöjä.
* Useita versioita:
    * Näytä kaikki ikkunat tällä työpöydällä
    * Näytä kaikki ikkunat kaikilla työpöydillä
    * Näytä kaikki työpöydät ruudukkona ja kaikki ikkunat niillä



Kokeile!
==================================
Kokeile eri jakeluita käynnistämällä kone DVD-levyltä.
Käynnistäminen vaatii, että valitaan tietokoneen käynnistäminen kiintolevyn sijaan cd/dvd-levyltä.
ICT1-luokan koneissa:

* Paina //Enter//, kun näkyy Lenovon logo ja teksti "ThinkCentre"
* Valitse //F12// eli "valitse väliaikainen käynnistysmedia"
* Valitse //CD/DVD-levy//
* Seuraavasta valikosta valitse käynnistettävä järjestelmä

Huom! SystemRescueCD ja Clonezilla ovat ylläpito- ja pelastustyökaluja, joita tarkastellaan myöhemmin kurssilla


Tehtäviä
==================================
Tehtävät ovat vastattavissa kurssin Moodle-sivuilla.

Kuvakaappauksen voi ottaa *PrintScreen*-näppäimellä. Tiedostot voit tallentaa/kopioida erilliselle usb-tikulle, Ubuntu One -palveluun tai lähettää ne itsellesi sähköpostilla.

1. Mikä ero on Cinnamonin ja Elementary OS:n tavoilla käsitellä virtuaalityöpöytiä?
1. Minkä nimiset tiedostonhallintaohjelmat ovat käytössä seuraavista työpöytäympäristöissä?
    1. Unity (Ubuntu)
    1. Cinnamon (Linux Mint)
    1. KDE (Linux Mint, Kubuntu)
    1. LXDE (Lubuntu)
    1. Pantheon (Elementary OS)
1. Ota kuvakaappaus seuraavien ohjeiden mukaan:
    1. Vaihda Ubuntun taustakuvaksi valitsemasi kuva ja ota työpöydästä kuvakaappaus.
    1. Tallenna kuvakaappaus muistitikulle.
    1. Käynnistä jokin toinen Linux-jakelu DVD:ltä, vaihda taustakuva, avaa muistitikulta äskeinen kuvakaappaus näkymään ikkunaan ja ota kuvakaappaus.
    1. Tallenna uusi kuvakaappaus myös tikulle.
    1. Käynnistä vielä kolmas Linux-jakelu ja tee sama.
    1. Palauta tämä kolmas kuvakaappaus, jossa näkyvät kaikki kolme työpöytää.

