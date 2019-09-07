---
date: "2017-03-02T20:38:27+03:00"
title: "Kuvien katselu ja käsittely"
weight: 330
---


Kuvat ja niiden katselu sekä muokkaus ovat tärkeä osa nykyaikaista tietokoneen käyttöä.
Näihin tehtäviin Linux-järjestelmistä löytyy useita sovelluksia.

Katseluun
===============================

Kuvien katseluun on kussakin työpöytäympäristössä jokin oletusohjelma, jolla kuvatiedostot oletuksena
näytetään. Näissä on tyypillisesti käytettävissä muutama perus muokkaustoiminto, kuten kuvan kierrot,
peilaukset ja rajaukset. Osa ohjelmista on keskittynyt varsinaiseen kuvien näyttämiseen ja osassa
on lisäksi kuvakirjaston tai -gallerian ominaisuuksia. Galleriasovelluksissa kuvista pidetään
tyypillisesti jonkinlaista tietokantaa, josta niitä voidaan etsiä metatietojen, kuten päivämäärän
tai tapahtumaleimojen mukaan.

{{< figure src="/images/gwenview-3.jpg" link="/images/gwenview-3.jpg" class="floatimage floatright" title="Gwenview" >}}

Muutamia kuvankatseluohjelmia:

* Eye of Gnome eli Image Viewer (Unity, Gnome)
* Gwenview (KDE Plasma)
* Geeqie (Gnome)
* Shotwell (Gnome, galleria)
* Digikam (KDE, galleria)




Käsittelyyn
===============================

Kuvankäsittelyyn Linux-alustalla löytyy useita ohjelmia. Photoshopiin tottuneet usein vähättelevät
vaihtoehtoja, mutta useimpiin käyttötarkoituksiin nämä ovat täysin riittäviä.

GIMP
-------

{{< figure src="/images/Gimp-3.png" link="/images/Gimp-3.png" class="floatimage floatright" title="Gimp" >}}

[GIMP], eli GNU Image Manipulation Program, on Linux-alustojen perinteinen
kuvankäsittelyohjelma. Se on monipuolinen ja toimiva, joskin käyttöliittymä
saattaa erityisesti Photoshopiin tottuneille tuntua paikoittain vieraalta.
GIMP on tehty erityisesti kuvien mukaamiseen ja se tukee erilaisia filttereitä
sekä omien toimintojen ohjelmointia.

GIMP käyttää Gnomen pohjana olevaa GTK-käyttöliittymäkirjastoa. GTK onkin alkujaan
luotu tätä varten ja se on saanut nimensä GIMPiltä. (GIMP Toolkit)

GIMP on asennettavissa myös Windows-käyttöjärjestelmään.

Krita
------

{{< figure src="/images/krita-5.jpg" link="/images/krita-5.jpg" class="floatimage floatright" title="Krita" >}}

[Krita] on tuoreempi ja nopeasti kehittyvä kilpailija GIMPille. Kuvankäsittelyn lisäksi Krita
painottuu erityisesti kuvien piirtämiseen sekä digitaaliseen maalaamiseen ja tarjoaa siihen hyvät työkalut.

Pinta
------

[Pinta] on GIMPIä ja Kritaa kevyempään kuvankäsittelyyn tarkoitettu ohjelma. Siitä puuttuvat
monipuolisimmat kuvankäsittelytoiminnot, mutta kaikki perustoiminnot siitä löytyvät. Siksi
Pinta onkin helppo käyttöönotettava satunnaiselle kuvankäsittelijälle tai pikaiseen kuvan
piirtämiseen.

Pinta on taustaltaan avoimen lähdekoodin kopio aiemmasta Windowsille tarjolla olevasta
Paint.net -ohjelmasta.

MyPaint
-------

[MyPaint] on digitaalisen maalarin ja piirtäjän työkalu. Siinä ei ole varsinaisia
kuvankäsittelytoimintoja vaan siinä on käytettävissä suuri määrä erilaisia siveltimiä
ja kynien teriä digitaaliseen piirtämiseen ja maalaamiseen. Sen kanssa kannattaa
käyttää piirtopöytää ja kynää.


Valokuvien jälkikäsittelyyn
===============================

Valokuvien jälkikäsittelyyn voidaan Linuxissa käyttää tarpeen mukaan jotain edellä luetelluista
kuvien näyttämiseen tai käsittelyyn tarkoitetuista ohjelmista.

{{< figure src="/images/darktable-5.jpg" link="/images/darktable-5.jpg" class="floatimage floatright" title="Darktable" >}}

Ammattimaisempaan jälkikäsittelyyn on käytettävissä [Darktable], joka tarjoaa käyttöön virtuaalisen
valopöydän (lighttable) ja pimiön (darkroom). Sillä on hyvä lisätä häviöttömästi kuviin suodattimia
ja viedä lopullinen tuotos uuteen kuvatiedostoon.





Vektorigrafiikka
===============================

Vektorigrafiikkaohjelmilla voidaan piirtää tarkkoja skaalautuvia piirroskuvia ja kaavioita. Paras työkalu
vektoripiirrosten tekemiseen on useimmiten [Inkscape], jonka tallennusmuoto on standardi svg.
(Scalable Vector graphics)

Muita vektorigrafiikkaa tuottavia ohjelmia ovat LibreOfficne Draw sekä diagrammien ja kaavioiden piirtämiseen
soveltuva [Dia].


[GIMP]: https://www.gimp.org/ (GIMP)
[Krita]: https://krita.org/ (Krita)
[Pinta]: https://pinta-project.com/ (Pinta)
[MyPaint]: http://mypaint.org/ (MyPaint)
[Darktable]: http://www.darktable.org/ (Darktable)
[Inkscape]: https://inkscape.org/ (Inkscape)
[Dia]: http://dia-installer.de/ (Dia)
