+++
date = "2016-09-08T20:48:53+03:00"
title = "Verkko"
sectiontitle = "Järjestelmä"
weight = 140
+++

Verkkoyhteydet ovat olennainen osa nykyaikaista tietojenkäsittelyä.
Internet-yhteydet ovat olleet Unix-järjestelmien osana jo kauan ja Linuxissa alusta saakka

* AT&T julkaisi UNIX:in TCP/IP-toteutuksen public domainina 1989. Monet muut järjestelmät omaksuivat sen.
* Nyky-Linuxeissa verkkoyhteydet hoitaa NetworkManager, jonka käyttöliittymät antavat käyttäjän
  valita langattomat verkot yms.




Avahi
===============================

Avahi asettaa lähiverkkoasetusten automaattisesti [Zeroconf](https://en.wikipedia.org/wiki/Zero-configuration_networking)-toteutuksella. Mac-maailmassa vastaava tunnetaan nimellä Bonjour.

* Kukin kone tietää oman nimensä ja tarjoamansa palvelut sekä osaa kertoa ne muille saman verkon koneille
* Voidaan käyttää nimeä `koneennimi.local` pelkän ip-numeron sijaan
* Helpottaa silloin, kun koneet saavat ip-osoitteensa dynaamisesti DHCP-palvelimelta
  eikä niillä siksi ole aina samaa ip-numeroa.




Hosts-tiedosto
===============================

Jos Avahi ei ole toiminnassa, nimet lähiverkon ip-osoitteille voi kertoa tiedostossa `/etc/hosts`
Tiedosto muotoa:

```
 127.0.0.1       localhost
 192.168.0.1     aku
 192.168.0.23    mikki
 192.168.0.53    hessu hopo
```




Ssh-yhteys
===============================

Ssh on tekstipohjainen salattu komentoriviyhteys toiseen koneeseen.

* Kohdekoneella oltava ssh-palvelin päällä
* `ssh kayttajatunnus@etakone`
* Kysyy salasanan ja päästää komentoriville
* Ssh korvasi salaamattoman ja turvattoman telnet-yhteyden.
* Myös ssh on kehitetty alkujaan Suomessa. (Tatu Ylönen)




Tiedostonsiirto
===============================

Tiedostoja voidaan siirtää koneiden välillä esimerkiksi *Samba*- ja *Sftp*-protokollilla

* Samba on Windows-verkon smb-protokolla.
    * Jaettuja levyjä ja tulostimia voidaan käyttää
    * Omien jakaminen vaatii palvelun asentamisen omalle koneelle
* sftp toimii ssh-palvelimen kautta
    * Vaatii ssh-palvelimen asentamisen omalle koneelle, jotta sen tiedostoihin pääsee käsiksi.
    * Käyttäjä pääsee käsiksi kaikkiin tiedostoihin, joihin pääsisi paikallisesti kirjautumalla
    * Korvaa salaamattoman ftp-yhteyden.




Graafisesti
===============================

Samba- ja sftp-protokollia voi käyttää suoraan graafisilla tiedostonhallintaohjelmilla.

* Useimmista tiedostonhallintaohjelmista löytyy "Network"-valinta, jonka alta löytyvät Windows-verkon palvelut.
* Windows-jakoon voi viitata myös suoraan osoitteella `smb://koneennimi/jako`
* Sftp-yhteyden voi muodostaa toiselle koneelle vastaavasti osoitteella `sftp://koneennimi` tai `fish://koneennimi`

* scp: Kopioi tiedostoja ssh:n kautta suuntaan tai toiseen. Ei hakemistolistauksia, ei tiedostojen poistoa, yms.
* sftp: Palvelinpuolella erillinen sftp-server-ohjelma, jonka kanssa juttelee ssh:n läpi.
  Ssh hoitaa tunnistautumisen ja kryptaamisen.
* fish: Käyttää palvelinpuolella normaaleja komentorivityökaluja hakemistolistauksen näyttämiseen,
  tiedostojen poistamiseen yms. Toimii myös, kun ei ole sftp-server-ohjelmaa, mutta vaatii mahdollisuuden
  ajaa komentoriviohjelmia (eli käyttäjällä lupa kirjautua sisään ssh:lla).




Komentoriviltä
===============================

Ssh-yhteyden yli voidaan kopioida tiedostoja myös kometoriviltä. Esimerkkejä:

Kopioidaan tiedosto etäkoneelta paikalliseen hakemistoon antamalla ensin etäosoitteessa
olevan tiedoston nimi ja sitten pailallisen hakemiston nimi.
```no-highlight
scp kayttajanimi@etakone:/polku/tiedostoon/nimi.txt /polku/tiedostoon/talla/koneella/
```

Kopioidaan tiedosto etäkoneelta paikalliselle koneelle nykyiseen työhakemistoon uudella tiedostonimellä.

```no-highlight
scp kayttajanimi@etakone:/polku/tiedostoon/nimi.txt uusinimi.txt
```

Kopioidaan tiedosto paikalliselta koneelta etäkoneelle haluttuun hakemistoon uudella nimellä antamalla ensin
paikallisen tiedoston nimi tarvittavan absoluuttisen tai suhteellisen polun avulla ja sitten
uuden tiedoston etäosoite. (absoluuttinen polku)

```no-highlight
scp /polku/talla/koneella/nimi.txt kayttajanimi@etakone:/polku/toisella/koneella/uusinimi.txt
```

Kopioidaan tiedosto paikalliselta koneelta etäkoneelle haluttuun hakemistoon uudella nimellä. (suhteellinen polku)

```no-highlight
scp /polku/talla/koneella/nimi.txt kayttajanimi@etakone:hakemisto/kotihakemiston/alla/uusinimi.txt
```




Tehtäviä
========================

{{% wrapper class="exercises" %}}

Tehtävät 6
===============================

Tehtävien tekemiseen tarvitset palvelimen, käyttäjätunnuksen ja salasanan. Viimeistä tehtävää varten
palvelimella on oltava käynnissä (Apache) www-palvelin. Palauta vastauksena tiedosto `tehtava-6.zip`.

1. Selaa graafisella käyttöliittymällä esiin annettu sftp-osoite ja kopioi käyttäjätunnuksesi
   oman kotihakemiston Pictures-alihakemistosta yksi kuva omalle koneellesi.
2. Luo omalla koneellasi uusi tiedosto nimeltä `nimi.txt` ja kirjoita siihen oma nimesi.
    * Avaa terminaali ja kopioi tämä tiedosto scp-komennolla käsketylle palvelimelle kotihakemiston
      Documents-alihakemistoon.
    * Selaa graafisella tiedostohallinnalla tuo palvelinkoneen Documents-hakemisto näkyviin.
    * Ota kuvakaappaus, jossa näkyy hakemiston sisältö tiedostohallintaikkunassa sekä terminaalissa tehty kopiointi.
3. Ota terminaali-ikkunassa ssh-yhteys palvelimelle.
    * Siirry Documents-hakemistoon.
    * Muuta `nimi.txt`-tiedoston oikeuksia niin, että käyttäjällä ja ryhmällä ovat luku- ja kirjoitusoikeudet,
      mutta muilla ei mitään oikeuksia.
    * Listaa hakemiston sisältö pitkässä muodossa, jotta näet, että oikeudet ovat oikein.
    * Ota kuvakaappaus, jossa näkyvät terminaali-ikkunassa annetut komennot.
4. Paketoi ladattu kuvatiedosto ja otetut kuvakaappaukset zip-tiedostoon nimellä `tehtava-6.zip`.
5. Kopioi alla oleva teksti johonkin tekstieditoriin (gedit, scratch, jokin muu) ja tallenna nimellä `index.html`.
   Voit tehdä hienommankin html-sivun. Kopioi tiedosto haluamallasi tavalla palvelimelle kotihakemistossasi olevaan
   `public_html`-hakemistoon. Mene www-selaimella osoitteeseen `http://<palvelimen_nimi>/~<käyttäjätunnus>`.
   (Korvaa palvelimen nimi ja käyttäjätunnus.)

```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <title>Terve, Linux-kurssi!</title>
    </head>
    <body>
        <h1>Terve, Linux-kurssi!</h1>
        <p>Tämä on index.html-tiedosto käyttäjän oman kotihakemiston
<em>public_html</em>-alihakemistossa.</p>
    </body>
</html>
```
{{% /wrapper %}}