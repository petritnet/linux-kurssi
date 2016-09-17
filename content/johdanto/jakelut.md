+++
date = "2016-09-04T19:26:39+03:00"
title = "Linux-jakelut"
weight = 20
+++



Koska Linux on "vain" käyttöjärjestelmäydin, se tarvitsee seurakseen kokoelman
erilaisia, yleensä avointa lähdekoodia olevia, järjestelmäsovelluksia, käyttöliittymän sekä sovelluksia.
Linuxin ympärille on koottu useita *Linux-jakeluiksi* kutsuttuja ohjelmistokokoelmia.


Jakelut koostuvat Linux-ytimestä, järjestelmälle oleellisista ohjelmista, jostain (tai useammista) työpöytäjärjestelmistä
sekä käyttäjän käytettävissä olevista sovelluksista. Tyypillisesti jakelussa on kyse laitteelle asennuksen yhteydessä
järjestelmän ohella oletuksena asentuvasta kokoelmasta sovelluksia sekä tarjolla olevasta pakettivarastosta, josta
voidaan tarvittaessa asentaa muita avoimen lähdekoodin ohjelmia.

Tunnettuja jakeluita ovat esimerkiksi:

- Red Hat Enterprise Linux
- Debian
- Ubuntu
- Fedora
- CentOS
- OpenSUSE
- Linux Mint
- Elementary OS

Avoimuutensa ansiosta jakelut ovat usein jakautuneet jollain tavalla erikoistuneisiin versioihin aiemmista
jakeluista ja siksi ne muodostavat usein sukupuita.

* Debianista periytyy esimerkiksi Ubuntu. Ubuntusta on useita rinnakkaisia versioita (Kubuntu, Xubuntu, Lubuntu,...).
  Ubuntusta puolestaan periytyvät muun muassa Linux Mint ja ElementaryOS
* RedHatista periytyviä ovat OpenSUSE, Fedora, CentOS, Mageia




Live-CD / Live-DVD / Live-USB
==================================

Linux-jakeluiden asennusmediat ovat yleensä ladattavissa kunkin jakelun verkkosivujen kautta
`.iso`-päätteisenä levykuvatiedostona. Levykuva on suora kopio CD- tai DVD-levyn tiedostojärjestelmästä
yhtenä tiedostona ja sen voi kirjoittaa CD- tai DVD-levylle taikka USB-muistitikulle.

Levykuvasta luotu asennusmedia on tyypillisesti niin kutsuttu Live-levy, jolta voi käynnistää
toimivan Linux-järjestelmän työpöytineen. Järjestelmää voi käyttää suoraaln Live-levyltä
taikka asentaa sen tietokoneen kiintolevylle vakituista käyttöä varten.
Live-tilassa käynnistetty järjestelmä ei tee muutoksia tietokoneelle, ellei sitä erikseen
tahdo. Näin eri Linux-jakeluita ja niiden käyttöliittymien käyttötuntumaa on helppo kokeilla
asentamatta niitä pysyvästi.

Asennuslevyjen lisäksi on myös erityisesti Live-käyttöön tarkoitettuja jakeluita, jotka ovat
käteviä esimerkiksi vioittuneet tietokoneen korjaamiseen ja tietojen pelastamiseen.





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

