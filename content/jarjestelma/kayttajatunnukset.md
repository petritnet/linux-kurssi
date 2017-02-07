+++
date = "2016-09-06T21:59:51+03:00"
title = "Käyttäjätunnukset"
weight = 110
+++

Käyttäjätunnukset
==================

* Käyttäjätunnus
* User id (uid): käyttäjänumero
* `/etc/passwd`
    * Rivit muotoa:<br />
      `pesasa:x:1000:1000:Petri Salmela,,,:/home/pesasa:/bin/bash`
* Salasana: `/etc/shadow`
    * Rivit muotoa:<br />
      `pesasa:$6$mE/6BCoS$oV7b2d2//73dGtKHL.G9ezHgFQ9/kJcJVmqiP8YRiS7T76uRxU3oxx0P/uuYfwtgHxd4/1015dFRB.wJNYhI/.:15595:0:99999:7:::`


Käyttäjäryhmät
==================

* Käyttäjä voi olla useammassa ryhmässä
* Group id (gid): ryhmän numero
* `/etc/group`
    * Muotoa:<br />
      `audio:x:29:pulse,timidity`
* Käyttäjille annetaan usein oikeuksia ryhmän kautta.
* Käyttäjätunnuksesta ja ryhmistä tietoa komentorivillä komennolla `id`.




Käyttäjän lisääminen
==================

* Ubuntun asetuksista käyttäjien hallinta
* Lukituksen avaus salasanalla, jotta saadaan ylläpito-oikeudet
* Lisätään uusi käyttäjä ja valitaan käyttäjätyyppi (Standard / Administrator)
    * Käyttäjätyypin mukaan tiettyihin ryhmiin
    * Standard: vain saman niminen ryhmä kuin käyttäjätunnus
    * Administrator: lisäksi ryhmä `sudo`
* Salasana joko syötettynä tai generoituna
* Valittavissa myös: *Automatic login*

