+++
date = "2016-09-09T20:31:21+03:00"
title = "Clmystery"
weight = 430
+++

[Clmystery] on komentorivin käytön harjoitteluun tarkoitettu murhamysteeri.

{{% wrapper class="exercises" %}}
Toimi näin:
-------------

1. Lataa tarvittavat tiedostot [zip-pakettina](https://github.com/veltman/clmystery/archive/master.zip)
2. Pura tiedostot koneellesi.
3. Avaa terminaali-ikkuna, siirry paketista purettuun hakemistoon.
4. Tulosta terminaaliin ohjeet komennolla `cat instructions`.

```no-highlight
.OOOOOOOOOOOOOOO @@                                   @@ OOOOOOOOOOOOOOOO.
OOOOOOOOOOOOOOOO @@                                    @@ OOOOOOOOOOOOOOOO
OOOOOOOOOO'''''' @@                                    @@ ```````OOOOOOOOO
OOOOO'' aaa@@@@@@@@@@@@@@@@@@@@"""                   """""""""@@aaaa `OOOO
OOOOO,""""@@@@@@@@@@@@@@""""                                     a@"" OOOA
OOOOOOOOOoooooo,                                            |OOoooooOOOOOS
OOOOOOOOOOOOOOOOo,                                          |OOOOOOOOOOOOC
OOOOOOOOOOOOOOOOOO                                         ,|OOOOOOOOOOOOI
OOOOOOOOOOOOOOOOOO @          THE                          |OOOOOOOOOOOOOI
OOOOOOOOOOOOOOOOO'@           COMMAND                      OOOOOOOOOOOOOOb
OOOOOOOOOOOOOOO'a'            LINE                         |OOOOOOOOOOOOOy
OOOOOOOOOOOOOO''              MURDERS                      aa`OOOOOOOOOOOP
OOOOOOOOOOOOOOb,..                                          `@aa``OOOOOOOh
OOOOOOOOOOOOOOOOOOo                                           `@@@aa OOOOo
OOOOOOOOOOOOOOOOOOO|                                             @@@ OOOOe
OOOOOOOOOOOOOOOOOOO@                               aaaaaaa       @@',OOOOn
OOOOOOOOOOOOOOOOOOO@                        aaa@@@@@@@@""        @@ OOOOOi
OOOOOOOOOO~~ aaaaaa"a                 aaa@@@@@@@@@@""            @@ OOOOOx
OOOOOO aaaa@"""""""" ""            @@@@@@@@@@@@""               @@@|`OOOO'
OOOOOOOo`@@a                  aa@@  @@@@@@@""         a@        @@@@ OOOO9
OOOOOOO'  `@@a               @@a@@   @@""           a@@   a     |@@@ OOOO3
`OOOO'       `@    aa@@       aaa"""          @a        a@     a@@@',OOOO'


There's been a murder in Terminal City, and TCPD needs your help.

To figure out whodunit, go to the 'mystery' subdirectory and start working from there.

You'll want to start by collecting all the clues at the crime scene
(the 'crimescene' file).

The officers on the scene are pretty meticulous, so they've written down
EVERYTHING in their officer reports.

Fortunately the sergeant went through and marked the real clues with
the word "CLUE" in all caps.

If you get stuck, open one of the hint files (from the CL, type 'cat hint1',
'cat hint2', etc.).

To check your answer or find out the solution, open the file 'solution'
(from the CL, type 'cat solution').

To get started on how to use the command line, open cheatsheet.md or cheatsheet.pdf
(from the command line, you can type 'nano cheatsheet.md').

Don't use a text editor to view any files except these instructions,
the cheatsheet, and hints.
```

{{% /wrapper %}}

Tehtävänä on ratkaista Terminal Cityssä tapahtunut murha käyttämällä komentorivityökaluja (`cat`, `head`, `tail`, `grep`,...).
Älä avaa tiedostoja tekstieditorissa.

* Murhan ratkominen aloitetaan siirtymällä `mystery`-hakemistoon ja tutkimalla 
  siellä olevaa tiedosto `crimescene`.
  Tässä tiedostossa kuvaillaan tapahtumien kulku rikospaikalla.
* Tämä tiedosto on valitettavasti aika pitkä, mutta onneksi rivit, jolla on tärkeitä johtolankoja,
  on merkitty isoilla kirjaimilla kirjoitetulla sanalla "**CLUE**".
* Vihjeitä ja faktoja löytyy muista tiedostoista, mutta niissä on tarkoituksella
  niin paljon turhaa tietoa, että halutut tiedot pitää osata suodattaa niistä esiin
  sopivilla komennoilla.
* Jos tulee seinä vastaan, vihjeitä voi matkan varrella pyytää tiedostoista `hint1`, `hint2`, ... , `hint8`.
* Lopullinen ratkaisu on tiedostossa `solution`, *mutta älä kurki sitä liian aikaisin!*


Tehtäviä
=========================

{{% wrapper class="exercises" %}}
Tehtävät 11
=========================

Ratkaise Terminal Cityssä tapahtunut murha. Lähetä palautuksena murhaajan nimi.

Tehtävää voi hyvin tehdä yhdessä.

{{% /wrapper %}}


[Clmystery]: https://github.com/veltman/clmystery (Clmystery)