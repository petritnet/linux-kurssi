---
date: "2016-09-06T22:06:10+03:00"
title: "Tiedosto-oikeudet"
sectiontitle: "Järjestelmä"
weight: 120
---

Tiedostojen oikeudet
==================

Unixeissa tiedostojärjestelmän kaikille hakemistoille ja tiedostoille on
määritelty niiden käyttöoikeudet tiedoston omistajuuden ja ryhmän perusteella.

Jokaiselle tiedostolla ja hakemistolla on yksi *omistaja* (käyttäjätunnus, `uid`) ja yksi
*omistajaryhmä* (ryhmä, `gid`). Jokaiselle tiedostolle on määrätty kolmenlaisia käyttöoikeuksia
kolmelle joukolle käyttäjiä.

Käyttöoikeuksia ovat:

|Lyhenne| Oikeus                          | Huom       |
|-------|---------------------------------|------------|
| *r*   | Lukuoikeus (**r**ead)           | Saa lukea tiedoston tai hakemiston sisällön. |
| *w*   | Kirjoitusoikeus (**w**rite)     | Saa kirjoittaa tiedostoon tai luoda hakemIstoon uusia tiedostoja.|
| *x*   | Suoritusoikeus (e**x**ecute)    | Saa suorittaa tiedoston tai viitata hakemiston sisältöön. |

Käyttäjäjoukkoja, joille näitä oikeuksia voidaan antaa, ovat:

|Lyhenne| Käyttäjäjoukko                  |
|-------|---------------------------------|
| *u*   | Käyttäjä (**u**ser)             |
| *g*   | Ryhmä (**g**roup)               |
| *o*   | Muut (**o**thers)               |

Kullekin kolmelle käyttäjäjoukolle ovat annettavissa kaikki kolme käyttöoikeutta.



Tiedostojen oikeudet tiedostonhallinnalla
=========================================

{{< figure src="/images/ubuntu-accessrights.png" link="/images/ubuntu-accessrights.png" class="floatright floatimage" title="Tiedostojen oikeudet" caption="Ubuntun tiedostonhallinnalla voi muokata tiedoston oikeuksia." >}}

{{< figure src="/images/ubuntu-listcolumns.png" link="/images/ubuntu-listcolumns.png" class="floatright floatimage" title="Oikeudet näkyviin" >}}

{{< figure src="/images/ubuntu-listcolumns-quick.png" link="/images/ubuntu-listcolumns-quick.png" class="floatright floatimage" title="Oikeudet näkyviin" >}}

Graafisella tiedostonhallintaohjelmalla voi Ubuntussa muokata tiedostojen oikeuksia seuraavasti:

1. Otetaan tiedostonhallinta esiin.
2. Klikataan valittua tiedostoa hiiren oikealla napilalla.
3. Valitaan "Properties" tai "Ominaisuudet", riippuen käytetystä kielestä.
4. Välilehdeltä "Permissions" / "Oikeudet" ovat valittavissa seuraavat asetukset:
    - Omistaja voi vaihtaa tiedoston ryhmän johonkin omista ryhmistään.
    - Omistajan oikeuksille vaihtoehdot: "Read-only" ja "Read and write"
    - Ryhmän oikeuksille vaihtoehdot: "None", "Read-only" ja "Read and write"
    - Muiden oikeuksille vaihtoehdot: "None", "Read-only" ja "Read and write"
    - Lisäksi on rastiruutu suoritusoikeuksille. (Laittaa suoritusoikeuden kaikille kolmelle.)

Tällä graafisella työkalulla ei ole mahdollista saada aikaan kaikkia mahdollisia oikeuksien yhdistelmiä
vaan vain tyypillisimmin tarvitut yhdistelmät. Erikoisemmat oikeuksien yhdistelmät pitää asettaa
joko jollain muulla työkalulla tai komentoriviä käyttäen.




Oikeudet näkyviin tiedostonhallinnalla
=========================================

Tiedostojen oikeudet on mahdollista saada näkyviin myös suoraan tiedostonhallintaikkunan
listamuotoisessa näkymässä. Listanäkymän saa käyttöön ikkunan oikean yläreunan listakuvakkeella.

Listänäkymässä näkyviä sarakkeita voi muokata valitsemalla työpöydän yläreunan valikosta
*"Files"* -> *"Preferences"* ja sieltä *"List Columns"*-välilehdeltä rastiruuduilla halutut
sarakkeet, kuten **"Group"**, **"Owner"** ja **"Permissions"**.

Tämä valinta muuttaa listanäkymässä oletuksena näytettäviä sarakkeita. Jos sarakkeet halutaan
näkyviin vain yksittäisessä hakemistossa tai väliaikaisesti, ne voi valita myös klikkaamalla
sarakkeiden otsikkoriviä hiiren oikealla napilla.





Tiedostojen oikeudet komentorivillä
=========================================

Tiedostojen oikeuksia voi komentorivillä tarkastella komennolla `ls`.

1. Käynnistetään terminaali (Launcher: "terminal")
2. Siirrytään hakemistoon (kansio), jossa tutkittava tiedosto: `cd Pictures`
   (tai `cd Kuvat`)
3. Luetellaan tiedostot tietoineen: `ls -la`
    - `ls`: luetellaan hakemistossa olevat tiedostot ("list")
    - `-la`: tarkennetaan ohjelman toimintaa <br>
        *`l`*: pitkä muoto, enemmän tietoa tiedostoista <br>
        *`a`*: kaikki tiedostot, myös pisteellä alkavat

```bash
pesasa@kurssibuntu:~$ cd Pictures/
pesasa@kurssibuntu:~/Pictures$ ls -la
total 440
drwxr-xr-x  2 pesasa pesasa   4096 Sep  5 22:44 .
drwxr-xr-x 36 pesasa pesasa   4096 Sep 12 21:45 ..
-rwxrwxr-x  1 pesasa pesasa 410662 Sep  5 22:28 Screenshot-01.png
-rw-rw-r--  1 pesasa pesasa  27645 Sep  5 22:44 Screenshot-02.png
pesasa@kurssibuntu:~/Pictures$
```

Komennon tulostuksessa kullakin rivillä näytetään yhden tiedoston tiedot.
Rivin ensimmäisenä merkkinä on `d`, jos kyseessä on hakemisto, muutoin rivi alkaa
viivalla. Seuraavat yhdeksän merkkiä ovat käyttäjän, ryhmän ja muiden oikeudet
kukin kolmella merkillä järjestyksessä `rwx`. Jos joltain käyttäjäjoukoista puuttuu
jokin oikeus, on sen kohdalla viiva `-`.

Muita riviltä luettavia tietoja ovat tiedoston omistajan käyttäjätunnus, tiedoston
omistava ryhmä, tiedoston koko tavuina, tiedoston muokkausaika sekä tiedoston nimi.



Omistajan ja ryhmän muuttaminen komentorivillä
=========================================

Tiedoston omistajan ja ryhmän voi vaihtaa komennolla `chown`.

Tiedoston omistajan voi vaihtaa vain ylläpito-oikeuksilla, eli esimerkiksi
komennolla:

```no-highlight
sudo chown petri Screenshot-01.png
```

Tiedoston ryhmän voi vaihtaa vain sellaiseksi ryhmäksi, johon käyttäjä itse kuuluu.
Ylläpito-oikeuksilla voi kuitenkin ryhmäksi vaihtaa minkä tahansa ryhmän.

Komennossa omistaja ja ryhmä annetaan kaksoispisteellä (`:`) tai pisteellä (`.`)
eroteltuina. Pelkkä ryhmä vaihdetaan jättämällä käyttäjätunnuksen paikka tyhjäksi
ja antamalla vain ryhmä kaksoispisteen jälkeen. Esimerkiksi:

```no-highlight
chown :sudo Screenshot-01.png
```

Tiedoston omistaja ja ryhmä voidaan vaihtaa samalla kertaa komennolla:

```no-highlight
sudo chown petri:audio Screenshot-01.png
```

Tähän tarvitaan kuitenkin ylläpito-oikeuksia.

Muutosten jälkeen tiedostojen omistajuudet näyttävät tältä:

```bash
pesasa@kurssibuntu:~/Pictures$ ls -la
total 440
drwxr-xr-x  2 pesasa pesasa   4096 Sep 12 23:15 .
drwxr-xr-x 36 pesasa pesasa   4096 Sep 12 21:45 ..
-rwxrwxr-x  1 petri  audio  410662 Sep  5 22:28 Screenshot-01.png
-rw-rw-r--  1 pesasa pesasa  27645 Sep  5 22:44 Screenshot-02.png
pesasa@kurssibuntu:~/Pictures$
```




Oikeuksien muuttaminen komentorivillä
=========================================

Komentoriviltä käsin tiedostojen oikeuksia voi muokata graafista työkalua vapaammin
komennolla `chmod`.

Esimerkiksi myös omistajalta voi ottaa lukuoikeuden pois ja suoritusoikeuden voi
laittaa erkseen omistajalle, ryhmälle tai muille.

* Oikeuksia voi lisätä (**+**), poistaa (**-**) ja asettaa (**=**)
* omistajalle (**u**), ryhmälle (**g**), muille (**o**) tai kaikille (**a**)

Asettamisessa kyseiselle käyttäjäjoukolle tulevat oikeuksiksi täsmälleen ne oikeudet,
jotka komennossa sanotaan, ei muita.

"Kaikki"-joukko on lyhennys, joka tarkoittaa sekä omistajaa, ryhmää että muita.

Esimerkiksi:

```no-highlight
chmod u=rwx Screenshot-02.png
chmod g+x Screenshot-02.png
chmod o-r Screenshot-02.png
chmod a+r Screenshot-02.png
chmod u=rx,g-x,o=r Screenshot-02.png
```

Näissä esimerkeissä:

- Asetetaan omistajalle (`u`) kaikki oikeudet (`rwx`).
- Lisätään ryhmälle (`g`) suoritusoikeus (`x`).
- Poistetaan muilta (`o`) lukuoikeus (`r`)
- Lisätään kaikille (`a`) lukuoikeus (`r`)
- Asetetaan käyttäjälle oikeudet `rx`, poistetaan ryhmältä oikeus `x` ja asetetaan muille oikeus `r`.



Tehtäviä
=========================================

{{% wrapper class="exercises" %}}
Tehtävät 4
===========


Käynnistä jokin live-levyn työpöytä-Linux ja tee tehtävät siinä.
Kirjoita vastaukset LibreOfficen Writer-ohjelmalla tiedostoon `tehtava-4.odt`.

1. Selvitä tiedostosta `/proc/cpuinfo` käyttämäsi koneen prosessorin merkki/malli.
2. Mikä on käyttäjätunnuksesi uid?
2. Mitkä omistaja ja ryhmä ovat tiedostoilla `/etc/passwd` ja `/etc/shadow`?
3. Mitkä ovat näiden tiedostojen oikeudet omistajalle, ryhmälle ja muille?
4. Kopioi terminaalissa annetun komennon `ls -l /etc/passwd /etc/shadow` tulostus vastaustiedostoosi.
5. Tiedostossa `/etc/passwd` luetellaan järjestelmässä olevat käyttäjätunnukset.
   Etsi rivi, jolla on tunnus nimeltä `nobody`.
   Mikä on nobodyn käyttäjänumero? (Rivin ensimmäinen numero kahden `:`-merkin välissä.)
6. Tallenna vastaustiedostosi ja aseta sen oikeudet niin, että käyttäjällä ovat luku- ja kirjoitusoikeudet,
   ryhmällä lukuoikeus ja muilla ei mitään. Miten teit tämän?
7. Ota tiedostohallintaan näkyviin tiedostojen oikeudet niin, että vastaustiedoston tiedot näkyvät,
   ja ota ikkunasta kuvakaappaus. Liitä kuvakaappaus vastaustiedostoosi.
{{% /wrapper %}}
