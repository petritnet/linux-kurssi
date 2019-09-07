---
date: "2019-09-07T20:51:00+03:00"
title: "Www-palvelin"
weight: 530
---

Yleisimmin käytetyt www-palvelinohjelmistot ovat **[Apache]** ja **[Nginx]** (lausutaan, kuten "engine-x").
Molemmat ovat avointa lähdekoodia ja löytyvät suoraan Linux-jakeluiden paketinhallinnasta.

Molempien oletusasetukset ovat melko järkevät. Apachella documentroot-hakemisto, eli hakemisto, jonka alle www-sivut
tallennetaan, on useimmissa Linux-jakeluissa `/var/www/html/`. Palvelimen asetustiedostot puolestaan löytyvät hakemistoista
`/etc/apache2/` tai `/etc/httpd/`.


{{% wrapper class="exercises" %}}
Kokeile (Apache2)
---------------

Asenna `apache2`-paketti:

```no-highlight
sudo apt-get install apache2
```

Kokeile sitä menemällä selaimella osoitteeseen: <http://localhost/>.
Näkyviin pitäisi tulla Apachen oletustestisivu.

- Nouda tämä sivu `wget`-komennolla ja kopio saamasi `index.html`-tiedosto
  hakemistoon `/var/www/html/` nimellä `palveluita.html`. (ettei ylikirjoiteta oletussivua)
- Huomaa, että hakemistoon `/var/www/html/` kirjoittamiseen tarvitset root-käyttäjän
  oikeudet. Käytä siis `sudo`-komentoa kopiointikomennon edessä.
- Mene selaimella osoitteeseen: <http://localhost/palveluita.html>
{{% /wrapper %}}


Muita www-palvelimia
---------------------

Linuxille on tarjolla useita avoimen lähdekoodin www-palvelimia:

- *Apache2* – Yleisin, monipuolinen, paljon moduleja
- *Nginx* – Toiseksi yleisin, yleistyy kovaa vauhtia, pieni ja tehokas www-palvelin
- *Lighttpd* – Pieni ja nopea www-palvelin
- Jotkut ohjelmointikielet, kuten Python ja Node.js (Javascript) sisältävät
  toiminnallisuuden toimia itse www-palvelimina.


[Apache]: https://www.apache.org/ (Apache)
[Nginx]: https://www.nginx.com/ (Nginx)
