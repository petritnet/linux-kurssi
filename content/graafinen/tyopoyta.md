---
date: "2016-09-06T22:42:04+03:00"
title: "Työpöytäympäristöt"
sectiontitle: "Graafinen käyttöliittymä"
weight: 240
---

{{< figure src="/images/Gnome-Ubuntu-desktop.png" link="/images/Gnome-Ubuntu-desktop.png" class="floatimage floatright" title="Ubuntun Gnome-työpöytä" >}}
{{< figure src="/images/Plasma-Kubuntu-desktop.png" link="/images/Plasma-Kubuntu-desktop.png" class="floatimage floatright" title="KDE Plasma" >}}
{{< figure src="/images/gnome-desktop.png" link="/images/gnome-desktop.png" class="floatimage floatright" title="Fedoran Gnome-työpöytä" >}}
{{< figure src="/images/Xfce-Xubuntu-desktop.png" link="/images/Xfce-Xubuntu-desktop.png" class="floatimage floatright" title="Xubuntun Xfce-työpöytä" >}}
{{< figure src="/images/LXQt-Lubuntu-desktop.png" link="/images/LXQt-Lubuntu-desktop.png" class="floatimage floatright" title="Lubuntun LXQt-työpöytä" >}}
{{< figure src="/images/mate-desktop.png" link="/images/mate-desktop.png" class="floatimage floatright" title="Mate" >}}
{{< figure src="/images/elementary-desktop.png" link="/images/elementary-desktop.png" class="floatimage floatright" title="Pantheon" >}}

Joitain vuosia sitten Linux-järjestelmissä oli perinteisten ikkunamanagerien
rinnalle työpöytäympäristöinä käytännössä kaksi vaihtoehtoa: KDE ja Gnome.
Kolmanneksi, kevyemmäksi, vaihtoehdoksi muodostui Xfce. KDE:n ja Gnomen
versiopäivitysten yhteydessä tapahtui suuria muutoksia, joihin kaikki eivät olleet
tyytyväisiä. Tässä vaiheessa ilmaantui lisää muutamia työpöytiä, joista ainakin
osa, esimerkiksi Mate, pyrki seuraamaan käyttöliittymässään aiempien versioiden
linjoja. Toisaalta, kilpailemaan ilmaantui myös aivan uusia, kuten Pantheon,
joka muistuttaa tyyliltään ja muotoilultaan jonkin verran Applen MacOS-järjestelmän
työpöytää.

Useista työpöytäympäristöistä on varaa valita omaa silmää ja tuntumaa miellyttävä:

* [Gnome](https://www.gnome.org/): GNU-projektin työpöytäympäristö, joka on myös Ubuntussa oletuksena käytössä.
* [KDE Plasma](https://www.kde.org/): KDE-yhteisön kehittämä työpöytä.
  Tyylikäs ja paljon säätövaraa, jolla sen voi kustomoida mieleisekseen. Pohjautuu Qt-käyttöliittymäkirjastoon.
* [Xfce](https://xfce.org): Kehitetty alunperin kevyeksi vaihtoehdoksi Gnomelle.
* [LXDE](https://lxde.org/) / [LXQt](https://lxqt.org): Kevyt työpöytäympäristö.
* [Cinnamon](https://en.wikipedia.org/wiki/Cinnamon_(software)): Alkujaan Linux Mint -jakeluun kehitetty työpöytä
* [Mate](https://mate-desktop.org/): Gnomen-työpöydän version 2 pohjalta kehitetty moderni, mutta kevyempi työpöytä.
* [Pantheon](https://en.wikipedia.org/wiki/Elementary_OS): ElmentaryOS-jakelua varten tehty työpöytä.






Ubuntu muilla työpöydillä
==============================

Ubuntusta on useita versioita, jotka koostuvat käytännössä samasta pohjajärjestelmästä,
mutta joissa asentuu oletuksena eri työpöytä.

* Ubuntu: Gnome-työpöytä
* Kubuntu: KDE Plasma-työpöytä
* Xubuntu: Xfce-työpöytä
* Lubuntu: LXQt-työpöytä

Yhdellä työpöydällä asennettuun Ubuntuun voi helposti asentaa myös toisen työpöytäympäristön
asentamalla sitä vastaavan paketin:

* Gnome: `ubuntu-desktop`
* KDE Plasma: `kubuntu-desktop`
* Xfce: `xubuntu-desktop`
* LXDE: `lubuntu-desktop`

Käynnistettävä työpöytä on valittavissa sisään kirjautumisen yhteydessä.







Tehtäviä
========================

{{% wrapper class="exercises" %}}

Tehtävät 7
==============================

Kokoa vastauksesi tiedostoon `tehtava-7.odt`.

1. Lisää Ubuntun sovellusvalikoimaan *Universe* -pakettilähde.<br>
   (Ubuntu Software -> Software & Updates -> Ubuntu Software -välilehti: rasti ruutuun kohtaan "Universe")<br>
2. Etsi ja nimeä Ubuntun ohjelmistovarastosta kaksi ikkunamanageria (window manager), joita ei mainittu edellä,
   ja joista toinen on tiilittävä (tiling).<br>
   (Tämän voi tehdä myös komentorivillä: `apt search <hakusanat>`).
3. Asenna jokin seuraavista: fvwm, wmaker, icewm, openbox
   * Minkä asensit?
4. Asenna Fluxbox *Sovellusvalikoimasta* tai komentoriviltä käsin komennolla:<br> `sudo apt install fluxbox`
5. Asenna myös xterm, ellei se ole jo asennettuna. (`sudo apt install xterm`)
6. Siirry tekstikonsoliin näppäinyhdistelmällä ctrl-alt-f2. Kirjaudu sisään<br>
   (Live-Ubuntussa käyttäjätunnus: `ubuntu`
   ja salasana tyhjä, eli pelkkä enter)
7. Käynnistä uusi X-istunto komennolla `xinit -- :1 vt2`<br>
   (Jos näppäimistöasettelu on amerikkalainen, `-` on `+` ja `:` on `ö`)
8. Käynnistä näkyviin tulevassa terminaali-ikkunassa Fluxbox komennolla: `fluxbox &`
9. Mistä löytyy Fluxboxin valikko? Saatko vaihdettua valikon kautta ikkunamanageriksi Wmakerin, Icewm:n tai Openboxin?
   (Minkä asensitkin aiemmassa kohdassa.)

{{% /wrapper %}}
