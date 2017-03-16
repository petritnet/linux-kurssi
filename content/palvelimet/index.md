+++
date = "2017-03-16T22:24:38+03:00"
title = "Palvelimet"
weight = 500
type = "index"
menu = ["main"]
+++

Mikä on palvelin? Usein palvelimesta puhuttaessa ensimmäiseksi ajatellaan tehokasta laitetta.
Varsinaisesti palvelimessa on kuitenkin kyse käynnissä olevasta palvelinohjelmasta.
Ohjelmasta, johon asiakasohjelma ottaa yhteyttä ja pyytää "palvelusta".

Tällaisia voivat olla esimerkiksi:

- www-palvelin
- ssh-palvelin
- tietokantapalvelin
- sähköpostipalvelin
- pikaviestipalvelin
- tiedostopalvelin

Palvelinohjelma voi olla käynnissä pienessäkin koneessa, kuten Raspberry Pi -koneessa.



Palvelimen portti
=================

Kun palvelinohjelma on käynnissä ja valmiina ottamaan vastaan pyyntöjä, sanotaan, että
se kuuntelee jotain porttia. Tämä tarkoittaa, että kaikki koneelle tulevat yhteyspyynnöt,
joissa pyydetään yhteyttä tietyllä porttinumerolla, ohjataan tälle palvelinohjelmalle.

Joillain palvelintyypeille on varattu käyttöön tietyt sovitut porttinumerot. Esimerkiksi:

|Palvelu | Portti | Kuvaus                                    |
|--------|-------:|-------------------------------------------|
| http   | 80     | web                                       |
| https  | 443    | web ssl-salattuna                         |
| ftp    | 21     | tiedostonsiirtopalvelu                    |
| ssh    | 22     | salattu komentoriviyhteys                 |
| telnet | 23     | selväkielinen komentoriviyhteys           |
| smtp   | 25     | lähtevä sähköposti, salattuna 465 tai 587 |
| imap   | 143    | saapuva sähköposti, salattuna 993         |



Palvelut Ubuntussa
===================

Palvelinohjelmistot ovat asennettavissa paketinhallinnasta samaan tapaan kuin muutkin ohjelmat.
Jos palvelu on asennettuna, se myöskin käynnistetään oletuksena.
Palvelinohjelmistoja on mahdollista asentaa myös paketinhallinnan ulkopuolelta käsin.

Asennettujen ja käytettävissä olevien palveluiden käynnistämiseen ja pysäyttämiseen käytettävät
skriptit ovat vanhastaan hakemistossa `/etc/init.d/`. Uudemmissa järjestelmissä käynnistysasetukset löytyvät
hakemistosta `/etc/init/`.

Ubuntussa toimivat rinnakkain vanhempi ja uudempi tapa käynnistää, sammuttaa ja uudelleenkäynnistää palveluita
sekä kysyä niiden tila.
Vanhempi tapa on komennoilla:

```no-highlight
sudo service <palvelu> start
sudo service <palvelu> stop
sudo service <palvelu> restart
sudo service <palvelu> status
```

Uudempi, **systemd**-järjestelmän tapa tapahtuu vastaavasti komennoilla:
```no-highlight
sudo systemctl start <palvelu>
sudo systemctl stop <palvelu>
sudo systemctl restart <palvelu>
sudo systemctl status <palvelu>
```
