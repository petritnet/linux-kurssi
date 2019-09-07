+++
date = "2016-09-02T21:28:22+03:00"
title = "Historiaa"
weight = 10
+++

Mikä on Linux?
==============

> "Jotta voi kertoa, mikä on Linux, pitää ensin kertoa, mikä on käyttöjärjestelmä."
>
> – Linus Torvalds

Mikä on käyttöjärjestelmä?
==========================

[Käyttöjärjestelmä] on tietokonetta käynnistettäessä ensimmäinen ladattava
ohjelma tai ohjelmistokokonaisuus, joka:

- käynnistää muita ohjelmia ja
- tarjoaa niille resursseja ja palveluita, kuten
    - muistin käyttö
    - tiedostojen lukeminen ja kirjoittaminen levylle
    - syöte näppäimistöltä/hiireltä/muilta laitteilta
    - tulostus näytölle, tulostimelle
    - verkko
    - äänet sisään ja ulos
- jakaa ohjelmille suoritusaikaa

Tavallisten ohjelmien ei tällöin tarvitse huolehtia esimerkiksi laitteiston
erityispiirteistä vaan niiden toiminta saadaan käyttöjärjestelmältä palveluna.

> "Kukaan ei käytä käyttöjärjestelmää vaan ohjelmia."

Käyttöjärjestelmä on kuin entisaikojen brittiläinen palvelusväki: ei näy, mutta palvelu pelaa.

Linuxin synty
=============

{{< figure src="/images/Linus_Torvalds_cropped.jpeg" title="Linus Torvalds" attr="CC-BY-SA, Wikipedia, thumperward" link="http://commons.wikimedia.org/wiki/File:Linus_Torvalds_%28cropped%29.jpg" attrlink="http://commons.wikimedia.org/wiki/File:Linus_Torvalds_%28cropped%29.jpg" class="floatright floatimage" >}}

- [Linus Torvalds]
- Helsingin Yliopiston tietojenkäsittelytieteen opiskelija
- Oli hankkinut uuden 386-tietokoneen, muttei ollut tyytyväinen sen DOS-järjestelmään.
- Ihastui yliopistolla käytettyyn Unixiin ja halusi sellaisen myös omaan koneeseensa.
- Linux alkoi Minix käyttöjärjestelmän päälle rakennettuna terminaaliemulaattoriohjelmana, jolla hän sai yhteyden yliopiston Unix-koneeseen.
- Linux kasvoi vähitellen käyttöjärjestelmän ytimeksi.


Linuxin julkaisu
================

Linus kertoi 25.8.1991 projektistaan news-keskusteluryhmässä [comp.os.minix]

> Hello everybody out there using minix -
>
> I'm doing a (free) operating system (just a hobby, won't be big and professional like gnu) for 386(486) AT clones.
> This has been brewing since april, and is starting to get ready. I'd like any feedback on things people like/dislike in minix,
> as my OS resembles it somewhat (same physical layout of the file-system (due to practical reasons) among other things).
>
> I've currently ported bash(1.08) and gcc(1.40), and things seem to work. This implies that I'll get something practical within a few months,
> and I'd like to know what features most people would want. Any suggestions are welcome, but I won't promise I'll implement them :-)
>
> Linus (torvalds@kruuna.helsinki.fi)
> PS. Yes – it's free of any minix code, and it has a multi-threaded fs. It is NOT portable (uses 386 task switching etc),
> and it probably never will support anything other than AT-harddisks, as that's all I have :-(.
>
> —Linus Torvalds


Reaktiot
========

{{< figure src="/images/AndrewTanenbaum2.png" title="Andrew S. Tanenbaum" attr="CC-BY, Okura" attrlink="http://commons.wikimedia.org/wiki/File:AndrewTanenbaum2.png" link="http://commons.wikimedia.org/wiki/File:AndrewTanenbaum2.png" class="floatright floatimage" >}}

- Linux otettiin [innostuneesti vastaan][vastaanotto]
- MINIXin kehittänyt amerikkalainen, Amsterdamissa työskentelevä tietojenkäsittelytieteen professori Andrew S. Tanenbaum (AST)
  kommentoi: ["LINUX on vanhanaikainen"][AST-vastaus]
- Tanenbaumin kritiikin syyt:
   - Linux on [monoliittinen käyttöjärjestelmäydin][monoliittinen]. Hänen mielestään modernin ytimen piti olla [mikroydin][mikrokerneli], kuten Minixissä.
   - Linux ei ollut (vielä) ollut sovitettavissa kuin Intelin i386-prosessoreille ja Tanenbaumin mielestä RISC-prosessorit syrjättäisivät Intelin x86-sarjan ennen pitkää.

> "I still maintain the point that designing a monolithic kernel in 1991 is a fundamental error. Be thankful you are not my student.
> You would not get a high grade for such a design :-)"
>
> – Andrew S. Tanenbaum

Ytimien tyyppien paremmuudesta voidaan kiistellä, mutta toistaiseksi mikroydinten
kehitys on jäänyt vielä vähäiseksi 2000-luvulla. Mac OS X:n ydin on hybridi,
jossa on ominaisuuksia Mach-mikroytimestä ja BSD:n monoliittisesta ytimestä.
Esimerkiksi Nokian aiemmissa puhelinmalleissa käytetyssä Symbian-käyttöjärjestelmässä
oli mikroydin.

RISC-prosessorien käyttö puolestaan väheni ja Intelin x86-yhteensopivat
prosessorit yleistyivät. Kuitenkin nykyään RISC-tyyppiset ARM-prosessorit ovat
nousseet jälleen suureen suosioon erityisesti mobiililaitteiden ja
kodin älykkään elektroniikan myötä.


Linus vastaa
=============

Arvostetun professorin kritiikki varmasti säväytti, mutta Torvalds oli jo silloin
jääräpäinen ja suorasanainen:

> Your job is being a professor and researcher: That's one hell of a good excuse for some of the brain-damages of minix.
>
> – Linus Torvalds to Andrew Tanenbaum


Oikea hetki
============

{{< figure src="/images/kello.png" class="floatright floatimage" >}}

Linux syntyi juuri oikealla hetkellä tai juuri siksi, että hetki oli oikea.

- [Richard M. Stallman][RMS] ja [GNU-projekti][GNU]
- Berkeleyn yliopiston Berkeley Software Distribution (BSD)
- BSD:llä tekijänoikeusoikeudenkäynti
- Inteliltä 32-bittinen i386-prosessori
- MINIX opettamiseen ja akateemiseen käyttöön
- Jos ei Linux, niin ehkä FreeBSD tai GNU/HURD?

Richard M. Stallmanin vetämä [GNU-projekti][GNU] pyrki luomaan vapaan Unix-tyyppisen
käyttöjärjestelmän. Muut osat olivat jo, mutta ytimeksi suunniteltu HURD oli vielä kesken.

Berkeleyn yliopiston kehittämä Unix-järjestelmä, [Berkeley Software Distribution] (BSD),
oli vapaa ja ilmainen, mutta juuri tuolloin ongelmissa tekijänoikeusoikeudenkäynnin takia.
Oikeudenkäynti AT&T:n kanssa ratkesi myöhemmin BSD:n hyväksi.

Intel oli muutamaa vuotta aiemmin julkaissut 32-bittisen i386-prosessorin,
joka oli teknisesti hyvä alusta Unix-tyyppiselle järjestelmälle.

MINIX sopi opetukseen ja akateemiseen käyttöön, mutta sen muokkaamiseen ja
levitykseen ei ollut tarpeeksi oikeuksia. Lisäksi se oli 16-bittinen ja
opetustarkoituksen vuoksi suunniteltu tarkoituksella yksinkertaiseksi.

Jos Linuxia ei olisi tullut, sen paikan olisi luultavasti ottanut hieman
myöhemmin esimerkiksi BSD-pohjainen FreeBSD tai GNU/HURD. Nyt Linux kuitenkin
houkutteli kiinnostuneet ohjelmoijat mukaan kehitykeen ja BSD sekä HURD jäivät
vähemmälle huomiolle. BSD:stä ovat sittemmin kehittyneet mm. FreeBSD, OpenBSD,
NetBSD. Myös Mac OS X sisältää joitain FreeBSD:stä peräisin olevia osia.

GNU/HURD:in kehitys on ollut hidasta ja on jäänyt selvästi Linuxin suosion varjoon.


GNU (Gnu is Not Unix)
=====================

{{< figure src="/images/Richard_Stallman_at_Pittsburgh_University.jpg" class="floatright floatimage" attr="CC-BY-SA, Wikipedia, Victor Powell" attrlink="http://en.wikipedia.org/wiki/File:Richard_Stallman_at_Pittsburgh_University.jpg" title="Richard M. Stallman" link="http://en.wikipedia.org/wiki/File:Richard_Stallman_at_Pittsburgh_University.jpg" >}}

- [GNU-projektin][GNU.org] nimi tulee sanoista GNU is Not Unix.
- Pyrkii luomaan vapaan käyttöjärjestelmän nimeltä GNU.
- [Richard M. Stallman][RMS] projektin johdossa.
- [Free Software Foundation][FSF] (FSF)
- HURD-ydin on yhä kesken.
- Linux sopi hyvin yhteen GNU-projektin muiden työkalujen kanssa.
- Erityisesti Richard Stallman muistuttaa aina, että käyttöjärjestelmästä pitäisi
  käyttää nimeä *GNU/Linux*.


Lisenssi
========

{{< figure src="/images/copyleft.svg" class="floatright floatimage" title="Copyleft" >}}

Linux on julkaistu GNU-projektin [GNU GPL][GNU GPL] -lisenssillä (GNU General Public License),
joka on niin kutsuttu *Copyleft*-lisenssi. Copyleft-lisenssi jättää käyttäjälle
enemmän oikeuksia kuin normaali tekijänoikeus (Copyright) antaisi.
Käyttäjä saa vapaasti:

1. käyttää ohjelmaa mihin tahansa tarkoitukseen
2. opiskella ohjelman toimintaa ja soveltaa/muokata sitä
3. levittää kopioita muille
4. parantaa ohjelmaa ja antaa muutokset levitykseen, jotta koko yhteisö hyötyy



Vapaa vs. ilmainen
==================
Englannin kielen sana **free** on tässä yhteydessä huono, sillä se tarkoittaa
sekä vapaata että ilmaista. GPL-lisensoidut ohjelmistot ovat **vapaita** ja
Stallmanin sanoin:

> "Free as in free speech, not free as in free beer."

- Ilmaisia ohjelmia ei välttämättä voi vapaasti muokata ja levittää.
- Vapaista ohjelmia voi halutessaan vapaasti myös myydä, jos joku maksaa.



Vapaa vs. avoin
===============
Vapaiden ja avoimen lähdekoodin ohjelmistojen (VALO) käyttöön on usein kaksi
eri näkökulmaa ja toisinaan kannattajat jakautuvat näihin kahteen leiriin.

- **Vapaista** ohjelmista puhuvat painottavat ideologista puolta.
   - [Richard M. Stallman (RMS)][RMS]
   - [Free Software Foundation][FSF]
   - ohjelmakoodin vapaus **moraalisesti** tärkeää
   - näkemykset usein jyrkempiä
- **Avoimesta** lähdekoodista puhuvat painottavat käytännön sovelluksia.
   - [Eric S. Raymond (ESR)][ESR]
   - [Open Source Initiative][OSI]
   - lähdekoodin avoimuus tärkeää teknisistä ja **käytännöllisistä** syistä,
     ei ideologisista
   - "Avoimen lähdekoodin menetelmät tuottavat parempia ohjelmia."

Usein puhutaan VALOista tai FLOSS-ohjelmista (Free/Libre, Open Source Software),
kun ei haluta ottaa kantaa näiden kahden suuntauksen välillä.



Miksi Linux on vapaa?
=====================
Linux on selvästi menestynyt. Miksi Linus Torvalds julkaisi sen avoimena
lähdekoodina eikä lyönyt rahoiksi?

- Linux on menestynyt, koska se on vapaa ja avoin.
- Maksullisena se olisi luultavasti ollut vain yhden suomalaisen yliopisto-opiskelijan
  "kyhäelmä", mutta vapaana se on levinnyt ja suuri joukko muita on osallistunut
  sen kehittämiseen.
- Koska Linux on vapaa, myös monet suuret tai pienet yritykset ovat osallistuneet kehitykseen
  tuoden oman kortensa kekoon ja samalla hyötyen siitä itse. Esimerkiksi:
  Red Hat, Canonical, Intel, IBM



Mistä nimi?
===========
Onko Linus itsekeskeinen, kun valitsi nimeksi Linux?

- Linus oli ajatellut nimeksi Freax, yhdistelmä sanoista friikki (freak),
  vapaa (free) ja unix (X).
- Linus oli harkinnut nimeä Linux, mutta piti sitä liian egoistisena.
- Linusin työkaveri [Ari Lemmke] antoi Helsingin yliopiston ftp-palvelimelta
  tilaa projektin lähdekoodeille, eikä pitänyt nimestä Freax,
  joten hän laittoi Linusilta kysymättä hakemiston nimeksi Linux.

> "I am egoistic bastard, first I named Linux after myself and then Git"
>
> – Linus Torvalds


Mikä on käyttöjärjestelmä?
==========================
Käyttöjärjestelmä on tietokoneohjelma tai kokonaisuus, joka käynnistyy ensimmäisenä
ja käynnistää ja palvelee muita ohjelmia.

- Se tarjoaa muiden ohjelmien käyttöön levyt, tiedostojärjestelmät, verkon, yms. laitteet.
- Ohjelmat eivät itse pääse käsiksi laitteisiin vaan pyytävät kaiken käyttöjärjestelmältä.

Onko Linux käyttöjärjestelmä?
=============================

- Toisten mielestä: Kyllä, se täyttää käyttöjärjestelmän tehtävät yksinään.
- Toisten mielestä: Ei, se on vain käyttöjärjestelmän ydin. Käyttöjärjestelmä on
  Linux + muutamia muita ohjelmia yhdessä.

Käytännössä pelkällä Linux-ytimellä ei kuitenkaan tee mitään vaan sen lisäksi
tarvitaan muukin kokonaisuus.


Linux-jakelut
=============
Linux-toimitetaan yleensä jakelupaketteina, eli distribuutioina.

- Debian, Ubuntu, Mint, Elementary OS
- Red Hat Enterprise Linux, CentOS, Fedora
- openSUSE, Arch, Mageia,...

Jakelupaketissa on koottu yhdeksi paketiksi asennettavaksi kokonaisuus:
Linux-ydin, muut järjestelmän oleelliset osat, paketinhallinta, asetukset,
graafiset käyttöliittymät ja läjäpäin ohjelmia.
Osa jakelupaketeista on aloittanut ohjelmistojen kasaamisen alusta, suurin
osa pohjautuu johonkin aiempaan.

[Sukupuu](/images/gldt1210.svg)



Kaupalliset jakelut vs. yhteisölliset jakelut
==============================================
Jakelupaketteja kootaan kaupallisesti palkatulla väellä tai yhteisöllisesti vapaaehtoisvoimin. Toisinaan yritysten ja yhteisöjen välillä on rinnakkaista yhteistyötä. Esimerkiksi:

- **[Fedora]**: Yhteisön voimin rakennettu jakelu.
- **[Red Hat Enterprise Linux][RHEL]**: Fedoraan pohjautuva Red Hat -yhtiön kaupallisesti
  tuettu versio.
- **[CentOS]**: RHEL:in kanssa yhteensopiva yrityskäyttöön suunnattu yhteisön kasaama
  jakelu ilman Red Hatin brändäystä ja tukea. Nykyään myös Red Hatin omistama.
- **[Debian]**: Täysin yhteisöllisesti toimiva projekti ja jakelu.
- **[Ubuntu]**: Canonical-yhtiön ja Ubuntu-yhteisön yhdessä Debianin pohjalta kehittämä jakelu.
- **[Linux Mint]**: Yhteisövetoinen jakelu, joka pohjautuu Ubuntuun.
- **[Elementary OS]**: Ubuntuun pohjautuva kaupallisesti kehitettävä jakelu.



Linuxin levinneisyys
====================
Linuxin työpöytävalloitusta odoteltaessa se on valloittanut:

- palvelimet
- supertietokoneet
- digiboxit ja älytelevisiot
- puhelimet
   - Googlen ja kumppaneidensa Android
   - ~~Nokian Maemo ja MeeGo~~
   - Jollan SailfishOS
   - Intel ja Samsung: Tizen
   - Samsungin Bada
   - ~~Canonicalin Ubuntu Phone~~
   - ~~Mozillan Firefox OS~~
- tabletit (Android, WebOS)
- älykellot
- reitittimet
- gps-navigaattorit
- mainosnäytöt
- rahapelikoneet
- lypsykoneet

{{< youtube xPbAXKMCDkY >}}




Linux muutakin kuin komentorivi
===============================

On yleinen harhaluulo, että Linux olisi yhtä kuin musta ruutu, vaaleaa tekstiä ja vaikeasti muistettavia komentoja.

- X window system tai Wayland antaa graafisen tilan
- Näiden päällä useita vaihtoehtoisia käyttöliittymiä
    - Gnome-työpöytä
    - KDE Plasma-työpöytä
    - XFCE-työpöytä
    - LXDE-työpöytä
    - Cinnamon-työpöytä (Linux Mint)
    - MATE-työpöytä
    - Pantheon-työpöytä
    - Useita ikkunanhallintaohjelmia (Enlightenment, Blackbox, ...)
- Useita rinnakkaisia virtuaalityöpöytiä
- Yksittäisiä ohjelmia tai koko työpöytää voi ajaa etänä verkon yli.


{{< figure src="/images/Gnome-Ubuntu-desktop.png" attr="The Gnome Project and Ubuntu" attrlink="https://www.gnome.org/" title="Gnome-työpöytä Ubuntussa" >}}
{{< figure src="/images/Gnome-Fedora-desktop.png" attr="The Gnome Project and Fedora" attrlink="https://www.gnome.org/" title="Gnome-työpöytä Fedorassa" >}}
{{< figure src="/images/Plasma-Kubuntu-desktop.png" attr="KDE Plasma and Kubuntu" attrlink="https://kde.org/" title="KDE Plasma-työpöytä Kubuntussa" >}}
{{< figure src="/images/xfce-xubuntu-desktop.png" attr="XFCE and Xubuntu" attrlink="https://xfce.org/" title="XFCE-työpöytä Xubuntussa" >}}
{{< figure src="/images/Pantheon-Elementaryos-desktop.png" attr="Pantheon and Elementary OS" attrlink="https://elementary.io/" title="Pantheon-työpöytä Elementary OS:ssä" >}}
{{< figure src="/images/Cinnamon-Mint-desktop.png" attr="Cinnamon and Linux Mint" attrlink="https://linuxmint.com/" title="Cinnamon-työpöytä Linux Mintissä" >}}


{{< youtube WVTWCPoUt8w >}}


Tehtäviä
===========

{{% wrapper class="exercises" %}}
Tehtävät 1
===========

Kuvakaappauksen voi ottaa *PrintScreen*-näppäimellä. Palauta vastauksesi annettuun sähköpostiosoitteeseen.

- Käynnistä DVD:ltä tai USB-tikulta jokin seuraavista: Ubuntu, Kubuntu, Lubuntu, Linux Mint, ElementaryOS tai Fedora.
- Tutki, minkä niminen tekstinkäsittelyohjelma löytyy.
- Entä mikä on nimeltään oletuksena tarjolla oleva www-selain?
- Kirjoita vastaus tekstinkäsittelyohjelmalla ja tallenna nimellä `tehtava-1.*`. (Missä pääte `*` on ohjelman oletustallennusmuoto.)
{{% /wrapper %}}



[Käyttöjärjestelmä]: https://fi.wikipedia.org/wiki/K%C3%A4ytt%C3%B6j%C3%A4rjestelm%C3%A4 "Käyttöjärjestelmä – Wikipedia"
[Linus Torvalds]: https://fi.wikipedia.org/wiki/Linus_Torvalds "Linus Torvalds"
[comp.os.minix]: https://groups.google.com/forum/#!msg/comp.os.minix/dlNtH7RRrGA/SwRavCzVE7gJ "Hello everybody outh there using minix -"
[vastaanotto]: https://groups.google.com/d/msg/comp.os.minix/dlNtH7RRrGA/SwRavCzVE7gJ "comp.os.minix"
[AST-vastaus]: https://groups.google.com/d/msg/comp.os.minix/wlhw16QWltI/XdksCA1TR_QJ "Andrew S. Tanenbaum"
[mikrokerneli]: http://en.wikipedia.org/wiki/Microkernel "Mikrokerneli"
[monoliittinen]: http://en.wikipedia.org/wiki/Monolithic_kernel "Monoliittinen kerneli"
[RMS]: http://fi.wikipedia.org/wiki/Richard_Stallman "Richard M. Stallman – Wikipedia"
[GNU]: http://en.wikipedia.org/wiki/GNU_project "GNU-projekti – Wikipedia"
[GNU.org]: https://www.gnu.org/ "GNU.org"
[FSF]: http://www.fsf.org/ "Free Software Foundation"
[GNU GPL]: https://www.gnu.org/licenses/gpl.html "GNU GPL"
[ESR]: https://en.wikipedia.org/wiki/Eric_S._Raymond "Eric S. Raymond – Wikipedia"
[OSI]: https://opensource.org/ "Open Source Initiative"
[Berkeley Software Distribution]: https://en.wikipedia.org/wiki/Berkeley_Software_Distribution "BSD – Wikipedia"
[Ari Lemmke]: https://fi.wikipedia.org/wiki/Ari_Lemmke "Ari Lemmke – Wikipedia"

[RHEL]: https://redhat.com/rhel "Red Hat Enterprise Linux"
[Fedora]: https://getfedora.org/ "Fedora"
[CentOS]: https://www.centos.org/ "CentOS"
[Debian]: https://www.debian.org/ "Debian"
[Ubuntu]: https://ubuntu.com/ "Ubuntu"
[Linux Mint]: https://www.linuxmint.com/ "Linux Mint"
[Elementary OS]: https://elementary.io/ "Elementary OS"
