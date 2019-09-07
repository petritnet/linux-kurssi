+++
date = "2016-09-02T21:28:37+03:00"
title = "Asennus"
weight = 30
+++

Asennetaan Linux. Käytetään esimerkkinä Ubuntua.

**Huomio! Asenna vain koneelle, jolle sinulla on lupa asentaa!**

Linux-jakelun asentaminen
==========================

Linux-käyttöjärjestelmän asentaminen alkaa sillä, että hankitaan jostain asennettavaksi valitun *Linux-jakelun*
asennuslevy. Sen voi tyypillisesti ladata vapaasti *levykuvana*, eli iso-päätteisenä tiedostona, kyseisen jakelun
kotisivuilta tai joltain muulta sitä levittävältä sivustolta. Esimerkki: [Ubuntun lataussivu][Ubuntu Download]

Vaihtoehtoisesti asennuslevyjä voi saada esimerkiksi jonkin Linux-aiheisen lehden liitteenä. Tällaisia ovat esimerkiksi
monien markettien lehtihyllyillä myytävät [Linux Format] ja [Linux Magazine].

Jos asennusmedia on hankittu levykuvana, pitää se seuraavaksi polttaa (koosta riippuen) CD- tai DVD-levylle taikka
kirjoittaa USB-tikulle siihen käyttöön tarkoitetulla ohjelmalla. Esimerkiksi Ubuntu ohjeistaa Windows-käyttäjiä
käyttämään [Rufus USB Installer] -ohjelmaa. Mac-koneilla kirjoittaminen tapahtuu
Macin omalla [Disk Utility][Mac usb live] -ohjelmalla. Levyn voi kirjoittaa
myös [Ubuntussa][Ubuntu live creator].

Tämän jälkeen laitetaan levy tietokoneen DVD-asemaan tai USB-tikku USB-porttiin ja käynnistetään tietokone tältä
levyltä. Jotta tietokoneen saa käynnistettyä ulkoiselta medialta, voi joutua vaihtamaan käynnistysjärjestystä,
eli sitä, missä järjestyksessä tietokone etsii käynnistettävää käyttöjärjestelmää levyiltä. Tämä asetus on tyypillisesti
tietokoneen BIOS- tai UEFI-asetuksissa, joihin pääseminen riippuu käytetystä tietokonemallista.

- Uusimmissa Windows-koneissa USB-tikulta käynnistämisen tai UEFI-asetuksiin menemisen
  voi valita Windowsin kautta "palautusasetuksista".
- UEFI- tai BIOS-asetuksiin pääsee usein myös tietokoneen käynnistyksen yhteydessä
  jollain laitteen merkistä riippuvalla näppäimellä, kuten F1, F2, F10, F12 tai Del.
- Joissain malleissa voi myös valita väliaikaisen käynnistyslevyn. Esimerkiksi Lenovon
  pöytäkoneilla *Enter*-näppäin antaa valikon, josta valitsemalla *F12*-vaihtoehdon
  voi valita käynnistykseen käytettävän ulkoisen median.
- Nykyisissä UEFI-käynnistystä käyttävissä tietokoneissa saattaa joutua kytkemään
  UEFI:n käynnistysasetuksista pois päältä "Secure Boot" -kohdan, jotta tietokone
  suostuu käynnitymään USB-tikulta.

Kun tietokone on saatu käynnistettyä asennusmedialta, on loppu asennus lähinnä muutamaan kysymykseen vastaamista.
Varovainen kannattaa olla erityisesti kohdissa, joissa kysytään, mille levylle asennetaan ja asennetaanko
Linux-jakelu tietokoneessa jo mahdollisesti olevan muun käyttöjärjestelmän rinnalle vai korvataanko se.

Vaihtoehtoisesti Linuxin voi asentaa myös virtuaalikoneeseen. Tätä varten koneella täytyy olla jokin virtuaalikoneiden
hallintaan tarvittava ohjelmisto. Esimerkiksi [VirtualBox].

Kertauksena vaiheet ovat siis:

1. Hanki asennuslevy
2. Selvitä, miten tietokoneen saa käynnistymään asennuslevyltä.
3. Käynnistä tietokone asennuslevyltä.
4. Asenna.


Jakeluita
==========================

Koska Linux on vapaa käyttöjärjestelmäydin, ovat sen käyttäjät koonneet siitä ja muista tarvittavista
vapaista ohjelmista monia omaan käyttöönsä ja mieltymyksiinsä sopivia koosteita. Näitä kutsutaan
*jakelupaketeiksi* tai vain *Linux-jakeluiksi*. Ne sisältävät tyypillisesti Linux-ytimen lisäksi yhden
tai useamman työpöytäympäristön sekä varsin laajan koosteen erilaisia sovellusohjelmia toimisto-ohjelmista
ja webbiselaimista ohjelmointiympäristöihin.

{{< figure src="/images/Gnome-Ubuntu-desktop.png" link="/images/Gnome-Ubuntu-desktop.png" class="floatright floatimage" title="Ubuntun Gnome-työpöytä" >}}
{{< figure src="/images/Plasma-Kubuntu-desktop.png" link="/images/Plasma-Kubuntu-desktop.png" class="floatright floatimage" title="Kbuntun KDE Plasma -työpöytä" >}}
{{< figure src="/images/Pantheon-Elementaryos-desktop.png" link="/images/Pantheon-Elementaryos-desktop.png" class="floatright floatimage" title="Elementary OS ja Pantheon-työpöytä" >}}

Tunnettuja Linux-jakeluita ovat muun muassa:

* [Ubuntu](http://ubuntu.com)
* [Linux Mint](http://linuxmint.com)
* [Kubuntu](http://kubuntu.org)
* [Lubuntu](http://lubuntu.org)
* [Xubuntu](http://xubuntu.org)
* [ElementaryOS](http://elementaryos.org)
* [Fedora](http://fedoraproject.org/fi/)
* [openSUSE](http://opensuse.fi/)
* [Debian](http://www.debian.org)

Pitkä lista eri käyttöihin ja tyyleihin tarkoitetuista jakeluista löytyy esimerkiksi [DistroWatch](http://distrowatch.com/)-sivustolta.


Esimerkkinä Ubuntu
==========================

Yksi tämän hetken suosituimmista Linux-jakeluista on [Ubuntu](http://ubuntu.com).
Se on pyritty tekemään käyttäjäystävälliseksi. Sen asennuslevy sisältää käytettävän kokonaisuuden, eli
yleisimmin tarvittavat ohjelmat, kuten selain, sähköposti, tekstinkäsittely, kuvienkäsittely, pikaviestimet ja niin edelleen.

Ubuntu on käynnistettävissä ja kokeiltavissa suoraan asennuslevyltä niin kutsuttuna Live-levynä ilman asentamista.
Asentaminen on suoraviivaista ja helppoa. Sen voi tehdä suoraan Live-levyn työpöydältä samalla kun käyttää tietokonetta.

Ubuntu pohjautuu Debian GNU/Linux -jakeluun.



Ubuntun taustaa
==========================

{{< figure src="/images/Mark-Shuttleworth.jpg" class="floatright floatimage" title="Mark Shuttleworth" link="https://en.wikipedia.org/wiki/Mark_Shuttleworth" attrlink="https://en.wikipedia.org/wiki/File:Mark-Shuttleworth-Ubuntu-fr-Karmic.jpg" attr="Wikipedia, Nitot (CC-by-sa)" >}}

* **Ubuntu** on bantunkielinen sana, joka voidaan suomentaa: *"ihmiseltä ihmiselle"*. Sen voidaan ymmärtää tarkoittavan myös *"inhimillisyyttä toisia kohtaan"*.
* Ubuntu-jakelua tekevät yhdessä **Canonical-yhtiö** sekä **Ubuntu-yhteisö**. Canonical tarjoaa kaupallista tukea yrityksille sekä ohjaa Ubuntu kehityksen suuntaa.
* Canonicalin ja Ubuntun perusti eteläafrikkalainen [Mark Shuttleworth](http://en.wikipedia.org/wiki/Mark_Shuttleworth) rikastuttuaan myymällä aiemman yrityksensä 575 miljoonalla Yhdysvaltojen dollarilla.

Ubuntusta julkaistaan uusi päivitetty versio aina noin kuuden kuukauden välein, yleensä huhti- ja lokakuussa. Tuki näillä versioilla on vähintään yhdeksän kuukautta.
Kahden vuoden välein julkaistaan pidempään tuettu niin kutsuttu LTS-versio (Long Term Support). Näiden, yleensä
parillisen vuoden keväällä julkaistavien, versioiden tuki on viisi vuotta.
LTS-versioita suositellaan tavallisille käyttäjille ja yrityksille. Tiheämmin julkaistavat "väliversiot" on suunnattu lähinnä harrastajille ja kehittäjille.

Ubuntun versiot numeroidaan julkaisuvuoden ja kuukauden mukaan, esimerkiksi vuoden 2018 huhtikuussa julkaistu LTS-versio on
numeroltaan 18.04. Numeron lisäksi kullakin versiolla on kaksiosainen eläinaiheinen lempinimi, jonka alkukirjain etenee aakkosissa aina jokaisen
uuden version myötä. Esimerkiksi versio 18.04 on lempinimeltään "Bionic Beaver" ja keväällä 2019 julkaistu 19.04 on "Disco Dingo".


Asennuslevy
==========================

Kuten monen muunkin jakelun, myös Ubuntu asennuslevy on niin kutsuttu Live-levy.
Se on ladattavissa iso-levykuvana [Ubuntun kotisivuilta](http://ubuntu.com) tai
vaikka [Ubuntu Suomen](http://ubuntu-fi.org) sivuilta.
Ubuntu käynnistyy Live-levyltä suoraan työpöydälle ja se on siis kokeiltavissa
näin suoraan ilman asentamista.




CD:n / DVD:n poltto ja USB-tikun teko
==========================

Cd- tai dvd-levyä poltettaessa huomioitavaa:

* iso-tiedostoa ei polteta levylle tiedostona vaan valitaan poltto-ohjelmasta
*"polta levykuva"* tai *"burn image"*.

USB-tikkua tehtäessä voidaan seurata vaikka Ubuntun vaiheittaisia ohjeita:

* [Windowsille][Rufus USB Installer]
* [Macille][Mac usb live]
* [Ubuntulle][Ubuntu live creator]

Tikun kirjoittamiseen voi käyttää myös [balenaEtcher]-ohjelmaa, joka voi olla
tuttu esimerkiksi Abitti-tikkujen kirjoittamisesta.


Virtuaalikone
==========================

{{< figure src="/images/virtualbox.png" link="/images/virtualbox.png" class="floatright floatimage" title="VirtualBox" caption="Linux-järjestelmiä voi käyttää myös virtuaalikoneeseen asennettuna, esimerkiksi VirtualBoxilla." >}}

Asennus on mahdollista myös virtuaalikoneeseen, jolla on helppo kokeilla asentamista ja asennettua järjestelmää muuttamatta oman koneen levyosiointia.

* [Virtualbox](http://virtualbox.org/)
* Isäntäjärjestelmä, eli host, sekä virtuaalikoneessa ajettava vierasjärjestelmä, eli guest.
* Virtualboxin käyttöliittymällä helppo luoda uusia virtuaalikoneita ja -levyjä.
* Osaa käynnistää suoraan iso-levykuvatiedostosta. Ei tarvitse polttaa CD:lle/DVD:lle.




Ubuntun käynnistys asennuslevyltä
==========================

1. Tietokone täytyy saada käynnistymään cd-levyltä
2. BIOS- tai UEFI-asetukset tai muu boot-valikko
3. Asennuslevyn käynnistysvalikko esille "nuoli alas"-näppäimellä
4. Valikossa vaihtoehtoina:
    * Live-levy ("kokeile asentamatta")
    * Asennus suoraan ilman työpöytää
    * levyn tarkistus
    * muistin tarkistus

Lisäksi käynnistysvalikossa on myös:

* Mahdollisuus valita käytettävä näppäimistökartta ja kieli
* Muita käynnistysparametreja




Asentaminen
==========================

Jos asennuslevy on käynnistetty kokeilutilaan, eli Ubuntun työpöydälle, voidaan asennus
aloittaa työpöydällä olevaa käynnistyskuvaketta napsauttamalla.

Asennus tapahtuu muutamassa askeleessa ja se kysyy käyttäjältä mahdollisimman vähän.
Työpöytä ohjelmineen on asennuksen aikana käytettävissä vaikka verkkoselailuun tai
tarjolla oleviin ohjelmiin tutustumiseen.

Asennuskieliksi on tarjolla lukuisia vaihtoehtoja. Kielitukia voi asentaa lisää myös jälkeenpäin.

Ubuntun voi asentaa:

* Ainoaksi järjestelmäksi, jolloin se "jyrää" levyllä ennestään olevan datan tai käyttöjärjestelmän.
* Aiemman käyttöjärjestelmän (esimerkiksi Windows) rinnalle, jolloin käyttäjä voi tietokoneen käynnistyksen
  yhteydessä valita käynnistettävän järjestelmän.
* **Muulle levylle**

*Asennuslevyn valinnassa on aina oltava huolellinen!*
Asennuksen yhteydessä voi valita myös netistä saatavat päivitykset ja multimedia-koodekit




Käyttäjätunnukset
==========================

Ubuntussa, kuten kaikissa Linuxeissa ja Unixeissa, käyttäjien oikeudet rajattu käyttäjätunnuksen
mukaan. Pääkäyttäjätunnus, eli ylläpitotunnus, on Linux-järjestelmissä nimeltä *root*. Tämä vastaa
Windowsin *Administrator*-tunnusta.
Ubuntu-pohjaisissa järjestelmissä käyttäjä ei voi kirjautua sisään suoraan root-tunnuksella vaan
tavallinen käyttäjä voi hetkellisesti "lainata" root-käyttäjän oikeuksia käyttämällä *sudo*-komentoa.

* Ylläpitotehtäviä tekee tavallinen käyttäjä, jolle on annettu oikeus käyttää *sudo*-komentoa.
* *sudo* tarkoittaa: "superuser do"
* *sudo*:n käytön yhteydessä kysytään varmuudeksi käyttäjän omaa salasanaa.
* Järjestelmässä voi olla useampia käyttäjiä, joilla on sudo-oikeus, eli ylläpito-oikeus.

Tavallisilla käyttäjätunnuksilla (ilman sudo-oikeutta) ei ole oikeutta tehdä muutoksia
järjestelmän asetuksiin. Tavallinen käyttäjä voi muokata vain omia tiedostojaan.





Gnome-työpöytä
==========================

Ubuntu käyttää monessa muussakin Linux-jakelussa käytössä olevaa
Gnome-työpöytää. Ubuntussa sen ulkoasu näyttää seuraavalta:

* Vasemmalla panelissa:
    * käynnistyskuvakkeet,
    * käynnissä olevat ohjelmat
* Yläpalkissa:
    * valikko sammutukselle ja henkilökohtaisille asetuksille
    * kello
    * äänenvoimakkuus
    * wifi-valinnat
* Vasemmasta alakulmasta löytyy valikko, jolla pääsee hakemaan ja käynnistämään ohjelmia sekä tiedostoja.
* Ohjelmien valikot tulevat yläpalkkiin, kun hiiren vie sen päälle. (Tämä ominaisuus on säädettävissä.)

{{< figure src="/images/Gnome-Ubuntu-desktop.png" attr="The Gnome Project and Ubuntu" attrlink="https://www.gnome.org/" title="Gnome-työpöytä Ubuntussa" >}}







[Ubuntu Download]: https://www.ubuntu.com/download/desktop (Ubuntun lataus)
[Rufus USB Installer]: https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows (Rufus)
[Mac usb live]: https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos (Disk Utility)
[Ubuntu live creator]: https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu (Ubuntu)
[Linux Format]: http://www.linuxformat.com/ (Linux Format)
[Linux Magazine]: http://www.linux-magazine.com/ (Linux Magazine)
[VirtualBox]: https://www.virtualbox.org/ "VirtualBox"
[balenaEtcher]: https://www.balena.io/etcher/ (balenaEtcher)
