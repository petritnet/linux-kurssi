---
date: "2017-02-25T18:30:04+03:00"
title: "X-ikkunointi"
sectiontitle: "Graafinen käyttöliittymä"
weight: 210
---


Unixeissa ja Linuxissa on perinteisesti käytetty ikkunointiin järjestelmää
nimeltä [X Window System], eli X11 tai
lyhyesti vain X.

Nykyisin Linuxissa on X:n toteutuksena [X.org], jonka edeltäjä oli
nimeltään XFree86. Nykyinen X.org syntyi, kun suuri osa XFree86:n
kehittäjistä jatkoi erimielisyyksien takia kehitystä uudella nimellä.

{{% wrapper class="theorybox" %}}
Asiakas–palvelin
====================
X toteuttaa ikkunoinnin **asiakas–palvelin** -periaatteella, mikä tarkoittaa sitä, että:

* käytettävä ohjelma on asiakas, joka pyytää palveluja. ("Piirrä ruudulle ikkuna, jossa...",
  "Ota vastaan näppäimen painallukset sekä hiiren liikkeet ja kerro ne minulle")
* X on palvelin, joka toteuttaa asiakkaan pyynnöt.
* X on välikerros, joka toimii käyttäjän ja ohjelmien välillä näyttämällä tulosteen (output) näytöllä
  ja välittämällä syötteen (input) syöttölaitteilta (näppäimistö, hiiri, piirtopöytä, jne.).
  {{% /wrapper %}}


Eräs X:n ominaisuus on ollut **verkkoläpinäkyvyys**, eli asiakas ja palvelin voivat
olla eri koneilla. Tämä on mahdollistanut graafiset terminaalit, joissa on paikallisesti
vain X-serveri hoitamassa näyttöä sekä syöttölaitteita ja joilla käytettävät ohjelmat
ovat käynnissä etäpalvelimella. Monet ovat kuitenkin oikeutetusti sitä mieltä,
että ohjelmat ovat nykyään jo käyttöliittymältään ja teemoitukseltaan sen verran
raskaita, että verkon yli tapahtuvaan käyttöön on usein tehokkaampaa käyttää
jotain muuta etäkäyttöön soveltuvaa järjestelmää, kuten **VNC**:tä.

X yksinään ei näytä oikein miltään, sillä se on vain palvelija, joka hoitaa ruudulle piirtämisen ja
syötteiden vastaanoton sekä välittämisen.




X-ikkunointi: kokeillaan
==============================

{{< figure src="/images/xorg.jpg" link="/images/xorg.jpg" class="floatright floatimage" title="X.org" caption="'Tyhjä' X.org ja siihen käynnistetty xterm." >}}

Havainnollistuksen vuoksi käynnistetään X mahdollisimman minimaalisena.
Seuraavat ohjeet vaativat, että järjestelmässä on asennettuna `xterm`-ohjelma.
Live-Ubuntuun sen voi asentaa lisäämällä käyttöön "universe"-pakettilähde ja
asentamalla paketti `xterm`.

Käynnistetään X minimaalisimmillaan seuraavasti:

1. Linuxin tekstitilaan, eli virtuaaliterminaaliin, painamalla `ctrl-alt-f2`.
    * (Virtuaaliterminaaleja yleensä 6 kpl. f1-f6)
2. Kirjaudutaan sisään käyttäjätunnuksella ja salasanalla. (Live-Ubuntussa `ubuntu` ja tyhjä)
3. Käynnistetään uusi X komennolla: `xinit -- :1 vt2`
    * Jo käynnissä oleva X on numero 0. (`:0`)
    * `vt2` tarkoittaa virtuaaliterminaalia numero 2 (sama, johon siirryttiin näppäimellä `ctrl-alt-f2`)
4. Käynnistyy X ilman taustakuvaa, ikkunoidenhallintaa tai mitään muuta "koristeita".
   Vain *xterm*-pääteikkuna ja rastimainen hiiren kursori.

{{< figure src="/images/xeyes.jpg" link="/images/xeyes.jpg" class="floatright floatimage" title="xeyes ja xlogo" caption="Terminaalista käynnistetyt xeyes ja xlogo." >}}

X-istuntoon voi käynnistää ohjelmia käynnistämällä ne *xterm*-pääteikkunasta käsin. Niiden siirtely ja
koon muokkaaminen ei kuitenkaan onnistu tässä tilassa, sillä X yksinään ei sisällä mitään käyttöliittymää
tällaiseen ikkunoiden hallintaan.

Kokeillaan komentoja:

```
xeyes -geometry 500x300+500+200 &
```

ja

```
xlogo -geometry 100x100+80020 &
```

Näille ohjelmille on komentorivillä suoraan kerrottu niiden koko ja sijainti näytöllä. Komennon lopussa
oleva `&`-merkki laittaa ohjelman suorituksen taustalle. Tämä tarkoittaa sitä, että komentorivi ei jää
odottamaan ohjelman suorituksen loppumista vaan on heti valmiina ottamaan vastaan seuraavan käskyn.
Voit kokeilla, mitä tapahtuu, jos käynnistät ohjelman ilman `&`-merkkiä. Edustalla olevan ohjelman saa lopetettua
näppäinyhdistelmällä `ctrl-c`.

Aiempi X, jossa on normaali työpöytä, on saatavilla esiin näppäilemällä `ctrl-alt-f1` ja
"uusi X" näppäilemällä uudelleen `ctrl-alt-f2`.

X-istunto päättyy, kun siihen ensimmäisenä ohjelmana käynnistynyt xterm suljetaan. Tämä tapahtuu
kirjoittamalla *xterm*-ikkunaan `exit`.



[X Window System]:https://en.wikipedia.org/wiki/X_Window_System (X Window System)
[X.org]: https://www.x.org/wiki/ (X.org)
