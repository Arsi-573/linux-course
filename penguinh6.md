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

Seuraavana asensin Certbot- ohjelmiston, jotta saan palvelimeni HTTPS- suojauksen automatisoitua. Tämä tapahtui syöttämällä terminalissa komennoksi ```sudo apt install certbot``` ja kuittaamalla asennuksen kirjaamalla ```y``` ja return. 

<img width="901" height="380" alt="certbot asennus" src="https://github.com/user-attachments/assets/07165aed-f664-4136-9f49-69eb014de4a5" />

Tämän jälkeen asensin vielä Certbotin Apache- laajennuksen komennolla ```sudo apt install python3-certbot-apache``` ja kuittasin asennuksen kirjoittamalla ```y``` ja painamalla return. 

<img width="686" height="289" alt="python3-certbot asennus" src="https://github.com/user-attachments/assets/68c6c5c3-56a7-4df3-ba9a-428dd3e595bc" />

Lopuksi vielä hain sertifikaatin komennolla ```sudo certbot```, kirjoitin oman sähköpostiosoitteeni, kuittasin palvelun ehdot ja hyväksyin Electronic Frontier Foundationin kaikki mainospostit molemmat kirjoittamalla terminalissa ```y``` ja painoin return. Tämän jälkeen Sertifikaatin haku oli valmis ja se otettiin käyttöön automaattisesti palvelimelleni. 

<img width="929" height="660" alt="sudo certbot" src="https://github.com/user-attachments/assets/8b832d33-9e60-4eee-a98b-722bba81c1c0" />

Lopuksi vielä testasin sertifikaatin toimivuuden terminalissa komennolla ```curl https://juhoarveli.com``` ja kirjoittamalla selaimeni osoitinkenttään https://juhoarveli.com.

<img width="814" height="251" alt="curl testaus https" src="https://github.com/user-attachments/assets/990487f4-dae9-4ec0-915f-c418f6cd2216" />

<img width="1278" height="822" alt="image" src="https://github.com/user-attachments/assets/1b094c62-9756-4c0a-aa0c-484558f2c9a6" />

<img width="710" height="588" alt="image" src="https://github.com/user-attachments/assets/cf16fb73-34e8-42ce-9ecb-77d05d075edd" />

#### B) A-rating

Seuraavaksi oli tarkoitus tarkastaa sivuston TLS (Transport Layer Security). Siirryin oppimateriaalissa mainitulle sivustolle https://www.ssllabs.com/ssltest/ ja syltin oman URL:n juhoarveli.com ja laitoin haun päälle klikkaamalla "Submit". Hetken odottelun jälkeen raportti oli valmis ja tästäkin selvittiin puhtain paperein kokonaisarvosanalla A.

<img width="1100" height="628" alt="image" src="https://github.com/user-attachments/assets/358b3f5d-256b-4f83-a84c-64950d615599" />


### Lähteet 

https://terokarvinen.com/linux-palvelimet/

https://letsencrypt.org/how-it-works/

https://httpd.apache.org/docs/2.4/ssl/ssl_howto.html#configexample

https://www.ssllabs.com/ssltest/
