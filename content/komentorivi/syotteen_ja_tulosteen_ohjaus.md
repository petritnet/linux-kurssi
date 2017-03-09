+++
date = "2016-09-08T22:23:11+03:00"
title = "Syötteen ja tulosteen ohjaus"
weight = 420
+++

Komentoriviohjelmat saavat tyypillisesti syötteensä käyttäjältä näppäimistön kautta
ja ne tulostavat tuottamansa tekstin näytölle, terminaaliin, jossa ohjelma on käynnissä.
Näin ei kuitenkaan välttämättä tarvitse olla, sillä ojelma voidaan laittaa ottamaan syötteensä,
eli sille syötteenä annettavan tekstin, esimerkiksi tiedostosta tai joltain toiselta ohjelmalta.
Samoin ohjelman tulostama teksti voidaan näytön sijasta ohjata joko tiedostoon tai jollekin
toiselle ohjelmalle.

Tekstin lukeminen tiedostosta tai sen tulostaminen tiedostoon lisää mahdollisuutta
automaatioon, sillä se vähentää ihmisen tarvetta syöttää tietoa interaktiivisesti
näppäimistöltä.

Ohjelman tulosteen ohjaaminen toisen ohjelman syötteeksi puolestaan mahdollistaa
tekstille erilaisia operaatiota tekevien ohjelmien linkittämisen. Näin yksinkertaiset
ohjelmat saadaan tekemään yhdessä monimutkaisempia kokonaisuuksia.


{{% wrapper class="exercises" %}}
Ohjelmien yhdisteleminen (kokeile)
--------------------------

Kirjoita terminaaliin seuraava komentorivi:

```
seq 39 | sort -R | head -n 7 | sort -n
```

Pohdi:

1. Mistä yksittäisistä komennoista se koostuu ja mitä komennot tekevät?
2. Miten komennon tulosteen ohjaaminen toiselle komennolle merkitään?
3. Mitä käyttöä lopputuloksella voisi olla?


{{% /wrapper %}}








Stdin, stdout, stderr
=========================

Komentoriviohjelmilla on kolme niin kutsuttua standardivirtaa:

| Virta | Numero | Merkitys                                                                                                                                |
|-------|--------|-----------------------------------------------------------------------------------------------------------------------------------------|
|stdin  | 0      | "standardi **syötevirta**", "standard input", eli reitti, jota ohjelmalle menee tekstimuotoista syötettä, *normaalisti näppäimistöltä*. |
|stdout | 1      | "standardi **tulostevirta**", "standard output", eli reitti, jota ohjelman tuloste tulee, *yleensä näytölle*.                           |
|stderr | 2      | "standardi **virhevirta**", "standard error", eli reitti, jota ohjelman virheilmoitustulosteet tulevat, *yleensä myös näytölle*.        |


Näitä voi ohjailla uudelleen tulemaan jostain muualta, kun näppäimistöltä ja jonnekin muualle kuin näytölle.
Esimerkiksi tiedostosta tai tiedostoon taikka toiselta ohjelmalta tai toiselle ohjelmalle.





{{% wrapper class="exercises" %}}
Standardi input (kokeile)
-----------------------------

`cat`-ohjelma tulostaa normaalisti pyydetyn tiedoston sisällön näytölle:

```
 cat Documents/nano-harjoitus.txt
```

Jos `cat`-ohjelmalle ei anneta tulostettavaa tiedostoa, se ottaa syötteen vastaan näppäimistöltä (stdin)
ja tulostaa takaisin näytölle (stdout), kunnes käyttäjä antaa **ctrl-d**-näppäilyn. Kokeile!

```
 cat
```

{{% /wrapper %}}



Tulostus tiedostoon
=========================

Ohjelman tulostuksen voi ohjata haluamaansa tiedostoon lisäämällä komennon perään: `> tiedostonnimi`.

```
 ls -l > listaus.txt
```

```
 echo "Petri" > nimi.txt
```

Tällöin tulostus ei näy näytöllä lainkaan vaan menee sen sijaan suoraan käskettyyn tiedostoon.
Jos tiedostoa ei ole ennestään, se luodaan. Jos tiedosto on jo olemassa, se ylikirjoitetaan!






{{% wrapper class="exercises" %}}
Tulostus tiedostoon (kokeile)
--------------------------

`cat`-ohjelman tulosteen voi ohjata myös tiedostoon. Kokeile kirjoittaa seuraava:

```
 cat > nimi.sh
 #!/bin/bash
 echo "Anna nimesi: "
 read nimi
 echo "Heippa, $nimi!"
```

Lopuksi lopeta painamalla **ctrl-d**.

Jatkoa varten anna luodulle tiedostolle suoritusoikeudet:

```
 chmod a+x nimi.sh
```


{{% /wrapper %}}



Tulostus tiedoston loppuun
=========================

Tulosteen voi ohjata myös tiedoston loppuun ylikirjoittamatta aiempaa sisältöä käyttämällä
merkin `>` sijasta kahta merkkiä: `>>`

```
 echo 'echo "Loppu"' >> nimi.sh
```

Tarkista tiedoston sisältö komennolla:

```
 cat nimi.sh
```

Kokeile ajaa tämä ohjelma komentamalla:
```
 ./nimi.sh
```





Syöte tiedostosta
=========================

Monet ohjelmat, kuten `less`, `wc` ja `sort`, osaavat lukea syötteen suoraan tiedostosta.
Ohjelmille, jotka eivät osaa suoraan lukea tiedostosta, vaan lukevat näppäimistöä,
voidaan tiedoston sisältö antaa syötteenä lisäämällä komennon perään: `< tiedosto`.
Tämä tarkoittaa, että tiedoston sisältö ohjataan ohjelmalle sisään menevään standardiin syötevirtaan (stdin)
korvaamaan normaalisti käytettävä näppäimistösyöte.



{{% wrapper class="exercises" %}}
Syöte tiedostosta (kokeile)
-----------------------------

Suoritetaan ohjelma näin:

```
 ./nimi.sh < nimi.txt
```

Ohjelma saa syötteen näppäimistön sijasta tiedostosta `nimi.txt`.

{{% /wrapper %}}






Virheiden tulostus tiedostoon
=========================

Jotkut ohjelmat tulostavat virheilmoitukset erilliseen virhetulostusten virtaan, "stderr",
joka normaalisti tulostuu näytölle, kuten standardi tulostevirtakin.
Virhetulosteet voidaan kuitenkin ohjata erikseen eri tiedostoon kuin tavallinen tulostus,
lisäämällä komennon perään: `2> tiedosto`. Tämä tarkoittaa "ohjaa virran 2 teksti tiedostoon".

Kokeile komentoa:

```
 grep -r local /etc/cups
```

Komento etsii rekursiivisesti merkkijonoa "local" tiedostoista hakemiston `/etc/cups` alla.
Hakutulosten lisäksi tulostuu virheilmoituksia tiedostoista, joihin ei käyttäjällä ole lukuoikeuksia.

Kokeile seuraavaksi komentoa:
```
 grep -r local /etc/cups 2> /dev/null
```

Nyt virheilmoitukset ohjattiin tiedostoon `/dev/null`, joka on Unix-järjestelmissä oleva erikoistiedosto,
"musta-aukko", johon lähetetyt tekstit katoavat jälkiä jättämättä. Näytölle tulostuvat vain standardin
tulostusvirran tekstit, ei virheilmoituksia.





Tulosteen putkitus toiselle ohjelmalle
=========================

Toisinaan ohjelman tuloste halutaan ohjata tiedoston sijaan toiselle ohjelmalle.
Tämä tapahtuu *putkittamalla* tuloste `|`-merkillä. Ensimmäisen ohjelman tuloste menee putken toisesta
päästä sisään ja toisesta päästä suoraan toiselle ohjelmalle syötteeksi.

```
 history | less
```

`history`-komennon tuloste voi olla melko pitkä, mutta kun se putkitetaan `less`-ohjelmalle, sitä on mahdollista selata.

Putkittamalla voi ketjuttaa useampiakin ohjelmia peräkkäin.

```
 history | grep  ls | less
```

Poimitaan `history`:n tulosteesta vain kaikki rivit, joilla esiintyy merkkijono `ls` ja ohjataan ne `less`-ohjelmalle.
Huomaa, että viimeisellä rivillä on myös tämä komento itse.

```
 history | grep ls | wc -l
```

Lasketaan `ls`-merkkijonon sisältävien historiarivien määrä.

`cut`-ohjelmalla voi tekstitulosteesta leikata halutut sarakkeet.
Leikattavat sarakkeet voi kertoa valitsimella `-f` ja sarakkeiden erotinmerkin valitsimella `-d`.
Esimerkiksi:

```
 history | cut -d' ' -f 4-
```

Erotinmerkkinä toimii välilyönti ja tulosteesta leikataan mukaan kaikki sarakkeet sarakkeesta 4 alkaen.

```
 history | cut -d' ' -f 4- | sort | uniq | wc -l
```

Leikataan `history`:n tulosteesta pois rivinumerot ja jätetään vain komennot,
järjestetään ne aakkosjärjestykseen `sort`-ohjelmalla ja poistetaan useammankertaiset
samanlaiset rivit `uniq`-ohjelmalla. Lopuksi lasketaan jäljelle jääneiden rivien määrä.

Monissa komentoriviohjelmissa standardia tulostevirtaa tai syötevirtaa merkitään
merkillä `-`. Esimerkiksi `wget`-ohjelmassa voidaan tulostus ohjata syötevirtaan antamalla
tallennustiedoston nimen paikalla merkki `-`. Oletuksena tuloste menee siis näytölle, mutta
halutessaan sen voi ohjata toiselle ohjelmalle tai tiedostoon.


```
 wget -O - http://petrit.net/Linux-kurssi/files/pg32536.txt | head -n 20
```

Ladataan verkosta *Baskervillen koira* -romaani tekstitiedostona, tulostetaan se standardi tulostevirtaan
ja näytetään siitä ruudulla vain 20 ensimmäistä riviä.

Mutta... Huomaamme, että tulostuksessa näkyy välissä `wget`-ohjelman muita tulostuksia.
Nämä tulosteet tulevat virhetulostevirrasta ja niistä pääsee eroon mm. ohjaamalla virhetulosteet `/dev/null`:iin.

```
 wget -O - http://petrit.net/Linux-kurssi/files/pg32536.txt 2> /dev/null | head -n 20
```

Pohdintaa
=========

Pohdi, mitä eroa on tulosteen ohjaamisessa tiedostoon tai toiselle ohjelmalle. Mikä ero on niihin
käytetyssä merkinnässä?

**Vastaus:** Tiedostoon (tai tiedostosta) ohjaamiseen käytetään `>`-merkkiä (ja `<`-merkkiä), kun taas
ohjelmien väliseen ohjaamiseen, putkittamiseen, käytetään merkkiä `|`.


Tehtäviä
=========================

{{% wrapper class="exercises" %}}
Tehtävät 10
=========================

Suorita tehtävät komentorivillä ja kirjoita vastaukset tiedostoon `tehtava-10.txt`. Kerro jokaisessa kohdassa vastauksen lisäksi,
millä komennolla tai komennoilla suoritit tehtävän. (Kopioi komennot ja tulosteet terminaali-ikkunasta tekstitiedostoon.)
Palauta vastauksenasi tiedosto `tehtava-10.zip`, johon on paketoitu molemmat luomasi tekstitiedostot.

1. Kuinka monta __erilaista__ riviä on komentohistoriassasi?
2. Millä rivillä tiedostossa `http://petrit.net/Linux-kurssi/files/pg32536.txt` alkaa kuudes luku?
   * Vihje 1: `wget`, `grep`
   * Vihje 2: Kyseisellä rivillä lukee teksti *KUUDES LUKU*
   * Vihje 3: `grep` näyttää rivinumerot valitsimella `-n`
3. Monellako rivillä nimi *Holmes* esiintyy edellisessä tiedostossa?
   * Vihje: `wget`, `wc`, `grep`
4. Tutki hakemiston `/etc` sisältöä (ei sen alihakemistojen sisältöä).
   Monenko tiedoston tai hakemiston päiväys on vuodelta 2011?
   * Vihje: `ls`, `grep`
5. Käytössäsi on tiedosto `http://petrit.net/Linux-kurssi/files/pg32536.txt` sekä ohjelmat
  `wget`, `cat`, `head` ja `tail`. Näitä käyttäen tee tiedosto `kooste.txt`, joka on seuraavanlainen:
   * Tiedosto alkaa annetun tiedoston riveillä 9-13.
   * Näiden jälkeen tiedostossa on rivi, jolla on kolme pistettä (...).
   * Tämän jälkeen tiedostossa on vielä annetun tiedoston neljä viimeistä riviä.

{{% /wrapper %}}