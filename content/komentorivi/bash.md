+++
date = "2016-09-09T20:38:14+03:00"
title = "Bash-ohjelmointi"
weight = 440
+++

Sen lisäksi, että Bash on interaktiivinen tekstipohjainen käyttöliittymä,
se on myös täysiverinen ohjelmointikieli, josta löytyvät muun muassa
muuttujat, silmukat ja ehtolauseet. Sen ohjelmointiominaisuuksia voidaan
käyttää sekä interaktiivisesti tehostamaan komentorivin käyttöä tai erikseen
suoritettavien monimutkaisempien ohjelmien, skriptien, tekemiseen.

Yksinkertaisimpia tapoja käyttää ohjelmointia komentorivillä on jonkin
toistuvan toiminnon suorittaminen useammalle tiedostolle silmukassa.


{{% wrapper class="exercises" %}}
Esimerkki
-----------------------------

Pohdi, mitä seuraava komento tekee:

```no-highlight
for nimi in kuva1 kaavio2 kuvio3; do convert $nimi.png $nimi.jpg ; done
```


{{% /wrapper %}}





Tiedostonimien laajennus
============================

Bash-komentorivillä annetuissa komennoissa tiedostoihin voi viitata lyhennysmerkinnöillä.

* Yksinkertaisimpia lyhennysmerkintöjä ovat *jokerimerkit* `*` ja `?`.
* `*` tarkoittaa nollaa tai useampaa mitä tahansa merkkiä.
* `?` tarkoittaa tarkalleen yhtä mitä tahansa merkkiä.

Bash laajentaa jokerimerkkejä sisältävän merkkijonon listaksi tiedostoja, jotka sopivat merkkijonon esittämään kaavaan.
Bash tekee laajennuksen lyhennysmerkinästä "täyteen kokoon" ennen kuin ne annetaan kutsutulle ohjelmalle.

{{% wrapper class="exercises" %}}
Kokeile
-----------------------------
```
 echo *
 ls *.txt
```

{{% /wrapper %}}




Tiedostonimien laajennus: esimerkkejä
--------------------------------------

`*i.txt`
:   Kaikki (tässä hakemistossa olevat) tiedostot, jotka päättyvät `i.txt`
:   Esimerkiksi: `Petri.txt, tiedostoni.txt, i.txt`

`Pekk?.html`
:   Kaikki (tässä hakemistossa olevat) tiedostot, joissa on `?`-merkin kohdalla jokin merkki.
:   Esimerkiksi: `Pekka.html`, `Pekko.html`, `Pekkk.html`, `Pekk1.html`, `Pekk?.html`

`Documents/a??a`
:   Kaikki `Documents`-hakemistossa olevat nelikirjaimiset tiedostonimet, jotka alkavat ja päättyvät kirjaimella `a`.
:   Esimerkiksi: `aaaa`, `abba`, `aaba`, `a4.a`, `a=Aa`, `a..a`

`/etc/???????????*.conf`
:   Kaikki `/etc`-hakemistossa olevat tiedostot, joissa on vähintään 11 merkkiä, joiden jälkeen pääte `.conf`
:   Esimerkiksi: `/etc/ca-certificates.conf`, `/etc/popularity-contest.conf`, `/etc/request-key.conf`, `/etc/usb_modeswitch.conf`




Tiedostonimien laajennus: kirjainjoukot
---------------------------------------

Jokerimerkkien lisäksi voidaan käyttää myös muita lyhenteitä, kuten kirjainjoukkoja.
Kirjainjoukko on kokoelma hakasulkeiden välissä lueteltuja merkkejä (tai "merkkiväli").
Kirjainjoukko täsmää tarkalleen yhteen merkkiin, samoin kuin jokerimerkki `?`.

`[abcd]`
:   Mikä tahansa kirjaimista `abcd`.
:   Esimerkiksi: `[THL]upu.txt` laajentuu tiedostonimiksi
    `Tupu.txt` `Hupu.txt` `Lupu.txt`, jos sen nimiset tiedostot löytyvät tästä hakemistosta.


`[a-d]`
:   Mikä tahansa kirjain kirjaimesta `a` kirjaimeen `d` (aakkosjärjestyksessä).
:   Esimerkiksi `[a-zA-Z0-9]upu.txt` täsmää vaikkapa tiedostoihin `Tupu.txt`, `tupu.txt`, `Aupu.txt`, `3upu.txt` jne.

`[^abc]`
:    Mikä tahansa muu merkki kuin `a`, `b` tai `c`.
:    Esimerkiksi `[^THL]upu.txt` täsmää vaikkapa tiedostoihin, `Pupu.txt`, `3upu.txt` ja `tupu.txt`, mutta **EI** tiedostoihin `Tupu.txt`, `Hupu.txt` ja `Lupu.txt`.



Tiedostonimien laajennus: sanajoukot
-------------------------------------

Sanajoukot toimivat millä tahansa merkkijonoilla, ei vain kyseisessä hakemistossa olevilla tiedostonimillä.
Sanajoukon käyttö ei siis edellytä vastaavan tiedoston olemassaoloa.
Sanajoukko on aaltosulkujen väliin kirjoitettu pilkuilla eroteltu luettelo sanoja.

`{Aku,Mikki,Hessu}`
:   Pidempiä vaihtoehtoja voi luetella `{`- ja `}`-merkien välissä pilkulla erotettuna.
    Esimerkiksi `{Mo,Ve}rtti` laajentuu: `Mortti` ja `Vertti`.

```
 echo {Mo,Ve}rtti
 Mortti Vertti
```





Muuttujat
============================

Bashissa voi käyttää myös merkkijonomuuttujia.

* Sijoituksessa: `<muuttujannimi>=<muuttujanarvo>` (ei välilyöntejä `=`-merkin ympärillä)
* Muuttujan käyttö: `$<muuttujannimi>` (dollari muuttujan nimen edessä)

```
 NIMI=Petri
 KOKONIMI='Petri Salmela'
 KOKONIMI="$NIMI Salmela"
```

* Jos muuttujaan sijoitettavassa tekstissä on välilyöntejä, on se ympäröitävä lainausmerkeillä.
   (tai kirjoitettava välilyönnin eteen merkki `\`)





Muuttujat: Lainausmerkit
--------------------------

* Kahdet eri lainausmerkit: `'` ja `"`
* "Kaksoislainausten" välissä olevat muuttujaviittaukset korvautuvat muuttujan arvolla.
* 'Yksöislainausten' välissä olevat ovat vain merkkijonoja ja käsitellään sellaisenaan.

```
 echo "$NIMI Salmela"
 Petri Salmela
 echo '$NIMI Salmela'
 $NIMI Salmela
```






Erikoismerkit
============================

Joskus tiedostonimissä tai muuten komentorivillä on tarve käyttää esimerkiksi merkkejä `?*[]{}$'"`
tavallisina merkkeinä ilman niiden edellä esiteltyjä erikoismerkityksiä.
Erikoismerkitys riisutaan merkiltä kirjoittamalla sen eteen `\`-merkki.

```
 echo a\*
 echo "Mies sanoi \"Moi\"."
 echo \{Mo,Ve\}rtti
```






"Takahipsukat"
============================

Joskus halutaan sijoittaa muuttujaan jonkin komennon tulostus. Tämä onnistuu Bashissa
"takahipsukoilla" `` ` `` (backticks), joka saadaan näppäimistöltä pitämällä shift pohjassa ja
painamalla backspacen vasemmalla puolella olevaa näppäintä. Tämän jälkeen voi joutua painamaan
välilyöntiä, jotta merkki tulee näkyviin. Näiden välissä oleva komento suoritetaan ja korvataan sen tulosteella.

```
 aika=`date`
 echo $aika
 Wed Oct 24 19:15:49 EEST 2012
```

Bashissa saman voi tehdä myös merkinnällä `$(...)`, joka voi joskus olla käytännöllisempi. Siis:

```
 aika=$(date)
 echo $aika
 Wed Oct 24 19:15:49 EEST 2012
```





Komennot jonossa (;)
============================

Samalla komentorivillä voi antaa useampia komentoja kerralla.
Jos komennot erotellaan `;`-merkillä, ne suoritetaan peräkkäin.

```
 echo Moi ; ls ; echo "Sillä selvä"
```

Tekee täsmälleen saman kuin eri riveille kirjoitettuina.

```
 echo Moi
 ls
 echo "Sillä selvä"
```

Komentojen kirjoittaminen samalle riville `;`-merkillä eroteltuina on hyödyllistä
yleensä esimerkiksi tilanteissa, joissa yksittäisten komentojen suoritus saattaa kestää
kauan, esimerkiksi tunteja, eikä käyttäjä halua jäädä valvomaan niiden suoritusta.
Tällöin ne voidaan vain käskeä suoritettavaksi peräkkäin.



Komennot jonossa (&&)
============================

Ohjelmat kertovat niin kutsutulla paluuarvolla, onnistuiko sen suoritus. (0=onnistui, jotain muuta = ei onnistunut)
Paluuarvoa ei tulosteta, mutta Bash saa sen ohjelman suorituksen loputtua ja sitä voidaan käyttää esimerkiksi seuraavasti:

Jos komennot erotellaan merkeillä `&&`, seuraava komento suoritetaan vain, jos edellinen komento onnistui. (looginen "ja")

```
 echo Terve && ls --option && ls
 echo Moi && ls && ls -l
```

Ensimmäisellä rivillä komento `ls --option` on virheellinen, joten viimeistä `ls`-komentoa ei suoriteta.
Toisella rivillä kaikki kolme komentoa onnistuvat.





Komennot jonossa (||)
============================

Jos komennot erotellaan merkeillä `||`, seuraava komento suoritetaan vain, jos edellinen epäonnistui. (looginen "tai")

```
 komento || ls --option || ls
 komento || echo moi || ls
```

Ensimmäisellä rivillä vasta kolmas komento onnistuu. Toisella rivillä toinen komento onnistuu ja siksi kolmatta ei enää yritetä suorittaa.





Testit
============================

`test`-komennolla voidaan testata erilaisten väitteiden totuutta. Vastaus saadaan komennon paluuarvona.

```
 test 5 -lt 10 && echo "Joo, 5 oli pienempi kuin 10"
```

Testataan onko luku 5 pienempi kuin (lt=less than) luku 10. Koska näin on, paluuarvona palautetaan 0 (eli komento onnistui)
ja seuraava komento suoritetaan.

```
 test -f /etc/hosts && echo "Jep, tiedosto /etc/hosts on olemassa ja tavallinen tiedosto"
```

Edelliset testit voidaan myös kirjoittaa muodossa: `[ 5 -lt 10 ]` ja `[ -f /etc/hosts ]`. Huom: välilyönnit ovat tärkeitä!

```
 [ 5 -lt 10 ] && echo "Joo, 5 oli pienempi kuin 10"
 [ -f /etc/hosts ] && echo "Jep, tiedosto /etc/hosts on olemassa ja tavallinen tiedosto"
```





Tiedostotestejä
============================

| Tiedostotesti | Testin merkitys   |
|---------------|-------------------|
|-d *nimi*   |Tiedosto *nimi* on hakemisto|
|-f *nimi*   |Tiedosto *nimi* on tavallinen tiedosto|
|-L *nimi*   |Tiedosto *nimi* on symbolinen linkki|
|-r *nimi*   |Tiedosto *nimi* on luettava tiedosto|
|-w *nimi*   |Tiedosto *nimi* on kirjoitettava tiedosto|
|-x *nimi*   |Tiedosto *nimi* on ajettava tiedosto|
|-s *nimi*   |Tiedosto *nimi* on epätyhjä|
|*nimi1*   -nt *nimi2* |Tiedosto *nimi1* on uudempi tiedosto kuin *nimi2*|
|*nimi1* -ot *nimi2*   |Tiedosto *nimi1* on vanhempi tiedosto kuin *nimi2*|




Merkkijonotestit ja lukutestit
============================

Merkkijonotestit

| Merkkijonotesti | Testin merkitys |
|-----------------|-----------------|
|*s1* = *s2* |Merkkijonot *s1* ja *s2* ovat samat |
|*s1* != *s2* |Merkkijonot *s1* ja *s2* ovat erit |
|-z *s1* |Merkkijono *s1* on tyhjä|
|-n *s1* |Merkkijono *s1* on epätyhjä|

 
Lukutestit

| Lukutesti | Testin merkitys  |
|-----------|------------------|
|*a* -eq *b* |Luvut *a* ja *b* ovat yhtä suuret |
|*a* -ne *b* |Luvut *a* ja *b* ovat eri suuret |
|*a* -gt *b* |Luku *a* on suurempi kuin *b* |
|*a* -ge *b* |Luku *a* on suurempi tai yhtä suuri kuin *b* |
|*a* -lt *b* |Luku *a* on pienempi kuin *b* |
|*a* -le *b* |Luku *a* on pienempi tai yhtä suuri kuin *b* |




Testausten looginen yhdistely
============================

|Testien yhdistelmä | Testin merkitys        |
|-------------------|------------------------|
|*t1* -o *t2* |Testi *t1* tai testi *t2* tosi (OR) |
|*t1* -a *t2* |Testi *t1* ja testi *t2* tosia (AND) |
|! *t1* |Testi *t1* on epätosi (NOT) |
|\( ja \) |Testien järjestely sulkeilla|




Ehtolause (`if`)
============================

Testataan, pitääkö jokin väite paikkansa ja tehdään jotain toimintoja sen perusteella.

```bash
 if [ $NIMI = "Petri" ]
 then
   echo "Tervetuloa"
 fi
```

Jos väite pitää paikkansa, suoritetaan `then`-sanan ja `fi`-sanan välissä olevat komennot.

```bash
 if [ $NIMI = "Petri" ]
 then
   echo "Tervetuloa"
   echo "Kiitos"
 else
   echo "Tervemenoa"
   echo "Ole hyvä"
 fi
```

`else`-lohkon komennot suoritetaan, jos väite ei pidä paikkaansa.





Ehtolause yhdellä rivillä
---------------------------

Sama yhdelle riville kirjoitettuna.

```
 if [ $NAME = "Petri" ]; then echo "Tervetuloa"; echo "Kiitos"; else echo "Tervemenoa"; echo "Ole hyvä"; fi
```

Huomaa, puolipisteet `;`, jotka erottavat komennot toisistaan! Puolipisteitä ei tarvita, jos komennot kirjoitetaan eri riveille.





Toisto (`for`)
============================

Toisinaan tarvitsee toistaa sama toiminto useammalle merkkijonolle. Bashissa `for`-silmukka on muotoa:

```
 for nimi in lista sanoja jotka käydään läpi
 do
   echo $nimi
 done
```

Silmukka käy läpi kaikki listan `lista sanoja jotka käydään läpi` sanat, sijoittaa kunkin vuorollaan
muuttujaan `nimi` ja tulostaa sen. Sama yhdellä rivillä:

```
 for nimi in lista sanoja jotka käydään läpi; do echo $nimi; done
```

For-silmukalla on helppo käydä läpi vaikka kaikki jonkin tietyn ehdon täyttävät tiedostonimet:

```
 for tiedosto in *.txt; do echo "Lopetusrivi--------" >> $tiedosto; done
```

Tämä lisää kaikkien työhakemistossa olevien txt-päätteisten tiedostojen loppuun rivin, jossa on teksti `Lopetusrivi--------`.






`seq`
============================

`for`-silmukan yhteydessä eräs hyvin käytännöllinen aputyökalu on ohjelma nimeltä `seq`, joka tulostaa lukujonoja.

* Yhdellä argumentilla tulostaa luvut alkaen yhdestä ja päättyen annettuun numeroon: <br> `seq 7` tulostaa luvut 1-7. Kokeile!
* Kahdella argumentilla tulostaa luvut ensimmäisestä toiseen: <br> `seq 3 7` tulostaa luvut `3`, `4`, `5`, `6`, `7`. Kokeile!
* Kolmella argumentilla tulostaa luvut ensimmäisestä toisen suuruisella askeleella kolmanteen: <br> `seq 3 2 7` tulostaa
  luvut `3`, `5`, `7`. Kokeile!
* Askel voi olla myös negatiivinen tai desimaaliluku: <br> `seq 2 -0.5 -1` tulostaa luvut `2`, `1.5`, `1`, `0.5`, `0`, `-0.5`, `-1`. Kokeile!
* Lisävalitsin `-w` lisää eteen etunollia niin, että kaikki tulostettavat luvut ovat kaikki yhtä pitkiä, eli pisimmän pituisia: <br>
  `seq -w 1 100` tulostaa luvut `001`, `002`, `003`,..., `099`, `100`. Kokeile!




Toisto (`for` ja `seq`)
============================

`for`-silmukka ja `seq`-komento ovat joskus käytännöllistä yhdistää:

```
 for i in `seq 1 7`; do wget http://viikonvalo.fi/images/clementine-$i.png; done
```

* `` `seq 1 7` `` korvautuu komennon `seq 1 7` tulosteella, eli luvuilla `1 2 3 4 5 6 7`.
* `for`-silmukassa muuttuja `i` saa vuorollaan nämä (välilyönnillä erotellun listan) arvot
  ja `wget` hakee seitsemän eri kuvaa.




Toisto (`while`)
============================

Toinen toistorakenne on `while`-silmukka, jota suoritetaan niin kauan kuin sen ehto on voimassa,
eli ehtona oleva ohjelma suoritetaan onnistunesti.

```
 i=0;
 while [ $i -lt 7 ]
 do
   echo $i
   i=$(($i+1))
 done
```
Silmukkaa suoritetaan niin kauan kuin muuttujan `i` arvo on pienempi kuin (`-lt`) 7.
Joka kierroksella tulostetaan muuttujan arvo `$i` ja kasvatetaan muuttujaa yhdellä.
Huom: Bashissa matemaattisen lausekkeen arvon voi laskea merkinnällä: `$((lauseke))`.
Tämä merkintä korvautuu lausekkeen arvolla.






Syötteen lukeminen (`read`)
============================

`read`-komento ottaa käyttäjältä (standardisyötteestä) tekstiä ja sijoittaa sen annettuun muuttujaan.

```
 read nimi
 Petri
 echo $nimi
 Petri
```




Toisto (`while` ja `read`)
============================

`while`-silmukkaan yhdistettynä saadaan:

```
 while read i; do echo $i; done
```

Tämä silmukka toistaa kaiken, mitä sille kirjoittaa. Silmukan saa lopettamaan antamalla sille syötteen lopetusmerkin: **ctrl-d**.

Syötteen voi ohjata tälle silmukalle myös tiedostosta:

```
 while read i; do echo "Tiedostosta: $i"; done < /etc/passwd
```




Skripti-tiedoston tekeminen
============================

Bash-komennot voidaan kirjoittaa tiedostoon, josta ne suoritetaan. Skripti-tiedosto aloitetaan rivillä,
joka kertoo, että kyseessä on bash-skripi:

```
 #!/bin/bash
```
Tämän jälkeen kirjoitetaan suoritettavat komennot ja tallennetaan tiedosto. Usein tiedostossa käytetään päätettä `.sh`, mutta tämä ei ole pakollista.
Merkistä `#` alkaen rivin loppuun on kommenttia.
Käyttäjille annetaan tiedoston suoritusoikeus komennolla `chmod a+x tiedostonnimi.sh`.

Jos tiedosto ei ole jossain `$PATH`-muuttujassa luetelluista poluista, pitää se suoritetaan komennolla `./tiedostonnimi.sh`
tai viittaamalla siihen jotenkin muuten absoluuttisella tai suhteellisella polulla.





Bash-skripti
============================

Kirjoita seuraava tiedostoon `toisto.sh`, anna siihen suoritusoikeudet ja aja se.

```
#!/bin/bash
nimi=$@
if [ -z $nimi ]
then
  echo "Anna nimesi: "
  read nimi
fi
for i in `seq -w 10`
do
  echo "$i: Terve, $nimi."
done
```

{{% wrapper class="exercises" %}}
Suoritus
-----------------------------

Suoritetaan `toisto.sh`.

```no-highlight
$ ./toisto.sh 
Anna nimesi: 
Petri
01: Terve, Petri.
02: Terve, Petri.
03: Terve, Petri.
04: Terve, Petri.
05: Terve, Petri.
06: Terve, Petri.
07: Terve, Petri.
08: Terve, Petri.
09: Terve, Petri.
10: Terve, Petri.
```

{{% /wrapper %}}





Tehtäviä
============================
{{% wrapper class="exercises" %}}
Tehtävät 12
============================

Palautus tiedostona `vastaus-12.txt`.
Kerro jokaisessa kohdassa käyttämäsi komento tai komennot sekä niiden tulostukset.

1. Luettele kaikki tiedostot, jotka ovat hakemistossa `/etc` ja jotka alkavat kirjaimella `h` tai kirjaimella `f` ja
   joiden kolmas kirjain on `s`. Millä komennolla sait tulosteen?
2. Millä komennoilla teet seuraavat?
   * Laita muuttujaan `nimi` oma nimesi.
   * Laita muuttujaan `aika` komennon `date +"%Y-%m-%d %H:%M:%S"` tuloste.
   * Tulosta `echo`-komennolla rivi, joka on muotoa: `nimi tulosti tämän aika`.
3. Millä komennoilla teet seuraavat?
   * Testaa Bashilla (yhdellä rivillä), onko tiedosto `/etc/passwd` luettavissa ja tulosta "Luettavissa", jos on.
   * Testaa Bashilla (yhdellä rivillä), onko tiedosto `/etc/passwd` kirjoitettavissa ja tulosta "Kirjoitettavissa", jos on.
   * Tee sama tiedostolla `/etc/shadow`.
4. Tee tyhjät tiedostot, joiden nimet ovat `Alster`, `Buster` ja `Custer`. Miten teet seuraavan?
   * Muuta tiedostojen nimiksi `Alster.txt`, `Buster.txt` ja `Custer.txt`. Käytä hyödyksi `for`-silmukkaa ja `mv`-komentoa.
5. Anna komentorivillä komento `alias`
   * Mitä komento tulosti?
   * Selvitä, mitä `alias`-komento tekee ja miten se toimii sivulta <http://linux.fi/wiki/Alias>
   * Miten määrittelet aliaksen `ltxt`, joka luettelee kaikki tässä hakemistossa olevat `.txt`-päätteiset tiedostot?

{{% /wrapper %}}


Linkkejä:

* [Bash-ohjelmointi](http://koti.welho.com/jkajaste/bash.html)
* <http://linux.fi/wiki/Bash-skriptaus>
* <http://www.turuxi.org/Tapaaminen_13.01.2011>