---
date: "2017-03-16T22:24:38+03:00"
title: "Palveluita"
weight: 510
---

Käydään läpi joitain tyypillisesti Linux-asennuksessa käytettäviä palveluita ja
niihin käytettäviä ohjelmistoja.

Avahi
=====

Internetissä jokaisella koneella on IP-osoite, jolla se tunnistetaan verkossa.
Lisäksi palvelimilla on yleensä myös nimi, johon sillä voi viitata.
DNS-palvelu (Domain Name Service) tekee hoitaa nimien yhdistämisen IP-osoitteisiin. (kuin puhelinluettelo)
Nimien ja IP-osoitteiden yhdistäminen voidaan (kotiverkossa) tehdä myös `/etc/hosts`-tiedostolla.

Koska `hosts`-tiedoston päivittäminen on työlästä, jos osoitteet muuttuvat, käytetään
Ubuntussa ja useimmissa muissa Linux-jakeluissa Zeroconf-palvelua nimeltä Avahi.
Sillä kone käynnistyttyään kertoo itse nimensä samassa verkossa oleville koneille.
Avahi on palvelinohjelma, joka käynnistyy koneen käynnistyessä.



LAMP
=====

LAMP on nimitys, jota käytetään usein yhdistelmästä Linux + Apache + MySQL + PHP.
Nämä ovat komponentit, joista monet www-palvelut on koostettu: Käyttöjärjestelmäalusta,
[www-palvelin](../www-palvelin), [tietokantapalvelin](../tietokanta) sekä
www-palveluihin soveltuva ohjelmointikieli.
Nykyään M tarkoittaa usein MariaDB:tä ja toisinaan P tarkoittaa Pythonia.

Aiemmin LAMP oli ylivoimaisesti käytetyin yhdistelmä. Nykyään rinnalle on noussut
useita muita yhdistelmiä, kuten Java ja Tomcat sekä Javascript ja Node.js.



NextCloud / ownCloud
====================

Hyvä esimerkki LAMP-yhdistelmän päällä toimivasta palvelukokonaisuudesta on
ownCloud ja siitä haarautunut NextCloud. Kyseessä on järjestelmä, jolla voi
rakentaa itselleen omalle palvelimelle oman pilvipalvelun, joka voi sisältää
ainakin seuraavat toiminnallisuudet:

- Tiedostotallennuspalvelu
    - Hakemiston sisällön synkronointi vastaavasti kuin Dropbox, GoogleDrive, OneDrive, ...
    - Web-käyttöliittymä
    - Puhelinsovellukset ja kuvien automaattinen lähetys pilveen
- Kalenteri
    - Web-käyttöliittymä
    - Synkronointi tietokoneelle tai puhelimeen
    - CalDAV-standardi
- Yhteystiedot
    - Synkronointi tietokoneelle tai puhelimeen
    - CardDAV-standardi
- Kuvagalleria
- Musiikkigalleria ja -soitin
- Web-kirjanmerkit
- Todo-listat
- RSS-lukija
- Webmail sähköpostin lukemiseen


Tehtäviä
=========================

{{% wrapper class="exercises" %}}
Tehtävät 14
--------------------------

Kirjoita vastaukset tiedostoon `tehtava-14.txt` ja ota kuvakaappaukset.

1. Asenna `openssh-server`
2. Avaa terminaali-ikkuna ja ota ssh:lla yhteys koneeseen `localhost`. Ota terminaali-ikkunasta kuvakaappaus kirjautumisen jälkeen.
3. Asenna `apache2`.
4. Avaa selaimeen osoite <http://localhost/>. Mitä auenneella sivulla lukee? (Pari ensimmäistä riviä)
5. Tee itsellesi ssh-avaimet, kopio avain kurssin palvelimelle ja ota sen jälkeen kokeile ottaa yhteys. Millä komennoilla teit nämä?
   Asetitko avaimelle salasanan?
6. Kokeile NextCloudia osoitteessa <https://demo.nextcloud.com>. "Instant trial" -vaihtoehdolla palveluun voi tehdä 60 minuuttia kestävän
   NextCloud-palvelun kokelua varten. Ota kuvakaappaus.

{{% /wrapper %}}
