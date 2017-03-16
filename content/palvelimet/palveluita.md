+++
date = "2017-03-16T22:24:38+03:00"
title = "Palveluita"
weight = 510
+++

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



Ssh-palvelin
=============

Tekstipohjaista **etäkäyttöä** varten koneelle voi asentaa *ssh-palvelimen*.
Salatulla liikenteellä tapahtuvan etäkäytön lisäksi ssh mahdollistaa myös
**tiedostojen siirron** ja muun tyyppisten verkkoyhteyksien **putkittamisen**
ssh-yhteyden läpi.

Asentaminen tapahtuu paketinhallinnasta asentamalla paketti `openssh-server`.

```no-highlight
sudo apt-get install openssh-server
```

Ssh-yhteydellä koneelle kirjaudutaan joko **käyttäjätunnus ja salasana** -yhdistelmällä
taikka ssh-avaimilla. Yhteys muodostetaan komennolla:

```no-highlight
ssh <tunnus>@<koneen_nimi>
```

Tämän jälkeen ssh-palvelin kysyy käyttäjän salasanaa.

Ssh-avaimet
-------------

Ssh-avainten kanssa kirjautuminen tapahtuu seuraavasti:

- Asiakaskoneella luodaan ssh:ta varten avainpari (julkinen ja salainen) komennolla `ssh-keygen`.
    - Avaimelle voi määrätä salasanan, jota kysytään aina, kun sitä käytetään. Salasanan voi jättää myös antamatta, jolloin sitä ei kysytä.
    - Samaa avainta voi käyttää otettaessa yhteyksiä useammalle palvelimelle, jolloin riittää yksi salasana, eli avaimen salasana.
- Julkinen avain kopioidaan palvelinkoneelle kotihakemiston `.ssh`-hakemistoon tiedostoon `authorized_keys`. Tämä tapahtuu helposti komennolla `ssh-copy-id`.
- Kun palvelimelle seuraavan kerran otetaan ssh-yhteys, ssh-palvelin ei kysykään salasanaa vaan kirjautuminen tehdään avaimilla.
  Palvelin antaa julkista avainta käyttäen haasteen, johon vain oikea salainen avain osaa vastata oikein.
  Jos salainen avain on suojattu salasanalla, se kysytään, jotta salainen avain saadaan käyttöön, mutta salasanaa tai salaista avainta ei koskaan
  lähetetä verkon yli palvelimelle.

Avaimia käyttävä kirjautuminen on vahvempi ja varmempi kuin salasanalla tapahtuva.


Ssh-asetukset
---------------

Ssh-palvelun asetuksia voi säätää tiedostosta `/etc/ssh/sshd_config`. Muutettavissa olevia asetuksia ovat muun muoassa:

- Voiko `root`-käyttäjä kirjautua ssh:n kautta.<br>
  Root-käyttäjän kirjautuminen kannattaa olla estettynä, sillä suurin osa verkossa automaattisesti tehtävistä murtoyrityksistä kokeilee juuri `root`-tunnusta
  ja heikkoja salasanoja.
- Käytettävissä olevat kirjautumiskeinot (salasana, kirjautumisavaimet, sormenjälkilukija, älykortti)
- Graafisen (X11)-yhteyden tunnelointi

Asetusten muuttamisen jälkeen palvelu on uudelleenkäynnistettävä.

{{% wrapper class="exercises" %}}
Kokeile (ssh)
---------------

Asenna `openssh-server`:

```no-highlight
sudo apt-get install openssh-server
```

Kokeile sitä ottamalla yhteys:

```no-highlight
ssh <tunnus>@localhost
```

{{% /wrapper %}}



Www-palvelin
==============

Yleisimmin käytetyt www-palvelinohjelmistot ovat **[Apache]** ja **[Nginx]** (lausutaan, kuten "engine-x").
Molemmat ovat avointa lähdekoodia ja löytyvät suoraan Linux-jakeluiden paketinhallinnasta.

Molempien oletusasetukset ovat melko järkevät. Apachella documentroot-hakemisto, eli hakemisto, jonka alle www-sivut
tallennetaan, on useimmissa Linux-jakeluissa `/var/www/html/`. Palvelimen asetustiedostot puolestaan löytyvät hakemistoista
`/etc/apache2/` tai `/etc/httpd/`.


{{% wrapper class="exercises" %}}
Kokeile (Apache2)
---------------

Asenna `apache2`-paketti:

```no-highlight
sudo apt-get install apache2
```

Kokeile sitä menemällä selaimella osoitteeseen: <http://localhost/>.
Näkyviin pitäisi tulla Apachen oletustestisivu.

- Nouda tämä sivu `wget`-komennolla ja kopio saamasi `index.html`-tiedosto
  hakemistoon `/var/www/html/` nimellä `palveluita.html`. (ettei ylikirjoiteta oletussivua)
- Mene selaimella osoitteeseen: <http://localhost/palveluita.html>
{{% /wrapper %}}


Muita www-palvelimia
---------------------

Linuxille on tarjolla useita avoimen lähdekoodin www-palvelimia:

- Apache2 – Yleisin, monipuolinen, paljon moduleja
- Nginx – Toiseksi yleisin, yleistyy kovaa vauhtia, pieni ja tehokas www-palvelin
- Lighttpd – Pieni ja nopea www-palvelin
- Jotkut ohjelmointikielet, kuten Python ja Node.js (Javascript) sisältävät toiminnallisuuden toimia www-palvelimina.



MySQL- ja MariaDB-tietokannat
=============================

MySQL on suomalaisen Michael "Monty" Wideniuksen aloittama avoimen lähdekoodin tietokantajärjestelmä.
MySQL:n kävi pitkälti samoin kuin OpenOffice.org-toimisto-ohjelmiston.
Se myytiin Sun Microsystemsille, joka myytiin Oraclelle. Tämän jälkeen avoimen lähdekoodin kehittäjät
päättivät forkata ohjelmiston ja jatkaa kehittämistä uudella nimellä Oraclesta riippumattomana.

- MySQL AB -> Sun Microsystems -> Oracle
- Oli/on www-palveluissa usein käytetty tietokantajärjestelmä
- Voi toimia tietokantapalvelimena koneen sisäisesti www-palvelulle tai ulospäin.

MariaDB on MySQL:stä haarautunut (forkattu) Oraclesta riippumaton tietokantajärjestelmä, joka on yhteensopiva MySQL:n kanssa.

- Monty Widenius sai miljoonia euroja myytyään osuutensa MySQL AB:sta Sun Microsystemsille.
- Widenius ei kuitenkaan ollut tyytyväinen, kun MySQL päätyi Oraclen käsiin, vaan otti MySQL:n avoimen lähdekoodin ja
  lähti uudelleen kehittämään sitä uudella MariaDB-nimellä.
- Linux-jakelut ovat korvanneet MySQL:n paketinhallinnassa MariaDB:llä.
- Myös Google ja Wikipedia vaihtoivat käyttämään MariaDB:tä.

My ja Maria ovat molemmat Monty Wideniuksen tyttärien nimiä.

Asennus komennolla:

```no-highlight
sudo apt-get install mariadb-server
```

Muita tietokantoja
-------------------

Muita avoimen lähdekoodin tietokantoja Linux-järjestelmiin ovat:

- PostreSQL (SQL)
- MongoDB (NoSQL)
- CouchDB (NoSQL)

NoSQL-kannat ovat järjestelmiä, joihin tietoa ei tallenneta ja haeta SQL-kyselykielellä vaan JavaScriptillä JSON-objektien tapaan.




LAMP
=====

LAMP on nimitys, jota käytetään usein yhdistelmästä Linux + Apache + MySQL + PHP. Nämä ovat komponentit, joista monet www-palvelut
on koostettu: Käyttöjärjestelmäalusta, www-palvelin, tietokantapalvelin sekä www-palveluihin soveltuva ohjelmointikieli.
Nykyään usein M tarkoittaa MariaDB:tä ja toisinaan P tarkoittaa Pythonia.

Aiemmin LAMP oli ylivoimaisesti käytetyin yhdistelmä. Nykyään rinnalle on noussut useita muita yhdistelmiä, kuten Java ja Tomcat sekä
Javascript ja Node.js.



NextCloud / ownCloud
====================

Hyvä esimerkki LAMP-kokonaisuuden päällä toimivasta palvelukokonaisuudesta on ownCloud ja siitä haarautunut NextCloud.
Kyseessä on järjestelmä, jolla voi rakentaa itselleen omalle palvelimelle oman pilvipalvelun, joka voi sisältää ainakin seuraavat toiminnallisuudet:

- Tiedostotallennuspalvelu
    - Hakemiston sisällön synkronointi vastaavasti kuin Dropbox, GoogleDrive, OneDrive, ...
    - Web-käyttöliittymä
    - Puhelinsovellukset ja kuvien automaattinen lähetys pilveen
    - ODT-tiedostojen muokkaus suoraan web-käyttöliittymällä. Myös monta käyttäjää yhtä aikaa samalla tiedostolla.
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



Tehtäviä
=========================

{{% wrapper class="exercises" %}}
Tehtävät 14
--------------------------

Kirjoita vastaukset tiedostoon `tehtava-14.txt` ja palauta se ja kuvakaappaukset.

1. Asenna `openssh-server`
2. Avaa terminaali-ikkuna ja ota ssh:lla yhteys koneeseen `localhost`. Ota terminaali-ikkunasta kuvakaappaus kirjautumisen jälkeen.
3. Asenna `apache2`.
4. Avaa selaimeen osoite <http://localhost/>. Mitä auenneella sivulla lukee? (Pari ensimmäistä riviä)
5. Tee itsellesi ssh-avaimet, kopio avain kurssin palvelimelle ja ota sen jälkeen kokeile ottaa yhteys. Millä komennoilla teit nämä?
   Asetitko avaimelle salasanan?
6. Kokeile NextCloudia osoitteessa <https://demo.nextcloud.com>. "Instant trial" -vaihtoehdolla palveluun voi tehdä 60 minuuttia kestävän
   NextCloud-palvelun kokelua varten. Ota kuvakaappaus.

{{% /wrapper %}}






[Apache]: https://www.apache.org/ (Apache)
[Nginx]: https://www.nginx.com/ (Nginx)