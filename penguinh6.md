# h6 Salataampa

#### X) Tiivistykset artikkeleista

#### 1) Let’s Encrypt 

https://letsencrypt.org/how-it-works/

- ACME-protokolla hoitaa sertifikaattien hakemisen ja uusimisen automaattisesti ilman manuaalista työtä.
- Palvelimen hallintaoikeus todennetaan automaattisilla haasteilla (HTTP-tiedosto tai DNS-tietue), jolloin erillistä manuaalista tunnistautumista ei tarvita.
- Sertifikaattien haku ja hallinta perustuvat vahvaan salaukseen ja valtuutettuihin avainpareihin, mikä minimoi inhimilliset virheet ja tietoturvariskit.

#### 2) Apache SSL

https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample

- alattu yhteys otetaan käyttöön aktivoimalla ```mod_ssl```-moduuli, määrittämällä palvelin kuuntelemaan porttia 443 ja osoittamalla polut sertifikaatti- sekä avaintiedostoille.
- Palvelin voidaan rajoittaa käyttämään vain nykyaikaisia ja vahvoja salausalgoritmeja (```SSLCipherSuite```), ja eri hakemistoille voidaan asettaa erilaisia turvatasoja.
- Suorituskykyä ja luotettavuutta parannetaan käyttämällä OCSP Stapling -tekniikkaa, joka nopeuttaa sertifikaatin voimassaolon tarkistusta vastaanottajan selaimessa.

- 
