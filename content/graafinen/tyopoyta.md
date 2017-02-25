+++
date = "2016-09-06T22:42:04+03:00"
title = "Työpöytäympäristöt"
sectiontitle = "Graafinen käyttöliittymä"
weight = 230
+++

{{< figure src="/images/ubuntu-desktop-view.png" link="/images/ubuntu-desktop-view.png" class="floatimage floatright" title="Unity-työpöytä" >}}
{{< figure src="/images/kde-plasma-desktop.png" link="/images/kde-plasma-desktop.png" class="floatimage floatright" title="KDE Plasma" >}}
{{< figure src="/images/gnome-desktop.png" link="/images/gnome-desktop.png" class="floatimage floatright" title="Gnome" >}}
{{< figure src="/images/mate-desktop.png" link="/images/mate-desktop.png" class="floatimage floatright" title="Mate" >}}
{{< figure src="/images/elementary-desktop.png" link="/images/elementary-desktop.png" class="floatimage floatright" title="Pantheon" >}}
Linux-jakeluissa on tarjolla useita työpöytäympäristöjä:

* [Unity](http://unity.ubuntu.com/): Ubuntulle kehitetty työpöytä. Osittain samoja komponentteja kuin Gnomessa.
* [Gnome](http://www.gnome.org/): GNU-projektin työpöytäympäristö.
* [KDE Plasma](http://www.kde.org/): KDE-yhteisön kehittämä työpöytä.
  Tyylikäs ja paljon säätövaraa, jolla voi kustomoida mieleisekseen. Pohjautuu Qt-kirjastoon.
* [Xfce](http://xfce.org): Kehitetty alunperin kevyeksi vaihtoehdoksi Gnomelle.
* [LXDE](http://lxde.org/): Kevyt työpöytäympäristö.
* [Cinnamon](https://en.wikipedia.org/wiki/Cinnamon_(software)): Alkujaan Linux Mint -jakeluun kehitetty työpöytä
* [Mate](https://mate-desktop.org/): Gnomen-työpöydän version 2 pohjalta kehitetty moderni, mutta kevyempi työpöytä.
* [Pantheon](https://en.wikipedia.org/wiki/Elementary_OS): ElmentaryOS-jakelua varten tehty työpöytä.

Työpöytäympäristö on kokonaisuus, jossa ikkunamanagerin lisäksi mm. jotain seuraavista:

- panelit,
- työpöytäkuvakkeet,
- taustakuva,
- sovelmia,
- tiedostonhallinta,
- "raahaa ja pudota" -toiminnallisuus







Ubuntu muilla työpöydillä
==============================

Ubuntusta on useita versioita, jotka koostuvat käytännössä samasta pohjajärjestelmästä,
mutta joissa asentuu oletuksena eri työpöytä.

* Ubuntu: Unity-työpöytä
* Kubuntu: KDE Plasma-työpöytä
* Xubuntu: Xfce-työpöytä
* Lubuntu: LXDE-työpöytä

Yhdellä työpöydällä asennettuun Ubuntuun voi helposti asentaa myös toisen työpöytäympäristön
asentamalla sitä vastaavan paketin:

* Unity: `ubuntu-desktop`
* KDE Plasma: `kubuntu-desktop`
* Xfce: `xubuntu-desktop`
* LXDE: `lubuntu-desktop`

Käynnistettävä työpöytä on valittavissa sisään kirjautumisen yhteydessä.







Tehtäviä
========================

{{% wrapper class="exercises" %}}

Tehtävät 7
==============================

Palauta vastaukset tiedostona `tehtava-7.odt`.

1. Lisää Ubuntun sovellusvalikoimaan *Universe* -pakettilähde.<br>
   (Ubuntu Software -> Software & Updates -> Ubuntu Software -välilehti: rasti ruutuun kohtaan "Universe")<br>
2. Etsi ja nimeä Ubuntun ohjelmistovarastosta kaksi ikkunamanageria (window manager), joita ei mainittu edellä,
   ja joista toinen on tiilittävä (tiling).<br>
   (Tämän voi tehdä myös komentorivillä: `apt-cache search <hakusanat>`).
3. Asenna jokin seuraavista: wmaker, icewm, openbox
   * Minkä asensit?
4. Asenna Fluxbox *Sovellusvalikoimasta* tai komentoriviltä käsin komennolla:<br> `sudo apt-get install fluxbox`
5. Asenna myös xterm, ellei se ole jo asennettuna. (`sudo apt-get install xterm`)
6. Siirry tekstikonsoliin näppäinyhdistelmällä ctrl-alt-f1. Kirjaudu sisään<br>
   (Live-Ubuntussa käyttäjätunnus: `ubuntu`
   ja salasana tyhjä, eli pelkkä enter)
7. Käynnistä uusi X-istunto komennolla `xinit -- :1 vt1`<br>
   (Jos näppäimistöasettelu on amerikkalainen, `-` on `+` ja `:` on `ö`)
8. Käynnistä näkyviin tulevassa terminaali-ikkunassa Fluxbox komennolla: `fluxbox &`
9. Mistä löytyy Fluxboxin valikko? Saatko vaihdettua valikon kautta ikkunamanageriksi Wmakerin, Icewm:n tai Openboxin?
   (Minkä asensitkin aiemmassa kohdassa.)

{{% /wrapper %}}
