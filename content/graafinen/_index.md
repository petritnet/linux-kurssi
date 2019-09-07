---
date: "2016-09-11T21:19:57+03:00"
title: "Graafinen käyttöliittymä"
sectiontitle: "Graafinen käyttöliittymä"
weight: 200
type: "index"
menu:
    main:
        weight: 200
---

Usein esiintyvä mielikuva Linuxista pelkkänä tekstipohjaisena ympäristönä
on virheellinen. Linux-järjestelmät ovat lähes alusta saakka toimineet
myös graafisessa tilassa ja niihin on tarjolla useampiakin toiminnallisesti
ja esteettisesti upeita työpöytäympäristöjä.

Linux-järjestelmien ikkunoinnista on tähän saakka vastannut [X Window System](x-ikkunointi),
mutta olemme parhaillaan siirtymävaiheessa, jonka aikana ikkunointijärjestelmäksi
tulee [Wayland](wayland). Osassa Linux-jakeluista, esimerkiksi Ubuntussa,
siirtymä on jo käynnissä ja vanha X Window on vielä varajärjestelmänä.

Erityisesti Unix-tyyppisten käyttöliittymien ominaisuuksina ovat modulaarisuus,
muokattavuus sekä valinnanvara.

Modulaarisuus
==============================

Unixeissa on perinteisesti yritetty välttää monoliittisten ohjelmien tekemistä.
Sen sijaan on pyritty tekemään modulaarisesti pieniä ohjelmia, joita voidaan
yhdistellä muodostamaan monimutkaisempia kokonaisuuksia.

* Vaihtoehtoisia osia samaan käyttöön (valinnanvaraa)
* Modulaarisuus sekä komentorivillä että graafisessa käytössä


Muokattavuus
=============

Käyttöliittymän muokattavuus syntyy siitä, että modulaarisen rakenteen ansiosta lähes mikä tahansa
käyttöliittymän osa on vaihdettavissa johonkin toiseen, joka toteuttaa vastaavan toiminnallisuuden.
Avoin lähdekoodi on mahdollistanut muiden ohjelmistojen tapaan myös käyttöliittymien *forkkaamisen*
eli haarautumisen (fork = haarukka) kehittäjien erilaisten mieltymysten mukaan. Toisin sanoen, jos
käyttöliittymä ei joltain osin ole miellyttänyt, on ohjelmoija voinut lähteä kehittämään sitä
haluamaansa suuntaan. Tämä helpottaa uusien ja erilaisten käyttötapojen ja -liittymien kehittämistä,
koska niiden kehityksen voi aloittaa jo olemassa olevan järjestelmän pohjalta.
Ohjelmointiprojektien keräämä suosio ja kehittäjäjoukko määrää sitten, mitkä
niistä jäävät eloon.


Seuraavaksi tutustutaan, miten ja minkälaisista komponenteista käyttöliittymät koostuvat
sekä mitä erityispiirteitä niihin liittyy.

{{< figure src="/images/Gnome-Ubuntu-desktop.png" link="/images/Gnome-Ubuntu-desktop.png" class="nonfloatimage" title="Gnome" caption="Ubuntun oletustyöpöytä Gnome Ubuntun tyylisellä ulkoasulla." >}}
{{< figure src="/images/elementary-desktop.png" link="/images/elementary-desktop.png" class="nonfloatimage" title="Pantheon" caption="ElementaryOS:n Pantheon-työpöytä." >}}
{{< figure src="/images/fvwm2.jpg" link="/images/fvwm2.jpg" class="nonfloatimage" title="FVWM2" caption="Vanhempi ja 'alkeellisempi' ikkunanhallintaohjelma FVWM2." >}}
