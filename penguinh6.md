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


#### A) TLS- sertifikaatti Let's Encryptin kautta

Seurasin oppitunnilla käytyjä ohjeita ja tein niiden mukaan asiat samalla tavalla aloittamalla kirjautumalla terminalista palvelimelle komennolla ```ssh juhoarveli.com```. Tämän jälkeen testasin sivun toimivuuden komennolla ```curl http://juhoarveli.com```, jolla sain sivuston html- tiedoston tulostettua. Kokeilin myös komentoa ```curl https://juhoarveli.com``` josta oletettu tulostus oli ```curl: (7) Failed to connect to juhoarveli.com port 443 after 0 ms: Could not connect to server```. 

<img width="862" height="561" alt="sisäänkirjaus ssh + curl testaus" src="https://github.com/user-attachments/assets/9d0a6f8d-a1a1-4ef4-9583-86c0398de761" />

Seuraavana asensin Certbot- ohjelmiston, jotta saan palvelimeni HTTPS- suojauksen automatisoitua. Tämä tapahtui syöttämällä terminalissa komennoksi:
```sudo apt update
sudo apt install certbot
y```
