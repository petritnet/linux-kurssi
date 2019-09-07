---
date: "2017-03-16T22:24:38+03:00"
title: "Tietokantapalvelimet"
weight: 540
---

Www-palveluiden yhteydessä tarvitaan usein myös tietokantoja.
Linux-järjestelmissä on tarjolla useampia vaihtoehtoja.

MySQL- ja MariaDB-tietokannat
=============================

MySQL on suomalaisen Michael "Monty" Wideniuksen aloittama avoimen lähdekoodin
tietokantajärjestelmä. MySQL:n kävi pitkälti samoin kuin OpenOffice.org-toimisto-ohjelmiston.
Se myytiin Sun Microsystemsille, joka myytiin Oraclelle. Koska Oracle on suuri
tietokantajärjestelmien toimittaja, jolla on oma kaupallinen tietokantaohjelmistonsa,
heräsi MySQL-yhteisössä epäilyksiä MySQL:n tulevasta kohtalosta.
Tämän jälkeen avoimen lähdekoodin kehittäjät päättivät forkata ohjelmiston ja
jatkaa sen kehittämistä uudella nimellä Oraclesta riippumattomana.

- MySQL AB -> Sun Microsystems -> Oracle
- Oli/on www-palveluissa usein käytetty tietokantajärjestelmä
- Voi toimia tietokantapalvelimena koneen sisäisesti www-palvelulle tai ulospäin.

MariaDB on MySQL:stä haarautunut (forkattu) Oraclesta riippumaton tietokantajärjestelmä,
joka on suurelta osin yhteensopiva MySQL:n kanssa.

- Monty Widenius sai miljoonia euroja myytyään osuutensa MySQL AB:sta Sun Microsystemsille.
- Widenius ei kuitenkaan ollut tyytyväinen, kun MySQL päätyi Oraclen käsiin, vaan otti MySQL:n avoimen lähdekoodin ja
  lähti uudelleen kehittämään sitä uudella MariaDB-nimellä.
- Linux-jakelut ovat korvanneet MySQL:n pakettivarastoissaan MariaDB:llä.
- Myös esimerkiksi Google ja Wikipedia vaihtoivat käyttämään MariaDB:tä.

**My** ja **Maria** ovat molemmat Monty Wideniuksen tyttärien nimiä.

Asennus tapahtuu komennolla:

```no-highlight
sudo apt-get install mariadb-server
```

Muita tietokantoja
=====================

Muita avoimen lähdekoodin tietokantoja Linux-järjestelmiin ovat:

- PostreSQL (SQL)
- MongoDB (NoSQL)
- CouchDB (NoSQL)

NoSQL-kannat ovat järjestelmiä, joihin tietoa ei tallenneta ja haeta SQL-kyselykielellä vaan JavaScriptillä JSON-objektien tapaan.
