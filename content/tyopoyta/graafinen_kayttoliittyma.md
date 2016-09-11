+++
date = "2016-09-06T22:42:04+03:00"
title = "Graafinen käyttöliittymä"
weight = 8
+++

Modulaarisuus
==============================

Unixeissa on perinteisesti yritetty välttää monoliittisten ohjelmien tekemistä.

* Modulaarisia pieniä ohjelmia, joita voi yhdistellä
* vaihtoehtoisia osia samaan käyttöön
* sekä komentorivillä että graafisessa käytössä




X-ikkunointi
==============================

* [X Window System](http://en.wikipedia.org/wiki/X_Window_System), eli X11
* Linuxissa nykyisin toteutuksena [X.org](http://www.x.org/wiki/)
* Toteuttaa ikkunoinnin asiakas-palvelin -periaatteella
    * käytettävä ohjelma on asiakas (pyytää: "piirrä ruudulle ikkuna, jossa...",
      "ota vastaan näppäimen painallukset ja hiiren liikkeet")
    * X on palvelin (toteuttaa asiakkaan pyynnöt)
* Verkkoläpinäkyvä, eli asiakas ja palvelin voivat olla eri koneilla.
* Välikerros, joka vain toimii käyttäjän ohjelmien ja näytön (output) ja syöttölaitteiden (input) välillä.



X-ikkunointi: kokeillaan
==============================

Käynnistetään X minimaalisimmillaan seuraavasti:

1. Linuxin tekstitilaan, eli virtuaaliterminaaliin, painamalla `ctrl-alt-f1`.
    * (Virtuaaliterminaaleja yleensä 6 kpl. f1-f6)
2. Kirjaudutaan sisään käyttäjätunnuksella ja salasanalla.
3. Käynnistetään uusi X komennolla: `xinit -- :1`
    * Jo käynnissä oleva X on numero 0. (`:0`)
4. Käynnistyy X ilman taustakuvaa, ikkunoidenhallintaa tai mitään muuta.
   Vain *xterm*-pääteikkuna ja rastimainen hiiren kursori.

Aiempi X saatavilla esiin näppäilemällä `ctrl-alt-f7` ja "uusi X" näppäilemällä `ctrl-alt-f8`.
Poistuminen: kirjoittamalla `exit` *xterm*-ikkunaan.




Ikkunamanageri
==============================

Ikkunoiden hallinta (siirtely, koon muuttaminen, pinoaminen päällekkäin yms.) tapahtuu erillisellä
[ikkunamanagerilla](http://en.wikipedia.org/wiki/X_window_manager), joita on monia.

* Graafisesti näyttäviä 3d-efekteillä
* kevyempiä perusikkunamanagerita (Icewm, Windowmaker, Enlightenement (E17),...)
* "Tiilittäviä" ikkunamanagereita (Xmonad, Subtle, Ion, Ratpoison, Wmii,...)

Jotkut ikkunamanagerit osa suurempaa työpöytäympäristöä, joka sisältää työpöydän, panelit, sovelmat, jne. (Gnome, KDE, Unity, XFCE, LXDE, Cinnamon, MATE,...)




Ikkunamanageri: kokeillaan
==============================

1. Asennetaan muutama ikkunamanageri, esim.: icewm, windowmaker, ratpoison, openbox
    * `sudo apt-get install icewm`
2. Käynnistetään tyhjä X ja sinne esim. icewm kirjoittamalla *xterm*-ikkunaan: `icewm`
3. Kokeillaan ikkunamanagerin toimintaa, suljetaan se ja kokeillaan muita.

Vaihtoehtoisia ikkunamanagereja voi käyttää myös varsinaisessa X:ssä Unityn tilalla:

* Kirjaudutaan ulos työpöydältä
* Valitaan käyttöliittymäksi Unityn sijasta joku muu vaihtoehdoista
* Kirjaudutaan sisään




Työpöytäympäristöt
==============================

Tarjolla useita työpöytäympäristöjä: Unity, Gnome, KDE, Xfce, LXDE

* Työpöytäympäristö on kokonaisuus, jossa ikkunamanagerin lisäksi mm. jotain seuraavista:
    * panelit, työpöytäkuvakkeet, taustakuva, sovelmia, tiedostonhallinta, "raahaa ja pudota" -toiminnallisuus
* [Unity](http://unity.ubuntu.com/): Ubuntulle kehitetty työpöytä. Osittain samoja komponentteja kuin Gnomessa.
* [Gnome](http://www.gnome.org/): GNU-projektin työpöytäympäristö.
* [KDE](http://www.kde.org/): KDE-yhteisön kehittämä työpöytä. Tyylikäs ja paljon säätöjä. Pohjautuu Qt-kirjastoon.
* [Xfce](http://xfce.org): Kehitetty alunperin kevyeksi vaihtoehdoksi Gnomelle.
* [LXDE](http://lxde.org/): Kevyt työpöytäympäristö.




Ubuntu muilla työpöydillä
==============================

Ubuntusta on useita versioita, jotka ovat käytännössä sama järjestelmä, mutta oletuksena asentuu eri työpöytä.

* Ubuntu: Unity-työpöytä
* Kubuntu: KDE-työpöytä
* Xubuntu: Xfce-työpöytä
* Lubuntu: LXDE-työpöytä

Yhdellä työpöydällä asennettuun Ubuntuun voi helposti asentaa myös toisen työpöytäympäristön
asentamalla sitä vastaavan paketin:

* Unity: `ubuntu-desktop`
* KDE: `kubuntu-desktop`
* Xfce: `xubuntu-desktop`
* LXDE: `lubuntu-desktop`

Käynnistettävä työpöytä on valittavissa sisään kirjautumisen yhteydessä.





Uudet vaihtoehdot X:lle
==============================

* [Wayland](http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29)
   * X.org:in kehittäjien uusi parempi vaihtoehto
   * X:ssä historian painolastia ja "aivovammoja"
   * Jo käytössä muun muassa Jollan SailfishOS-käyttöjärjestelmässä.
* Mir
   * Canonicalin/Ubuntun vaihtoehto X:lle
   * Ovat kehittäneet muun muassa Ubuntu Phonea silmällä pitäen
   * Herättänyt jonkin verran kiistaa "sooloilulla" sen sijaan, että olisivat tukeneet Waylandin kehitystä.




Tehtävät
==============================

Palauta vastaukset Moodleen tiedostona `vastaus-6.odt`.

1. Lisää Ubuntun ohjelmavarastoon *Universe* -pakettilähde.
   (Ubuntu Software Center -> Edit -> Software Sources: rasti ruutuun kohtaan "Universe")
2. Etsi ja nimeä Ubuntun ohjelmistovarastosta kaksi ikkunamanageria (window manager),
   joita ei mainittu edellä, ja joista toinen on tiilittävä (tiling).
3. Asenna jokin seuraavista: wmaker, icewm, openbox
   * Minkä asensit?
4. Asenna Fluxbox *Software Centeristä* tai komentoriviltä komennolla: `sudo apt-get install fluxbox`
5. Asenna myös xterm, ellei se ole jo asennettuna `sudo apt-get install xterm`
6. Siirry tekstikonsoliin näppäinyhdistelmällä ctrl-alt-f1.
7. Käynnistä uusi X-istunto komennolla `xinit -- :1`
8. Käynnistä näkyviin tulevassa terminaali-ikkunassa Fluxbox komennolla: `fluxbox &`
9. Mistä löytyy Fluxboxin valikko? Saatko vaihdettua valikon kautta ikkunamanageriksi Wmakerin, Icewm:n tai Openboxin?
   (Minkä asensitkin aiemmassa kohdassa.)
