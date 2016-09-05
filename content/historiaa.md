+++
date = "2016-09-02T21:28:22+03:00"
title = "Historiaa"
weight = 1
+++

Mikä on Linux?
==============

> "Jotta voi kertoa, mikä on Linux, pitää ensin kertoa, mikä on käyttöjärjestelmä."
>
> – Linus Torvalds

Mikä on käyttöjärjestelmä?
==========================

Tietokonetta käynnistettäessä ensimmäinen ladattava ohjelma, joka:

- käynnistää muita ohjelmia ja
- tarjoaa niille palveluita, kuten
    - tiedostojen lukeminen ja kirjoittaminen levylle
    - syöte näppäimistöltä/hiireltä/muilta laitteilta
    - tulostus näytölle, tulostimelle
    - verkko
    - äänet sisään ja ulos
- jakaa ohjelmille suoritusaikaa

> "Kukaan ei käytä käyttöjärjestelmää vaan ohjelmia."

Käyttöjärjestelmä on kuin brittiläinen palvelusväki: ei näy, mutta palvelu pelaa.

Linuxin synty
=============

{{< figure src="/images/Linus_Torvalds_cropped.jpeg" title="Linus Torvalds" attr="CC-BY-SA, thumperward" link="http://commons.wikimedia.org/wiki/File:Linus_Torvalds_%28cropped%29.jpg" attrlink="http://commons.wikimedia.org/wiki/File:Linus_Torvalds_%28cropped%29.jpg" class="floatright floatimage" >}}

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

Ytimien tyyppien paremmuudesta voidaan kiistellä, mutta toistaiseksi mikroydinten kehitys on jäänyt vielä vähäiseksi 2000-luvulla. Mac OS X:n ydin on hybridi,
jossa on ominaisuuksia Mach-mikroytimestä ja BSD:n monoliittisesta ytimestä. Esimerkiksi Nokian aiemmissa puhelinmalleissa käytetyssä Symbian-käyttöjärjestelmässä oli mikroydin.

RISC-prosessorien käyttö puolestaan vähentyi ja Intelin x86-yhteensopivat prosessorit yleistyivät. Nykyään RISC-tyyppiset ARM-prosessorit ovat olleet jälleen nousussa muun muassa
mobiililaitteiden ja kodin elektroniikan myötä.


Linus vastaa
=============

Arvostetun professorin kritiikki varmasti säväytti, mutta Torvalds oli jo silloin jääräpäinen ja suorasanainen:

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

Richard M. Stallmanin vetämä GNU-projekti pyrki luomaan vapaan Unix-tyyppisen käyttöjärjestelmän. Muut osat olivat jo, mutta ytimeksi suunniteltu HURD oli vielä kesken.

Berkeleyn yliopiston kehittämä Unix-järjestelmä, Berkeley Software Distribution (BSD), oli vapaa ja ilmainen, mutta juuri tuolloin ongelmissa tekijänoikeusoikeudenkäynnin takia.

Intel oli muutamaa vuotta aiemmin julkaissut 32-bittisen i386-prosessorin, joka oli teknisesti hyvä alusta Unix-tyyppiselle järjestelmälle.

MINIX sopi opetukseen ja akateemiseen käyttöön, mutta sen muokkaamiseen ja levitykseen ei ollut tarpeeksi oikeuksia.
Lisäksi se oli 16-bittinen ja tarkoituksella suunniteltu yksinkertaiseksi.

Jos Linuxia ei olisi tullut, sen paikan olisi luultavasti ottanut hieman myöhemmin esimerkiksi BSD-pohjainen FreeBSD tai GNU/HURD.
Nyt Linux kuitenkin houkutteli kiinnostuneet ohjelmoijat mukaan ja BSD sekä HURD jäivät vähemmälle huomiolle. 
BSD:stä ovat sittemmin kehittyneet mm. FreeBSD, OpenBSD, NetBSD. Myös Mac OS X sisältää joitain FreeBSD:stä peräisin olevia osia.

GNU/HURD:in kehitys on ollut hidasta ja on jäänyt selvästi Linuxin varjoon.


GNU (Gnu is Not Unix)
=====================

{{< figure src="/images/Richard_Stallman_at_Pittsburgh_University.jpg" class="floatright floatimage" attr="CC-BY-SA, Victor Powell" attrlink="http://en.wikipedia.org/wiki/File:Richard_Stallman_at_Pittsburgh_University.jpg" title="Richard M. Stallman" link="http://en.wikipedia.org/wiki/File:Richard_Stallman_at_Pittsburgh_University.jpg" >}}

- GNU-projektin nimi tulee sanoista GNU is Not Unix.
- Pyrkii luomaan vapaan käyttöjärjestelmän nimeltä GNU.
- Richard M. Stallman projektin johdossa.
- [Free Software Foundation][FSF] (FSF)
- HURD-ydin on vieläkin kesken.
- Linux sopi hyvin yhteen GNU-projektin työkalujen kanssa.
- Erityisesti Richard Stallman muistuttaa aina, että käyttöjärjestelmästä pitää käyttää nimeä *GNU/Linux*.


Lisenssi
========

{{< figure src="/images/copyleft.svg" class="floatright floatimage" title="Copyleft" >}}

Linux on julkaistu GNU-projektin [GNU GPL][GNU GPL] -lisenssillä (GNU General Public License), joka on niin kutsuttu *Copyleft*-lisenssi. Copyleft-lisenssi jättää käyttäjälle enemmän oikeuksia kuin normaali tekijänoikeus (Copyright) antaisi. Käyttäjä saa vapaasti:

1. käyttää ohjelmaa mihin tahansa tarkoitukseen
2. opiskella ohjelman toimintaa, ja soveltaa sitä,
3. levittää kopioita muille,
4. parantaa ohjelmaa, ja antaa muutokset levitykseen, jotta koko yhteisö hyötyy.



Vapaa vs. ilmainen
==================
Englannin kielen sana free on tässä yhteydessä huono, sillä se tarkoittaa sekä vapaata että ilmaista. GPL-lisensoidut ohjelmistot ovat Stallmanin sanoin:

> "Free as in free speech, not free as in free beer."

- Ilmaisia ohjelmia ei välttämättä voi vapaasti muokata ja levittää.
- Vapaista ohjelmia voi halutessaan vapaasti myös myydä, jos joku maksaa.



Vapaa vs. avoin
===============
Vapaiden ja avoimen lähdekoodin ohjelmistojen (VALO) käyttöön on usein kaksi eri näkökulmaa ja joskus kannattajat jakautuvat näihin kahteen leiriin.

- Vapaista ohjelmista puhuvat painottavat ideologista puolta.
   - Richard M. Stallman (RMS)
   - [Free Software Foundation][FSF]
   - ohjelmakoodin vapaus tärkeää
   - näkemykset usein jyrkempiä
- Avoimesta lähdekoodista puhuvat painottavat käytännön sovelluksia.
   - Eric S. Raymond (ESR)
   - [Open Source Initiative][OSI]
   - lähdekoodin avoimuus tärkeää teknisistä ja käytännöllisistä syistä, ei ideologisista
   - "Avoimen lähdekoodin menetelmät tuottavat parempia ohjelmia."

Usein puhutaan VALOista tai FLOSS-ohjelmista (Free/Libre, Open Source Software), kun ei haluta ottaa kantaa.



Miksi Linux on vapaa?
=====================
Linux on selvästi menestynyt. Miksi Linus Torvalds julkaisi sen avoimena lähdekoodina eikä lyönyt rahoiksi?

- Linux on menestynyt, koska se on vapaa ja avoin.
- Maksullisena se olisi ollut vain yhden suomalaisen yliopisto-opiskelijan "räpellys", mutta vapaana se on levinnyt ja muut ovat osallistuneet sen kehittämiseen.



Mistä nimi?
===========
Onko Linus itsekeskeinen, kun valitsi nimeksi Linux?

- Linus oli ajatellut nimeksi Freax, yhdistelmä sanoista friikki (freak), vapaa (free) ja unix (X).
- Linus oli harkinnut nimeä Linux, mutta piti sitä liian egoistisena.
- Linusin työkaveri Ari Lemmke antoi Helsingin yliopiston ftp-palvelimelta tilaa projektin lähdekoodeille, eikä pitänyt nimestä Freax,
  joten hän laittoi Linusilta kysymättä hakemiston nimeksi Linux.

> "I am egoistic bastard, first I named Linux after myself and then Git"
>
> – Linus Torvalds


Mikä on käyttöjärjestelmä?
==========================
Käyttöjärjestelmä on tietokoneohjelma tai kokonaisuus, joka käynnistyy ensimmäisenä ja käynnistää ja palvelee muita ohjelmia.

- Se tarjoaa muiden ohjelmien käyttöön levyt, tiedostojärjestelmät, verkon, yms. laitteet.
- Ohjelmat eivät itse pääse käsiksi laitteisiin vaan pyytävät kaiken käyttöjärjestelmältä.

Onko Linux käyttöjärjestelmä?
=============================

- Toisten mielestä: Kyllä, se täyttää käyttöjärjestelmän tehtävät yksinään.
- Toisten mielestä: Ei, se on vain käyttöjärjestelmän ydin. Käyttöjärjestelmä on Linux + muutamia muita ohjelmia yhdessä.

Käytännössä pelkällä Linux-ytimellä ei kuitenkaan tee mitään vaan sen lisäksi tarvitaan muukin kokonaisuus.


Linux-jakelut
=============
Linux-toimitetaan yleensä jakelupaketteina, eli distribuutioina.

- Debian
- Slackware
- Red Hat
- Ubuntu, openSUSE, Fedora, Mint, Arch, Mageia, CentOS,...

Jakelupaketissa on koottu yhdeksi paketiksi asennettavaksi kokonaisuus: Linux-ydin, paketinhallinta, asetukset, graafiset käyttöliittymät ja läjäpäin ohjelmia.
Osa jakelupaketeista on aloittanut ohjelmistojen kasaamisen alusta, suurin osa pohjautuu johonkin aiempaan.

[Sukupuu](/images/gldt1210.svg)



Kaupalliset jakelut vs. yhteisölliset jakelut
==============================================
Jakelupaketteja kootaan kaupallisesti palkatulla väellä tai yhteisöllisesti vapaaehtoisvoimin. Toisinaan yritysten ja yhteisöjen välillä on rinnakkaista yhteistyötä. Esimerkiksi:

- **Fedora**: Yhteisön voimin rakennettu jakelu.
- **Red Hat Enterprise Linux**: Fedoraan pohjautuva Red Hat -yhtiön kaupallisesti tuettu versio.
- **CentOS**: RHEL:in kanssa yhteensopiva yrityskäyttöön suunnattu yhteisön kasaama jakelu ilman Red Hatin brändäystä ja tukea.
- **Debian**: Täysin yhteisöllisesti toimiva projekti ja jakelu.
- **Ubuntu**: Canonical-yhtiön ja Ubuntu-yhteisön yhdessä Debianin pohjalta kehittämä jakelu.
- **Linux Mint**: Yhteisövetoinen jakelu, joka pohjautuu Ubuntuun.



Linuxin levinneisyys
====================
Linuxin työpöytävalloitusta odoteltaessa se on valloittanut:

- palvelimet,
- supertietokoneet,
- digiboxit ja -telkkarit,
- puhelimet,
   - Googlen ja kumppaneidensa Android,
   - Nokian Maemo ja MeeGo,
   - Jollan SailfishOS
   - Intel ja Samsung: Tizen
   - Samsungin Bada,
   - Canonicalin Ubuntu Phone,
   - Mozillan Firefox OS
- tabletit (Android, WebOS),
- reitittimet,
- gps-navigaattorit,
- lypsykoneet

{{< youtube xPbAXKMCDkY >}}




Linux muutakin kuin komentorivi
===============================

On yleinen harhaluulo, että Linux olisi yhtä kuin musta ruutu, vaaleaa tekstiä ja vaikeasti muistettavia komentoja.

- X window system antaa graafisen tilan
- X:n päällä useita vaihtoehtoisia käyttöliittymiä
   - KDE-työpöytä
   - Gnome-työpöytä
   - Unity-työpöytä
   - XFCE-työpöytä
   - LXDE-työpöytä
   - Cinnamon-työpöytä (Linux Mint)
   - MATE-työpöytä
   - Pantheon-työpöytä
   - Useita ikkunanhallintaohjelmia (Enlightenment, Blackbox, ...)
- Useita rinnakkaisia virtuaalityöpöytiä
- Yksittäisiä ohjelmia tai koko työpöytää voi ajaa etänä verkon yli.


{{< figure src="/images/320px-Gnome_3.2_shell.png" attr="CC-BY, The Gnome Project" attrlink="http://en.wikipedia.org/wiki/File:Gnome_3.2_shell.png" title="Gnome" >}}
{{< figure src="/images/320px-KDE_4.png" attr="GNU GPL, KDE" attrlink="http://en.wikipedia.org/wiki/File:KDE_4.png" title="KDE" >}}
{{< figure src="/images/320px-Unity_5.12_on_Ubuntu_12.04.png" attr="CC-BY-SA, Rprpr" attrlink="http://en.wikipedia.org/wiki/File:Unity_5.12_on_Ubuntu_12.04.png" title="Unity" >}}
{{< figure src="/images/320px-XFCE-4.10-Desktop.png" attr="CC-BY-SA, Xfce Development Team" attrlink="http://en.wikipedia.org/wiki/File:XFCE-4.10-Desktop.png" title="XFCE" >}}
{{< figure src="/images/320px-LXDE_desktop_full.png" attr="GNU GPL, Hidro" attrlink="http://en.wikipedia.org/wiki/File:LXDE_desktop_full.png" title="LXDE" >}}


{{< youtube WVTWCPoUt8w >}}


Tehtäviä
========

Kuvakaappauksen voi ottaa PrintScreen-näppäimellä.

- Käynnistä DVD:ltä tai usb-tikulta jokin seuraavista: Ubuntu, Kubuntu, Lubuntu, Linux Mint, ElementaryOS tai Fedora.
- Tutki, minkä niminen tekstinkäsittelyohjelma löytyy.
- Entä mikä on nimeltään oletuksena tarjolla oleva www-selain?




[Linus Torvalds]: https://fi.wikipedia.org/wiki/Linus_Torvalds "Linus Torvalds"
[comp.os.minix]: https://groups.google.com/forum/#!msg/comp.os.minix/dlNtH7RRrGA/SwRavCzVE7gJ "Hello everybody outh there using minix -"
[vastaanotto]: https://groups.google.com/d/msg/comp.os.minix/dlNtH7RRrGA/SwRavCzVE7gJ "comp.os.minix"
[AST-vastaus]: https://groups.google.com/d/msg/comp.os.minix/wlhw16QWltI/XdksCA1TR_QJ "Andrew S. Tanenbaum"
[mikrokerneli]: http://en.wikipedia.org/wiki/Microkernel "Mikrokerneli"
[monoliittinen]: http://en.wikipedia.org/wiki/Monolithic_kernel "Monoliittinen kerneli"
[RMS]: http://fi.wikipedia.org/wiki/Richard_Stallman "Richard M. Stallman"
[GNU]: http://en.wikipedia.org/wiki/GNU_project "GNU-projekti"
[FSF]: http://www.fsf.org/ "Free Software Foundation"
[GNU GPL]: https://www.gnu.org/licenses/gpl.html "GNU GPL"
[OSI]: https://opensource.org/ "Open Source Initiative"
