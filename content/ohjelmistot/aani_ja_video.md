---
date: "2017-03-02T20:38:27+03:00"
title: "Ääni ja video"
weight: 340
---

Multimedian, eli äänen ja videon, soittamiseen, näyttämiseen ja muokkaamiseen on tarjolla
useita ohjelmia. Osa on käyttöliittymältään suunnattu erityisesti jollekin työpöydälle, mutta
ohjelmat toimivat luonnollisesti myös toisillakin työpöydillä.

Osa, kuten VLC, on myös Windows-maailmassa tuttuja sovelluksia.

Musiikkisoittimet
===============================

Suosittuja musiikkisoittimia ovat muun muassa

* Rhythmbox (Ubuntun oletussoitin)
* Banshee
* Amarok (KDE)
* Clementine

Lisäksi Linuxille on asennettavissa myös muun muassa [Spotify]-sovellus verkosta streamatun musiikin
kuuntelemiseen.





Videotoistimet
===============

Videoita voi katsella ainakin seuraavilla sovelluksilla:

* VLC
* Totem
* Parole Media Player
* Dragon


Osa ohjelmistoista voi vaatia multimediakoodekkien asentamisen joidenkin
tiedostomuotojen (ääni tai video) toistamiseen.

Patenttien rajoittamia koodekeja voi asentaa aktivoimalla "multiverse"-pakettivaraston
ja asentamalla paketin `ubuntu-restricted-extras` komennolla:

```bash
sudo apt install ubuntu-restricted-extras
```



Äänen muokkaus
===============

Äänen tallentamiseen ja muokkaamiseen Linuxissa voidaan käyttää Windowsistakin
tuttua avoimen lähdekoodin Audacity-ohjelmaa. Sen voi asentaa suoraan
pakettivarastosta komennolla:

```bash
sudo apt install audacity
```

Audacity löytyy myös snap-pakettina, joka saattaa olla versioltaan uudempi.

```bash
sudo snap install audacity
```


Videoeditointi ja -muunnos
===============================

Videoiden editointi löytyy useampi leikkausohjelma:

* OpenShot
* Pitivi
* Kdenlive

Videoiden muuntaminen muodosta toiseen tai esimerkiksi DVD-levyltä tiedostoksi onnistuu
Handbrake-ohjelmalla ja joitain muunnoksia voi tehdä myös Avidemux-ohjelmalla.

[OpenShot]-ohjelmasta kannattaa ladata tuorein saatavilla oleva versio
AppImage-muodossa sen omalta sivustolta.



[Spotify]: https://www.spotify.com/fi/download/linux/ (Spotify for Linux)
[OpenShot]: https://www.openshot.org/ (OpenShot)
