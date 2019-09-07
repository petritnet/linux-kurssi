+++
date = "2016-09-04T19:26:39+03:00"
title = "Linux-jakelut"
weight = 30
+++


Linux-jakelu
==================================

Linux-järjestelmiä on tarjolla useina erilaisina jakelupaketteina.
Ne koostuvat Linux-ytimestä, järjestelmälle oleellisista ohjelmista, jostain (tai useammista) työpöytäjärjestelmistä sekä sovelluksista

Tunnettuja jakeluita ovat esimerkiksi:

- [Red Hat Enterprise Linux][RHEL]
- [Debian]
- [Ubuntu]
- [Fedora]
- [CentOS]
- [OpenSUSE]
- [Linux Mint]
- [Elementary OS]

Jakeluista muodostuu sukupuita, koska ne ovat yleensä muunnoksia jostain
aiemmasta jakelusta. Esimerkiksi:

* Debianista periytyy mm. Ubuntu.
* Ubuntusta useita versioita (Kubuntu, Xubuntu, Lubuntu,...).
* Ubuntusta periytyy mm. Linux Mint ja ElementaryOS




Live-CD / Live-DVD / Live-USB
==================================

* CD- tai DVD-levy, jolta voi käynnistää toimivan Linux-järjestelmän
* Käytettävissä kuin kiintolevyltä paitsi:
    * CD-/DVD-levyillä tallennukset eivät säily, ellei erikseen siirrä esim. usb-tikulle.
    * Asennetut ohjelmat eivät säily.
* Voidaan tehdä myös live-USB-tikkuja
    * USB-tikulla voi olla käytössä "permanent-osio", jolle tiedostot ja asetukset tallentuvat.

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

Live-levyltä järjestelmä on käytettävissä kuin kiintolevyltä paitsi:


* Tallennukset eivät säily, ellei erikseen siirrä esim. USB-tikulle tai ellei Live-USB:hen ole lisätty tehtyjä muutoksia muistava *persistent*-ominaisuus.
* Asennetut ohjelmat eivät säily



Kurssin Live-USB -levyltä löytyvät jakelut
==================================

Kurssin yhteydessä saattaa olla käytössä Live-USB-tikku, jolta löytyvät
esimerkiksi seuraavat jakelut.

{{< figure src="/images/usb-memory.svg" class="floatright floatimage" >}}

* Ubuntu (Gnome-työpöytä)
* Kubuntu (Plasma-työpöytä)
* Xubuntu (XFCE-työpöytä)
* Lubuntu (LXDE/LXQT-työpöytä)
* Linux Mint (Cinnamon-työpöytä)
* Linux Mint (Mate-työpöytä)
* ElementaryOS (Pantheon-työpöytä)
* Fedora (Gnome-työpöytä)
* System Rescue CD
* Clonezilla

Kaikki levyllä olevat jakelut ovat 64-bittisiä versioita ja käynnistys vaatii EFI-käynnistyksen.



Työpöytiä
==================================

Aiemmin tarjolla oli työpöytäympäristöiksi lähinnä kaksi vaihtoehtoa: *KDE* ja *Gnome*.
GTK-käyttöliittymäkirjastoon perustuva Gnome oli vastaus KDE:hen, joka perustuu Qt-kirjastoon, joka ei aluksi ollut
joidenkin mielestä "tarpeeksi vapaa".

Työpöydän ominaisuuksia:

* Ohjelmia, joilla yhtenäinen samaa tyyliä oleva ulkoasu
   * Ikonit, ikkunat, työkalupalkit, paneelit, "widgetit" eli sovelmat
* Työpöytä-metafora, taustakuva
* Drag-n-drop (raahaa ja pudota) ohjelmien välillä
* Erinäisiä muita yhteisiä palveluita, joita ohjelmat voivat käyttää.
  Esimerkiksi ilmoitukset (notifikaatiot).

KDE:n ja Gnomen rinnalle tuli tarjolle kevyempi vaihtoehto, *Xfce*, joka käyttää
Gnomen tapaan myös GTK-kirjastoa.

Moni alkoi kysyä, miksi kehitetään useampaa työpöytäympäristöä.
Miksi ei yhdistetä voimia yhden tekemiseen?

Vastauksena työpöytäympäristöjen määrä moninkertaistui:

* **KDE Plasma**
* **Gnome**
* **Xfce** (kevyempi vaihtoehto Gnomelle)
* **Cinnamon** (Linux Mintin vaihtoehto Gnomelle)
* **LXDE** (kevyt työpöytävaihtoehto)
* **MATE** (edelleen kehitetty versio vanhemmasta Gnome 2 -työpöydästä)
* **Pantheon desktop** (Elementary OS:n työpöytä)
* **Trinity desktop** (KDE:n 3.x-versioihin perustuva vaihtoehto)
* **Razor-qt** / **LXQt** (kevyempi vaihtoehto Plasmalle)
* **Enlightenment**

Nyt työpöytävaihtoehtoja on jo paljon.
Moni niistä syntyi, kun KDE ja Gnome siirtyivät seuraavaan versioonsa ja osa
käyttäjistä/kehittäjistä ei tykännyt uudesta suunnata/tyylistä.



Hajaannus vai integrointi
==================================

Monen mielestä ei ole hyvä, että pirstaloidutaan useaan erilaiseen työpöytäymäristöön,
jotka toteuttavat samoja asioita.

> "Menee resursseja hukkaan, kun rakennetaan samaa pyörää uudelleen ja uudelleen"

Toisaalta, on hyvä, että kehitys tapahtuu tutkivasti moneen eri suuntaan yhtä aikaa

* "Veitsenteräkehityksen" takana tapahtuu kokoajan myös standardointia
* Parhaimmat toiminnallisuudet ja ideat jäävät eloon ja kopioituvat muihinkin työpöytiin
* Tehdään yhteisiä taustatoiminnallisuuksia, joihin työpöytäympäristöt toteuttavat
  vain käyttöliittymän oman tyylinsä mukaisesti.


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
  Tämä ei valitettavasti ole mainittavasti edennyt.

Tiedostohallinnat:

* Eri työpöydillä on omat tiedostohallintaohjelmansa
* Pieniä eroja esim. toiminnoissa ja keveydessä/raskaudessa
* Käyttöliittymän ulkoasut kuitenkin hioutuneet melko samanlaisiksi



Virtuaalityöpöydät
==================================
Virtuaalityöpöydät tai workspacet olivat käytössä ikkunamanagereissa jo ennen
työpöytäympäristöjä

* Nykyään käytettävissä kaikissa (Unix-tyyppisissä) työpöytäympäristöissä mukaan
  lukien MacOS.
* Osassa kiinteä käyttäjän valitsema määrä työpöytiä, osassa määrä kasvaa ja
  pienenee dynaamisesti käytön mukaan.
* Rivissä tai ruudukkona
* Erilaisia visualisointeja:
    * Kun 3D-efektit tulivat käyttöön, oli jonkin aikaa muotia laittaa työpöydät
      kuution sivuille ja animoida työpöydän vaihto kuutiota kääntämällä.



Kaikki avoimet ikkunat näyttävä näkymä
==================================
Mac OS X esitteli Exposén, eli näkymän, jossa kaikki avoimet ikkunat skaalataan
näkymään rinnakkain ikkunan valintaa varten.

* Toiminto ilmestyi myös suureen osaan vapaita työpöytäympäristöjä.
* Useita versioita:
    * Näytä kaikki ikkunat tällä työpöydällä
    * Näytä kaikki ikkunat kaikilla työpöydillä
    * Näytä kaikki työpöydät ruudukkona ja kaikki ikkunat niillä



Kokeile!
==================================
Kokeile eri jakeluita käynnistämällä kone USB-levyltä.
Käynnistäminen vaatii, että valitaan tietokoneen käynnistäminen kiintolevyn
sijaan ulkoiselta levyltä.

Esimerkiksi Lenovo ThinkCentre -koneissa:

* Paina *Enter*, kun näkyy Lenovon logo ja teksti "ThinkCentre"
* Valitse *F12* eli "valitse väliaikainen käynnistysmedia"
* Valitse USB-levy
* Seuraavasta valikosta valitse käynnistettäväksi haluamasi järjestelmä
* **Älä asenna koulun koneelle!**

Huom! SystemRescueCD ja Clonezilla ovat ylläpito- ja pelastustyökaluja, joita tarkastellaan myöhemmin kurssilla


Tehtäviä
==================================

{{% wrapper class="exercises" %}}
Tehtävät 2
==================================

Kuvakaappauksen voi ottaa *PrintScreen*-näppäimellä. Tiedostot voit tallentaa/kopioida
erilliselle USB-tikulle tai lähettää ne itsellesi sähköpostilla.

Kirjoita tekstinkäsittelyohjelmalla tiedosto `tehtava-2.odt`, jossa
ovat seuraavat vastaukset ja kuva.

1. Nimesi ja päivämäärä
2. Mikä ero on Mintin Cinnamonin ja Elementary OS:n tavoilla käsitellä virtuaalityöpöytiä?
3. Minkä nimiset tiedostonhallintaohjelmat ovat käytössä seuraavista työpöytäympäristöissä?
    1. Unity (Ubuntu)
    2. Cinnamon (Linux Mint)
    3. KDE (Kubuntu)
    4. LXDE (Lubuntu)
    5. Pantheon (Elementary OS)
4. Ota kuvakaappaus seuraavien ohjeiden mukaan:
    1. Vaihda Ubuntun taustakuvaksi valitsemasi kuva ja ota työpöydästä kuvakaappaus.
    2. Tallenna kuvakaappaus muistitikulle.
    3. Käynnistä jokin toinen Linux-jakelu, vaihda taustakuva, avaa muistitikulta äskeinen kuvakaappaus näkymään ikkunaan ja ota kuvakaappaus.
    4. Tallenna uusi kuvakaappaus myös tikulle.
    5. Käynnistä vielä kolmas Linux-jakelu ja tee sama.
    6. Palauta tämä kolmas kuvakaappaus, jossa näkyvät kaikki kolme työpöytää.

{{% /wrapper %}}

[RHEL]: https://redhat.com/rhel "Red Hat Enterprise Linux"
[Fedora]: https://getfedora.org/ "Fedora"
[CentOS]: https://www.centos.org/ "CentOS"
[Debian]: https://www.debian.org/ "Debian"
[Ubuntu]: https://ubuntu.com/ "Ubuntu"
[Linux Mint]: https://www.linuxmint.com/ "Linux Mint"
[Elementary OS]: https://elementary.io/ "Elementary OS"
[openSUSE]: https://www.opensuse.org/ "openSUSE"
