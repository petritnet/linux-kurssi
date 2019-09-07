---
date: "2019-09-07T20:51:00+03:00"
title: "Ssh-palvelin"
weight: 520
---

Tekstipohjaista **etäkäyttöä** varten koneelle voi asentaa *ssh-palvelimen*.
Salatulla liikenteellä tapahtuvan etäkäytön lisäksi ssh mahdollistaa myös
**tiedostojen siirron** ja muuta tyyppiä olevien verkkoyhteyksien **putkittamisen**
salatun ssh-yhteyden läpi.

Asentaminen tapahtuu paketinhallinnasta asentamalla paketti `openssh-server`.

```no-highlight
sudo apt-get install openssh-server
```

Ssh-yhteydellä koneelle kirjaudutaan joko **käyttäjätunnus ja salasana** -yhdistelmällä
taikka käyttäjätunnuksella ja ssh-avaimilla. Yhteys muodostetaan komennolla:

```no-highlight
ssh <tunnus>@<koneen_nimi>
```

Tämän jälkeen ssh-palvelin kysyy käyttäjän salasanaa.

Ssh-avaimet
============

Ssh-avainten kanssa kirjautuminen tapahtuu seuraavasti:

- Asiakaskoneella luodaan ssh:ta varten avainpari (julkinen ja salainen) komennolla `ssh-keygen`.
    - Avaimelle voi määrätä salasanan, jota kysytään aina, kun sitä käytetään.
      Salasanan voi jättää myös antamatta, jolloin sitä ei kysytä.
    - Samaa avainta voi käyttää otettaessa yhteyksiä useammalle palvelimelle,
      jolloin riittää yksi salasana, eli avaimen salasana.
- Julkinen avain kopioidaan palvelinkoneelle kotihakemiston `.ssh`-hakemistoon
  tiedostoon `authorized_keys`. Tämä tapahtuu helposti komennolla `ssh-copy-id`.
- Kun palvelimelle seuraavan kerran otetaan ssh-yhteys, ssh-palvelin ei kysykään
  salasanaa vaan kirjautuminen tehdään avaimilla. Palvelin antaa julkista avainta
  käyttäen haasteen, johon vain oikea salainen avain osaa antaa oikean vastauksen.
  Jos salainen avain on suojattu salasanalla, se kysytään, jotta salainen avain
  saadaan käyttöön, mutta salasanaa tai salaista avainta ei koskaan
  lähetetä verkon yli palvelimelle.

Avaimia käyttävä kirjautuminen on vahvempi ja turvallisempi kuin salasanalla tapahtuva.


Ssh-asetukset
================

Ssh-palvelun asetuksia voi säätää tiedostosta `/etc/ssh/sshd_config`.
Muutettavissa olevia asetuksia ovat muun muassa:

- Voiko `root`-käyttäjä kirjautua ssh:n kautta.<br>
  Root-käyttäjän kirjautuminen kannattaa olla estettynä, sillä suurin osa
  verkossa automaattisesti tehtävistä murtoyrityksistä kokeilee juuri `root`-tunnusta
  ja heikkoja salasanoja.
- Käytettävissä olevat kirjautumiskeinot (salasana, kirjautumisavaimet,
  sormenjälkilukija, älykortti)
- Graafisen (X11)-yhteyden tunnelointi ssh-yhteyden läpi

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
