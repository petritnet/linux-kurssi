---
date: "2017-02-25T18:30:04+03:00"
title: "Ikkunamanagerit"
sectiontitle: "Graafinen käyttöliittymä"
weight: 230
---


{{< figure src="/images/fvwm2.jpg" link="/images/fvwm2.jpg" class="floatimage floatright" title="FVWM2" caption="Vanhempi ja 'alkeellisempi' ikkunanhallintaohjelma FVWM2." >}}
{{< figure src="/images/enlightenment.jpg" link="/images/enlightenment.jpg" class="floatimage floatright" title="Enlightenment (E17)" caption="Modernimpi Enlightenment-ikkunamanageri" >}}
{{< figure src="/images/wmii.jpg" link="/images/wmii.jpg" class="floatimage floatright" title="Wmii" caption="Tiilittävä Wmii-ikkunamanageri" >}}

Ikkunoiden hallinta, eli niiden siirtely, koon muuttaminen, pinoaminen päällekkäin sekä muu
vastaava, tapahtuu erillisellä
[ikkunamanagerilla](http://en.wikipedia.org/wiki/X_window_manager).

{{% wrapper class="theorybox" %}}
Ikkunamanagerin tehtävät
========================
Ikkunamanageri piirtää ikkunoille kehykset ja mahdollistaa:

- ikkunoiden siirtelyyn
- ikkunoiden koon muuttamiseen
- ikkunoiden päällekkäisen järjestyksen hallinnan
- ikkunoiden luetteloinnin
- valikot ohjelmien käynnistämiseen
{{% /wrapper %}}


Näitä on monia ja ne voivat olla sekä ulkoasultaan, toiminnallisuuksiltaan että
tuntumaltaan hyvinkin erilaisia.

* Graafisesti näyttäviä 3d-efekteillä
* kevyempiä perusikkunamanagerita
* "Tiilittäviä" ikkunamanagereita

Perinteiset Ikkunamanagerit
============================

Perinteisesti ikkunamanagerit hoitivat "root"-ikkunan eli käytännössä
taustakuvan näyttämisen, ikkunoiden hallinnan sekä taustaa klikkaamalla esiin
tulevien ohjelma- ja ikkunavalikoiden näyttämisen. Ikkunamanageriin saattaa
liittyä myös erilaisia paneleita ja useampien näkymien ("workspace").

Perinteisiä ikkunamanagerieita ovat muun muassa: TWM, Fvwm, Fvwm2, Windowmaker,
Icewm, Enlightenment (E17), Openbox ja Fluxbox.

Työpöytäympäristöt
==================

Työpöytäympäristöt ovat yleensä suurempia ohjelmistokokonaisuuksia. Niissä yhtenä
osana on jokin ikkunamanageri, mutta sen lisäksi on yleensä paneleita ja sovelmia,
työpöytäkuvakkeita, taustakuvia ja teemoitusta, työkaluohjelmia, kuten tiedostohallinta,
järjestelmän ilmoitukset, "raahaa ja pudota"-toiminnallisuus, keskitetyt asetukset
sekä keinot tehdä tyyliltään ja toiminnoiltaan yhteneväisiä ohjelmia.

Linux-järjestelmissä on tyypillisesti tarjolla useita työpöytäympäristöjä.
Esimerkiksi: Gnome, KDE Plasma, Xfce, LXDE/LXQt, Cinnamon, Mate ja Pantheon

Tiilittävät ikkunamanagerit
===========================

[Tiilittävillä ikkunamanagereilla](https://en.wikipedia.org/wiki/Tiling_window_manager)
tarkoitetaan ikkunoiden hallintaan käytettäviä ohjelmia, jotka pyrkivät tarkoituksellisesti
välttämään ikkunoiden asettelemista päällekkäin. Tämä tapahtuu yleensä siten, että yksinäinen
ikkuna näytetään täydellä ruudulla ja aina kun uusi ikkuna avataan, jonkin aiemman ikkunan käyttämä tila
jaetaan kahtia. Näin ikkunoista muodostuu ruudukko, jossa ne ovat kaikki yhtä aikaa näkyvillä.
Tiilittävät ikkunamanagerit ovat tyypillisesti olleet joidenkin ohjelmoijien ja paljon terminaalia käyttävien
suosiossa. Ne ovat yleensä myös "näppäimistöystävällisiä", eivätkä siis vaadi hiiren käyttöä, sekä
tavallisempia ikkunanhallintaohjelmia kevyempiä, eli soveltuvat myös vanhempien ja hitaampien laitteiden
käyttöön.

Tiilittäviä ovat esimerkiksi: Xmonad, i3, Subtle, Ion, Ratpoison, Wmii ja dwm.

{{% wrapper class="theorybox" %}}
Tiilittävä ikkunamanageri: i3
===============================
{{< youtube 9ofq4gpG_lM >}}
{{% /wrapper %}}




Ikkunamanageri: kokeillaan
==============================

(Ubuntussa tämän osuuden asennusten tekeminen vaatii `universe`-pakettilähteen aktivoimista
Ubuntun sovellusvalikoiman asetuksista.)

1. Asennetaan muutama ikkunamanageri, esimerkiksi: fvwm, icewm, windowmaker, ratpoison, openbox
    * `sudo apt-get install icewm`
2. Käynnistetään tyhjä X (ohjeet sivulla [X-ikkunointi](../x-ikkunointi)) ja sinne esimerkiksi icewm kirjoittamalla *xterm*-ikkunaan: `icewm`
3. Kokeillaan ikkunamanagerin toimintaa, suljetaan se ja kokeillaan muita.

Vaihtoehtoisia ikkunamanagereja voi käyttää myös varsinaisessa X:ssä Gnomen tilalla:

* Kirjaudutaan ulos työpöydältä
* Valitaan käyttöliittymäksi Gnomen sijasta joku muu vaihtoehdoista
* Kirjaudutaan sisään

***Huom!*** Jos käytät live-levyä, joka tallentaa käyttäjän tiedostot ja asetukset, mutta ei järjestelmän
muutoksia, muista ennen järjestelmän sammuttamista kirjautua takaisin alkuperäiseen käyttöliittymään.

Tämä siksi, ettei seuraavan käynnistyksen yhteydessä yritetä, käyttäjän valitseman asetuksen
mukaisesti, ladata jokin muu käyttöliittymä, jota ei olekaan asennettuna. Eikä alkuperäistä ole kirjautumisikkunassa
valittavissa, koska oletusliittymän lisäksi ei ole muita asennettuna.

Jos näin kuitenkin pääsee käymään, tilanteen voi korjata poistamalla käyttäjän kotihakemistosta tiedoston `.dmrc`.
(Tekstitilaan näppäinyhdistelmällä `ctrl-alt-f2`, sisäänkirjautuminen live-tunnuksella "ubuntu" ja tyhjällä
salasanalla sekä komento `rm .dmrc`.)
