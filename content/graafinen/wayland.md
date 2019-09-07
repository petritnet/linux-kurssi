---
date: "2019-09-02T20:33:00+03:00"
title: "Wayland"
sectiontitle: "Graafinen käyttöliittymä"
weight: 220
---

X alkaa olla jo vanha toteutus, jota on paikattu ja laajennettu yhä uudelleen.
Sitä korvaamaan on suunniteltu uusi ikkunointijärjestelmä
[Wayland](https://wayland.freedesktop.org/).

Waylandissa on tarkoitus olla mukana kerros, joka mahdollistaa vanhojen X-ohjelmien
suorittamisen uudessa ikkunointijärjestelmässä.

{{% wrapper class="theorybox" %}}
Wayland
==============================
* [Wayland](http://en.wikipedia.org/wiki/Wayland_%28display_server_protocol%29)
* Samoja kehittäjiä kuin X.org:lla
* Parempi ja yksinkertaisempi vaihtoehto
* X:ssä historian painolastia, "aivovammoja" ja "paikkaa paikan päällä"
* Jo käytössä muun muassa Jollan SailfishOS-käyttöjärjestelmässä.
* Fedorassa käytössä oletuksena Gnome-työpöydän kanssa versiosta 25 alkaen.
* Ubuntu on kokeillut Waylandia vaihtoehtona X:lle ja vaihto oletukseksi on tulossa.
* [[linux.conf.au 2013] - The real story behind Wayland and X](https://www.youtube.com/watch?v=cQoQE_HDG8g) (Youtube)
{{% /wrapper %}}

{{< youtube cQoQE_HDG8g >}}

Laitteiston ja tarpeiden kehittymisen myötä X on monimutkaistunut pystyäkseen
toteuttamaan tehtävänsä. Waylandissa on tarkoituksellisesti yksinkertaistettu
toimintaa ja monet tehtävät on jätetty itse sovellukselle, kirjastoille ja
Linux-ytimelle.

X:n suurimpia ongelmia on ollut ennen kaikkea se, miten se on historiansa
vuoksi muodostunut eräänlaisina laajennoksina ja paikkoina tekemään tehtäviä,
joihin se ei alkujaan kyennyt. Osittain tämän vuoksi myöskin tietoturvallisuus
ei ole kaikilta osin kohdallaan. Esimerkiksi mikä tahansa käyttäjän suorittama
ohjelma pystyy ottamaan kuvakaappauksen mistä tahansa muusta ikkunasta tai
koko työpöydästä.

Waylandia on suunniteltu toisaalta siltä pohjalta, että se tekee mahdollisimman
vähän ja antaa vain sovelluksille muistialueen, johon ne voivat itse piirtää oman
sisältönsä. Samalla sen suunnittelussa on koetettu ottaa turvallisuus huomioon
entistä paremmin. Osittain tämän vuoksi esimerkiksi juuri kuvakaappausten ottaminen
ja näytön jakaminen ovat olleetkin haasteellisimpia osia Waylandin toteuttamisessa.
