+++
date = "2016-09-06T22:06:10+03:00"
title = "Tiedosto-oikeudet"
weight = 7
+++

Tiedostojen oikeudet
==================

* Jokaisella tiedostolla (ja hakemistolla) omistaja ja ryhmä
* Jokaisella tiedostolla kolmen tyypin oikeuksia kolmelle joukolle käyttäjiä
* luku (**r**ead), kirjoitus (**w**rite), suoritus (e**x**ecute)
* omistaja (**u**ser), ryhmä (**g**roup), muut (**o**thers)
* hakemistoilla suoritusoikeuden sijasta viittausoikeus




Tiedostojen oikeudet tiedostonhallinnalla
=========================================

1. Tiedostonhallinta esiin
2. Valittu tiedosto hiiren oikealla nappulalla
3. "Properties" / "Ominaisuudet"
4. "Permissions" / "Oikeudet"
    - Omistaja voi vaihtaa tiedoston ryhmän johonkin ryhmistään.
    - Omistajan oikeuksille vaihtoehdot: "Read-only" ja "Read and write"
    - Ryhmän oikeuksille vaihtoehdot: "None", "Read-only" ja "Read and write"
    - Muiden oikeuksille vaihtoehdot: "None", "Read-only" ja "Read and write"
    - Lisäksi rastiruutu suoritusoikeuksille. (Laittaa suoritusoikeuden kaikille kolmelle.)




Oikeudet näkyviin tiedostonhallinnalla
=========================================

* Tiedostonhallinta "lista"-näkymään (Ikkunan yläreunan kuvakkeesta)
* Valitaan näytettävät sarakkeet (Valikosta: "Files" -> "Preferences" -> "List Columns"-välilehti)
* Rastit kohtiin "Group", "Owner", "Permissions"





Tiedostojen oikeudet komentorivillä
=========================================

1. Käynnistetään terminaali (Launcher: "terminal")
2. Siirrytään hakemistoon (kansio), jossa tutkittava tiedosto: `cd Pictures`
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




Omistajan ja ryhmän muuttaminen komentorivillä
=========================================

* Komennolla `chown`
* Omistajan vaihto: `sudo chown petri Screenshot-01.png`<br>
    (Vain ylläpito-oikeuksilla voi vaihtaa omistajaa.)
* Ryhmän vaihto: `chown :sudo Screenshot-01.png`<br>
    (Käyttäjä voi vaihtaa ryhmän vain sellaiseen, johon itse kuuluu.)
* Omistajan ja ryhmän vaihto samalla kertaa: `sudo chown petri:audio Screenshot-01.png`<br>
    (Ylläpitäjä voi vaihtaa omistajan ja ryhmän miksi haluaa.)

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

* Monipuolisemmat asetukset kuin graafisella työkalulla
    * Esimerkiksi myös omistajalta voi ottaa lukuoikeuden pois ja suoritusoikeuden voi
      laittaa erkseen omistajalle, ryhmälle ja muille.
* Komennolla `chmod`
* Oikeuksia voi lisätä (**+**), poistaa (**-**) ja asettaa (**=**)
* omistajalle (**u**), ryhmälle (**g**), muille (**o**) tai kaikille (**a**)
* `chmod u=rwx Screenshot-02.png`
* `chmod g+x Screenshot-02.png`
* `chmod o-r Screenshot-02.png`
* `chmod a+r Screenshot-02.png`
* `chmod u=rx,g-x,o=r Screenshot-02.png`




Tehtävät
=========================================

Käynnistä jokin dvd-levyn työpöytä-Linux ja tee tehtävät siinä.
Palautus tiedostona `vastaus-5.odt`.

1. Mikä on käyttäjätunnuksesi uid?
2. Mitkä omistaja ja ryhmä ovat tiedostoilla `/etc/passwd` ja `/etc/shadow`?
3. Mitkä ovat näiden tiedostojen oikeudet omistajalle, ryhmälle ja muille?
4. Kopioi terminaalissa annetun komennon `ls -l /etc/passwd /etc/shadow` tulostus vastaustiedostoosi.
5. Tallenna vastaustiedostosi ja aseta sen oikeudet niin, että käyttäjällä ovat luku- ja kirjoitusoikeudet,
   ryhmällä lukuoikeus ja muilla ei mitään. Miten teit tämän?
6. Ota tiedostohallintaan näkyviin tiedostojen oikeudet niin, että vastaustiedoston tiedot näkyvät,
   ja ota ikkunasta kuvakaappaus. Liitä kuvakaappaus vastaustiedostoosi.
