---
date: "2016-09-11T21:25:17+03:00"
title: "Ohjelmistot"
weight: 300
type: "index"
menu:
    main:
        weight: 300
---

Tutustutaan Linuxeihin tarjolla oleviin ohjelmistoihin.

Ohjelmia Linuxiin
===============================

Usein kuulee Windows-käyttäjien sanovan, että "Linuxille ei ole ohjelmia".
Tämä ei kuitenkaan pidä paikkaansa. Ohjelmat vain ovat usein eri ohjelmia kuin
Windowsissa.

Linuxiin on tarjolla paljon vapaita ohjelmia, jotka ovat asennettavissa suoraan
järjestelmän omasta paketinhallinnasta. Osa merkittävimmistä Linuxissa käytettävistä
ohjelmista on tarjolla myös Windowsiin.

Kaupallisten ja ei-vapaiden ohjelmien sekä pelien tarjonta on kuitenkin rajallisempaa.
Tämä on perinteisesti johtunut toisaalta siitä, että Linux-käyttäjät ovat olleet
monille ohjelmistovalmistajille liian pieni kohderyhmä, ja toisaalta siitä, että
moneen erilaiseen jakeluun jakautunut Linux-kenttä ei ole tarjonnut teknisesti
riittävän yhtenäistä alustaa. Esimerkiksi ohjelmistojen paketointi vaihtelee
jakeluiden välillä jonkin verran.

Viime aikoina kuitenkin esimerkiksi [Steam]-palvelun kautta ostettavien ja
ladattavien pelien määrä on lisääntynyt myös Linux-alustalle. Samoin myös Ubuntu
ja muut Ubuntu-pohjaiset jakelut ovat keränneet sen verran suosiota, että
onnistuvat houkuttelemaan myös joitakin kaupallisia ohjelmia.

Uudet [paketointitavat](../../jarjestelma/ohjelmistopaketit), kuten Snap,
AppImage ja FlatPak ovat myös tuoneet mahdollisuuden paketoida ohjelmia helpommin
yhdellä paketoinnilla kaikissa Linux-jakeluissa toimivaan muotoon.

Myös HTML5 ja web-sovellukset muuttavat tilannetta, sillä varsin suuri osa
kuluttajien käyttämistä ohjelmista ei olekaan enää perinteisiä omalle koneelle
asennettavia ohjelmia vaan pilvipalveluna selaimella käytettäviä. Tällöin alustana
olevalla käyttöjärjestelmällä ei olekaan enää merkitystä sovelluksen
käytön kannalta.

HTML5-sovellusten lisääntyessä myös esimerkiksi [Electron]-ympäristöllä
JavaScript-kielellä toteutetut ohjelmistot ovat yleistyneet. Näin toteutetut
ohjelmistot ovat aiempaa helpommin paketoitavissa Linuxille samanlaisina kuin
Windows- ja Mac-alustoille. Electron-ympäristöä käyttäviä sovelluksia ovat
muun muassa:

- Atom (tekstieditori)
- MS Visual Studio Code (tekstieditori)
- Skype (viestintä)
- Slack (viestintä)
- Discord (viestintä)
- Google Play Music (musiikkisoittimen työpöytäversio)
- Etcher (levykuvien kirjoitusohjelma)



Ohjelmien jaottelua
===================

Sen lisäksi, että Linuxiin on sekä graafisia että tekstipohjaisia ohjelmia,
voidaan graafiset ohjelmat usein luokitella myös niiden tekemiseen käytettyjen
käyttöliittymäkomponenttien mukaan.

Koska Linuxissa on käytössä useampia eri työpöytiä, jotka käyttävät eri
käyttöliittymäkirjastoja, on seurauksena valikoiltaan, nappuloiltaan ja muilta
käyttöliittymäkomponenteiltaan hieman eri näköisiä ohjelmistoja. Suurin jako on
GTK-kirjastoa käyttävien Gnome-ohjelmien ja Qt-kirjastoa käyttävien KDE-ohjelmien
välillä. Useisiin käyttötarkoituksiin onkin tarjolla erikseen Gnome-pohjainen ja
KDE-pohjainen ohjelma. Esimerkiksi Gnome-tyyppisillä työpöydillä (Gnome, Unity,
Cinnamon, jne.) käytetään yleensä pdf-lukijana Evince-ohjelmaa ja KDE-ympäristössä
Okular-ohjelmaa.

Mikään ei luonnollisestikaan estä ohjelmien käyttämistä tämän jaottelun yli.
Ulkonäöllistä eroavaisuutta on usein pyritty myös tasoittamaan luomalla molemmille
käyttöliittymätyypeille toisiaan muistuttavia teemoja.


[Steam]: http://store.steampowered.com/ (Steam)
[Electron]: https://electronjs.org/ (Electron)
