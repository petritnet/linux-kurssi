+++
date = "2017-02-25T21:16:04+03:00"
title = "Tulevaisuus"
sectiontitle = "Graafinen käyttöliittymä"
weight = 240
+++

X alkaa olla jo vanha toteutus, jota on paikattu ja laajennettu yhä uudelleen.
Sitä korvaamaan on suunniteltu kahtakin uutta ikkunointijärjestelmää:
[Wayland](https://wayland.freedesktop.org/) ja [Mir](https://wiki.ubuntu.com/Mir)

Molemmissa on tarkoitus olla mukana kerros, joka mahdollistaa vanhojen X-ohjelmien
suorittamisen uudessa ikkunointijärjestelmässä.


[Wayland](http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29)
==============================

* Samoja kehittäjiä kuin X.org:lla
* Parempi ja yksinkertaisempi vaihtoehto
* X:ssä historian painolastia, "aivovammoja" ja "paikkaa paikan päällä"
* Jo käytössä muun muassa Jollan SailfishOS-käyttöjärjestelmässä.
* Fedora 25:ssä käytössä oletuksena Gnome-työpöydän kanssa. X on v
* [[linux.conf.au 2013] - The real story behind Wayland and X](https://www.youtube.com/watch?v=cQoQE_HDG8g) (Youtube)

Laitteiston ja tarpeiden kehittymisen myötä X on monimutkaistunut pystyäkseen toteuttamaan alkuperäisen
tehtävänsä. Waylandissa on tarkoituksellisesti yksinkertaistettu toimintaa ja monet tehtävät on jätetty
itse sovellukselle, kirjastoille ja Linux-ytimelle.

Mir
==============================

* Canonicalin/Ubuntun vaihtoehto X:lle
* On kehitetty erityisesti Ubuntu Phonea sekä työpöytäkäyttöliittymän ja mobiilikäyttöliittymän
  yhdistävää Unity8:aa silmällä pitäen.
* Mir on herättänyt jonkin verran kiistaa ja Canonicalia on syytetty "sooloilusta", koska alkoivat
  kehittää omaa järjestelmää sen sijaan, että olisivat tukeneet Waylandin kehitystä.
