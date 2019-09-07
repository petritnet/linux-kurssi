---
date: "2016-09-08T20:48:53+03:00"
title: "Verkko"
sectiontitle: "Järjestelmä"
weight: 150
---

Verkkoyhteydet ovat olennainen osa nykyaikaista tietojenkäsittelyä.
Internet-yhteydet ovat olleet Unix-järjestelmien osana jo kauan ja Linuxissa alusta saakka

* AT&T julkaisi UNIX:in TCP/IP-toteutuksen public domainina 1989. Monet muut järjestelmät omaksuivat sen.
* Nyky-Linuxeissa verkkoyhteydet hoidetaan taustalla ja käyttöliittymät antavat käyttäjän
  valita langattomat verkot yms.

TCP/IP-verkkoon kytketyillä koneilla on kullakin kyseisessä verkossa yksilöllinen ip-osoite.
IPv4-verkossa osoite on muotoa `aaa.bbb.ccc.ddd`, jossa kukin pisteillä eroteltu osa on väliltä
1-254. Pienemmät [sisäverkot](https://en.wikipedia.org/wiki/Private_network) ovat tyypillisesti
`192.168.`-alkuisia ja suuremmat `10.`-alkuisia.



Hosts-tiedosto
===============================

Koska verkon toisiin koneisiin on yleensä hankalaa viitata pelkällä ip-osoitteella,
käytetään niistä yleensä nimiä. Tutussa lähiverkossa muiden koneiden nimien ja
ip-osoitteiden vastaavuudet voidaan kertoa tiedostossa `/etc/hosts`, joka
on muotoa muotoa:

```
 127.0.0.1       localhost
 192.168.0.1     aku
 192.168.0.23    mikki
 192.168.0.53    hessu hopo
```

Kullakin rivillä on lueteltu ensin koneen ip-osoite ja sen jälkeen nimet, joilla kyseisessä
osoitteessa oleva tietokone tunnetaan.

Komennolla `ping` voi huhuilla muita samassa verkossa olevia koneita tai konetta itseään.
Komennon tuloste kertoo muun muassa sen, kuinka nopeasti paketit liikkuvat koneiden välillä.
Komennon suoritus lopetetaan näppäinyhdistelmällä `ctrl-c`.

Pingataan itseä (`localhost`):

```
$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.069 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.062 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.058 ms
64 bytes from localhost (127.0.0.1): icmp_seq=4 ttl=64 time=0.065 ms
^C
--- localhost ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.058/0.063/0.069/0.008 ms
```

Pingataan `hessu`-nimistä konetta:

```
$ ping hessu
PING hessu (192.168.0.29) 56(84) bytes of data.
64 bytes from hessu (192.168.0.29): icmp_seq=1 ttl=64 time=1.08 ms
64 bytes from hessu (192.168.0.29): icmp_seq=2 ttl=64 time=1.10 ms
^C
--- hessu ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.080/1.090/1.101/0.034 ms
```

Tiedoston `/etc/hosts` käytössä on kuitenkin se hankaluus, että kullakin koneella
pitää ylläpitää erikseen luetteloa kaikista lähiverkon koneista. Pienessä lähiverkossa
tämä vielä toimii, mutta jos koneita on vähänkin enemmän, jos ne vaihtuvat usein tai
jos niiden ip-osoitteet eivät pysy samoina, tämä käy hankalaksi.




Avahi
===============================

Nykyisissä Linux-järjestelmissä on yleensä oletuksena käytössä järjestelmä nimeltä
*Avahi*. Se asettaa lähiverkkoasetukset automaattisesti
[Zeroconf](https://en.wikipedia.org/wiki/Zero-configuration_networking)-toteutuksella.
Mac-maailmassa vastaava tunnetaan nimellä Bonjour.

* Kukin kone tietää oman nimensä ja tarjoamansa palvelut sekä osaa kertoa ne
  Avahin avulla muille saman verkon koneille
* Voidaan käyttää nimeä `koneennimi.local` pelkän ip-numeron sijaan.
* Helpottaa silloin, kun koneet saavat ip-osoitteensa dynaamisesti DHCP-palvelimelta
  eikä niillä siksi ole aina samaa ip-numeroa.

Avahia käytettäessä siis ei tarvitse pitää lähiverkon koneiden nimiä yllä
`/etc/hosts`-tiedostossa, sillä kukin kone kertoo itse automaattisesti
olemassaolostaan ja nimestään toisille koneille.

Pingataan taas `hessu`-konetta, mutta tällä kertaa nimellä `hessu.local`, jonka
sen Avahi on esitellyt meille:

```
$ ping hessu.local
PING hessu.local (192.168.0.29) 56(84) bytes of data.
64 bytes from hessu (192.168.0.29): icmp_seq=1 ttl=64 time=1.14 ms
64 bytes from hessu (192.168.0.29): icmp_seq=2 ttl=64 time=1.03 ms
^C
--- hessu.local ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.037/1.091/1.145/0.054 ms
```



Ssh-yhteys
===============================

*Ssh* on tekstipohjainen salattu komentoriviyhteys toiseen koneeseen.

* Kohdekoneella oltava ssh-palvelin päällä
* Yhteys komennolla: `ssh kayttajatunnus@etakone`
* Kysyy salasanan ja päästää komentoriville
* Ssh korvasi 90-luvulla salaamattoman ja turvattoman *telnet*-yhteyden.
* Myös ssh on kehitetty alkujaan Suomessa. (Tatu Ylönen)

Linux-jakeluissa ssh-asiakasohjelma on oletuksena asennettuna. Ssh-palvelimen voi
asentaa paketinhallinnasta. Ubuntussa asennettava paketti on nimeltä `openssh-server`.

***Huomio!*** Palvelimen asentaminen on aina lisäriski, eli varmistathan, että
salasanasi on kunnollinen ja asennat päivitykset säännöllisesti.

Kun koneelta *a* otetaan ensimmäistä kertaa ssh-yhteys koneelle *b*, ssh näyttää
koneen *b* ssh-palvelimen *sormenjäljen*, eli merkkijonotunnisteen. Tämän avulla
käyttäjä voi ensimmäisellä kerralla halutessaan varmistua siitä, että ollaan ottamassa
yhteyttä oikeaan koneeseen. Kun sormenjälki on kerran hyväksytty oikeaksi, se muistetaan
eikä siitä kysytä enää seuraavilla kerroilla.

```no-highlight
$ ssh ubuntu@hessu.local
The authenticity of host 'hessu.local (192.168.0.29)' can't be established.
ECDSA key fingerprint is SHA256:bNe0Yzd/iuDMZjlgvvVw3XCHzhDb+2abHNbOiaDA2sY.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'hessu.local' (ECDSA) to the list of known hosts.
ubuntu@hessu.local's password:
Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 4.4.0-31-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

ubuntu@hessu:~$
```

Yllä esitetyn kaltaisen ECDSA-avaimen sormenjäljen oikean arvon voi tarkistaa
palvelimella suorittamalla alla olevan komennon ja vertaamalla tulostusta
yhteyden otossa näytettävään sormenjälkeen. Oikea sormenjälki pitää tietenkin
saada palvelimelta jollain muulla keinolla ennen yhteydenottoa.

```
$ ssh-keygen -l -f  /etc/ssh/ssh_host_ecdsa_key.pub
256 SHA256:bNe0Yzd/iuDMZjlgvvVw3XCHzhDb+2abHNbOiaDA2sY root@hessu (ECSDA)
```

Lisää tietoa oikean sormenjäljen varmistamisesta löytyy esimerkiksi
artikkelista [Checking ssh public key fingerpirints][FingerprintCheck].


Tiedostonsiirto
===============================

Tiedostoja voidaan siirtää koneiden välillä esimerkiksi *Samba*- ja *Sftp*-protokollilla

Samba on Windows-verkosta tuttu smb-protokolla, eli se, josta Windowsissa
käytetään nimeä "verkkoympäristö".

* Samassa verkossa jaettuja levyjä ja tulostimia voidaan käyttää
* Omien jakaminen vaatii palvelun asentamisen omalle koneelle

Sftp toimii ssh-palvelimen kautta

* Vaatii ssh-palvelimen asentamisen kohdekoneelle, jotta sen tiedostoihin pääsee käsiksi.
* Käyttäjä pääsee käsiksi kaikkiin tiedostoihin, joihin pääsisi paikallisesti kirjautumalla
* Korvaa salaamattoman ftp-yhteyden esimerkiksi useissa webbihotelleissa keinona siirtää
  tiedostoja palvelimelle.

Windowsissa toimivia graafisia sftp-asiakasohjelmia ovat esimerkiksi
[WinSCP](https://winscp.net/eng/index.php), [FileZilla](https://filezilla-project.org/)
ja Firefoxin lisäosana toimiva [FireFTP](http://fireftp.net/)




Graafisesti
===============================

{{< figure src="/images/ubuntu-samba-share.png" link="/images/ubuntu-samba-share.png" class="floatright floatimage" title="Samba-jako" caption="Windows-verkon jakoja voi selata tiedostohallinnan Network-osiosta." >}}
{{< figure src="/images/ubuntu-samba-share2.png" link="/images/ubuntu-samba-share2.png" class="floatright floatimage" title="Samba-jako osoitteena" caption="Samba-osoitteen voi kirjoittaa suoraan osoiteriville." >}}

Samba- ja ssh/sftp-protokollia voi käyttää suoraan useimmilla Linuxissa tarjolla olevilla
graafisilla tiedostonhallintaohjelmilla. Tiedostojakoon yhdistämisen jälkeen useimmat
näistä näyttävät jaon ikkunan vasemmassa reunassa samaan tapaan kuin esimerkiksi
koneeseen liitetyn usb-levyn.

Samba
------

Useimmista tiedostonhallintaohjelmista löytyy "Network"-valinta, jonka alta löytyvät nykyisen
(lähi)verkon Windows-verkon palvelut, kuten levyjaot.

Windows-jakoon voi viitata myös suoraan osoitteella `smb://koneennimi/jako`. Osoitteen
pääsee kirjoittamaan tiedostohallintaohjelman osoiteriville pikanäppäimellä `ctrl-l`, eli
samalla, joka toimii www-selaimissakin.

Kolmas tapa yhdistää palvelimeen on joissain tiedostohallintaohjelmissa tarjolla oleva
valinta "Connect to Server", joka kysyy osoitteen, johon halutaan yhdistää.

{{< figure src="/images/ubuntu-ssh-share.png" link="/images/ubuntu-ssh-share.png" class="floatright floatimage" title="Ssh-yhteys" caption="Ssh-yhteys 'Connect to Server' -valinnalla." >}}
{{< figure src="/images/ubuntu-ssh-share-fingerprint.png" link="/images/ubuntu-ssh-share-fingerprint.png" class="floatright floatimage" title="Ssh-sormenjälki" caption="Käyttäjälle näytetään ssh-palvelimen sormenjälki ja varmistetaan, että tämä haluaa yhdistää." >}}
{{< figure src="/images/ubuntu-ssh-share-password.png" link="/images/ubuntu-ssh-share-password.png" class="floatright floatimage" title="Salasana" caption="Salasanan kysyminen käyttäjältä ja sen muistamisen valinta." >}}

Ssh / sftp
------

Ssh:lla yhteyden voi muodostaa toiselle koneelle vastaavasti osoitteella `sftp://koneennimi`. Joissain
ohjelmissa voidaan käyttää myös osoitetta `ssh://koneennimi` tai `fish://koneennimi`.
Sambaan yhdistämisen tavoin tämän osoitteen voi kirjoittaa joko ohjelman osoitekenttään
tai "Connect to Server" -kenttään.

* sftp: Palvelinpuolella erillinen sftp-server-ohjelma, jonka kanssa asiakas juttelee ssh:n läpi.
  Ssh hoitaa tunnistautumisen ja kryptaamisen.
* fish: Käyttää palvelinpuolella normaaleja komentorivityökaluja hakemistolistauksen näyttämiseen,
  tiedostojen poistamiseen yms. Toimii myös, kun ei ole sftp-server-ohjelmaa, mutta vaatii mahdollisuuden
  ajaa komentoriviohjelmia (eli käyttäjällä lupa kirjautua sisään ssh:lla).




Komentoriviltä
===============================

Ssh-yhteyden yli voidaan kopioida tiedostoja myös kometorivillä `scp`-komennolla. Esimerkkejä:

Kopioidaan tiedosto **etäkoneelta paikalliseen hakemistoon** antamalla ensin etäosoitteessa
olevan tiedoston nimi ja sitten paikallisen kohdehakemiston nimi.
```no-highlight
scp kayttajanimi@etakone:/polku/tiedostoon/nimi.txt /polku/tiedostoon/talla/koneella/
```

Kopioidaan tiedosto **etäkoneelta paikalliselle** koneelle nykyiseen työhakemistoon **uudella tiedostonimellä**.

```no-highlight
scp kayttajanimi@etakone:/polku/tiedostoon/nimi.txt uusinimi.txt
```

Kopioidaan tiedosto **paikalliselta koneelta etäkoneelle** haluttuun hakemistoon uudella nimellä antamalla ensin
paikallisen tiedoston nimi tarvittavan absoluuttisen tai suhteellisen polun avulla ja sitten
uuden tiedoston etäosoite. (**absoluuttinen polku**)

```no-highlight
scp /polku/talla/koneella/nimi.txt kayttaja@etakone:/polku/toisella/uusinimi.txt
```

Kopioidaan tiedosto **paikalliselta koneelta etäkoneelle** haluttuun hakemistoon uudella nimellä. (**suhteellinen polku**)

```no-highlight
scp /polku/talla/koneella/nimi.txt kayttajanimi@etakone:hakemisto/alihakem/uusinimi.txt
```




Tehtäviä
========================

{{% wrapper class="exercises" %}}

Tehtävät 6
===============================

Tehtävien tekemiseen tarvitset palvelimen osoitteen, käyttäjätunnuksen ja salasanan.
(Annetaan kurssilla.)

Viimeistä tehtävää varten palvelimella on oltava käynnissä (Apache) www-palvelin.
Koosta vastauksistasi tiedosto `tehtava-6.zip`.

1. Selaa graafisella käyttöliittymällä esiin annettu sftp-osoite ja kopioi sieltä käyttäjätunnuksesi
   oman kotihakemiston Pictures-alihakemistosta yksi kuva omalle koneellesi.
2. Luo omalla koneellasi uusi tiedosto nimeltä `nimi.txt` ja kirjoita siihen oma nimesi.
    * Avaa terminaali ja kopioi tämä tiedosto scp-komennolla käsketylle palvelimelle kotihakemiston
      Documents-alihakemistoon.
    * Selaa graafisella tiedostohallinnalla tuo palvelinkoneen Documents-hakemisto näkyviin.
    * Ota kuvakaappaus, jossa näkyy hakemiston sisältö tiedostohallintaikkunassa sekä terminaalissa tehty kopiointi.
3. Ota terminaali-ikkunassa ssh-yhteys palvelimelle.
    * Siirry Documents-hakemistoon. (`cd Documents`)
    * Muuta `nimi.txt`-tiedoston oikeuksia `chmod`-komennolla niin, että käyttäjällä ja ryhmällä ovat luku-
      ja kirjoitusoikeudet, mutta muilla ei mitään oikeuksia.
    * Listaa hakemiston sisältö pitkässä muodossa `ls`-komennolla, jotta näet, että oikeudet ovat oikein.
    * Ota kuvakaappaus, jossa näkyvät terminaali-ikkunassa annetut komennot.
4. Paketoi ladattu kuvatiedosto ja otetut kuvakaappaukset zip-tiedostoon nimellä `tehtava-6.zip`.<br>
   (Ubuntussa ohjelma nimeltä **Archive Manager**)
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

[FingerprintCheck]: https://www.phcomp.co.uk/Tutorials/Unix-And-Linux/ssh-check-server-fingerprint.html (Checking ssh public key fingerprints)
