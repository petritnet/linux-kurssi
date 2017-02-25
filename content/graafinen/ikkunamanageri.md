+++
date = "2017-02-25T18:30:04+03:00"
title = "Ikkunamanagerit"
sectiontitle = "Graafinen käyttöliittymä"
weight = 220
+++


{{< figure src="/images/fvwm2.jpg" link="/images/fvwm2.jpg" class="floatimage floatright" title="FVWM2" caption="Vanhempi ja 'alkeellisempi' ikkunanhallintaohjelma FVWM2." >}}
{{< figure src="/images/enlightenment.jpg" link="/images/enlightenment.jpg" class="floatimage floatright" title="Enlightenment (E17)" caption="Modernimpi Enlightenment-ikkunamanageri" >}}
{{< figure src="/images/wmii.jpg" link="/images/wmii.jpg" class="floatimage floatright" title="Wmii" caption="Tiilittävä Wmii-ikkunamanageri" >}}

Ikkunoiden hallinta, eli niiden siirtely, koon muuttaminen, pinoaminen päällekkäin sekä muu
vastaava, tapahtuu erillisellä
[ikkunamanagerilla](http://en.wikipedia.org/wiki/X_window_manager).
Näitä on monia ja ne ovat sekä ulkoasultaan, toiminnallisuuksiltaan että tuntumaltaan erilaisia.

* Graafisesti näyttäviä 3d-efekteillä
* kevyempiä perusikkunamanagerita<br>
  (Icewm, Windowmaker, Enlightenement (E17),...)
* "Tiilittäviä" ikkunamanagereita (Xmonad, Subtle, Ion, Ratpoison, Wmii, dwm,...)

[Tiilittävillä ikkunamanagereilla](https://en.wikipedia.org/wiki/Tiling_window_manager)
tarkoitetaan ikkunoiden hallintaan käytettäviä ohjelmia, jotka pyrkivät tarkoituksellisesti
välttämään ikkunoiden asettelemista päällekkäin. Tämä tapahtuu yleensä siten, että yksinäinen
ikkuna näytetään täydellä ruudulla ja aina kun uusi ikkuna avataan, jonkin aiemman ikkunan käyttämä tila
jaetaan kahtia. Näin ikkunoista muodostuu ruudukko, jossa ne ovat kaikki yhtä aikaa näkyvillä.
Tiilittävät ikkunamanagerit ovat tyypillisesti olleet joidenkin ohjelmoijien ja paljon terminaalia käyttävien
suosiossa. Ne ovat yleensä myös "näppäimistöystävällisiä", eivätkä siis vaadi hiiren käyttöä, sekä
tavallisempia ikkunanhallintaohjelmia kevyempiä, eli soveltuvat myös vanhempien ja hitaampien laitteiden
käyttöön.

Jotkut ikkunamanagerit osa suurempaa työpöytäympäristöä, joka sisältää työpöydän, panelit, sovelmat, kuvakkeet, jne.
(Gnome, KDE Plasma, Unity, XFCE, LXDE, Cinnamon, MATE, Pantheon, ...)




Ikkunamanageri: kokeillaan
==============================

(Ubuntussa tämän osuuden asennusten tekeminen vaatii `universe`-pakettilähteen aktivoimista
Ubuntun sovellusvalikoiman asetuksista.)

1. Asennetaan muutama ikkunamanageri, esimerkiksi: icewm, windowmaker, ratpoison, openbox
    * `sudo apt-get install icewm`
2. Käynnistetään tyhjä X ja sinne esimerkiksi icewm kirjoittamalla *xterm*-ikkunaan: `icewm`
3. Kokeillaan ikkunamanagerin toimintaa, suljetaan se ja kokeillaan muita.

Vaihtoehtoisia ikkunamanagereja voi käyttää myös varsinaisessa X:ssä Unityn tilalla:

* Kirjaudutaan ulos työpöydältä
* Valitaan käyttöliittymäksi Unityn sijasta joku muu vaihtoehdoista
* Kirjaudutaan sisään

***Huom!*** Jos käytät live-levyä, joka tallentaa käyttäjän tiedostot ja asetukset, mutta ei järjestelmän
muutoksia, muista ennen järjestelmän sammuttamista kirjautua takaisin alkuperäiseen käyttöliittymään.

Tämä siksi, että muutoin seuraavan käynnistyksen yhteydessä yritetään käyttäjän valitseman asetuksen
mukaisesti ladata jokin muu käyttöliittymä, jota ei olekaan asennettuna. Eikä alkuperäistä ole kirjautumisikkunassa
valittavissa, koska oletusliittymän lisäksi ei ole muita asennettuna.

Jos näin kuitenkin pääsee käymään, tilanteen voi korjata poistamalla käyttäjän kotihakemistosta tiedoston `.dmrc`.
(Tekstitilaan näppäinyhdistelmällä `ctrl-alt-f1`, sisäänkirjautuminen live-tunnuksella "ubuntu" ja tyhjällä
salasanalla sekä komento `rm .dmrc`.)

