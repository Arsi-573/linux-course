# h4 Maailma kuulee

#### X) Artikkeleiden tiivistys

#### Susanna Lehto 2022 Teoriasta käytäntöön pilvipalvelimen avulla (h4)
- Vuokrasi virtuaalipalvelimen (DigitalOcean) ja ohjasi domain-nimen sille.
- Suojasi palvelimen palomuurilla (UFW + sallit SSH-portti).
- Asensi Apache-web-palvelimen, teki kotisivut näkyviksi ja varmisti, että ne toimivat julkisesti.
- Päivitti palvelimen ohjelmat useilla apt-komennoilla varmistaakseen uusimmat päivitykset.

#### Karvinen 2012: First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS
- Opastaa uuden VPS-palvelimen perustamisen DigitalOceanissa ja kirjautumisen ensimmäisillä asetuksilla.
- Neuvoo palomuurin (UFW) käyttöönoton ja SSH-yhteyden suojaamisen sekä ei-root-käyttäjän luomisen.
- Korostaa ohjelmistojen päivittämisen ja turvallisen salasanan tärkeyttä heti alussa.
- Lopuksi ohjeistaa VPS:n käyttöönoton jälkeen esim. web-palvelimen ja DNS-nimen käytön.

#### A) Virtuaalipalvelimen vuokraus
Päädyin vuokraamaan oman virtuaalipalvelimeni suomaiselta Upcloud Oy:ltä, koska heillä on tiedetysti kaksi eri konesalia Suomen rajojen sisässä ja haluan tukea kotimaista toimijaa. Loin heidän sivustolleen käyttäjätunnuksen omilla tiedoillani ja siirryin virtuaalipalvelimen vuokraukseen. 

<img width="1910" height="357" alt="image" src="https://github.com/user-attachments/assets/506d6d2d-ea40-4077-bfe7-da4dfd2bb394" />

Valinta Cloud Servers ja sen jälkeen sivuston oikeasta reunasta Deploy server. Tämän jälkeen päästään uuden serverin luontiin ja ensimmäisenä valitaan sijainti. Oma valintani on FI-HEL1, joka on Suomessa sijaitseva konesalitila. 

<img width="1327" height="782" alt="image" src="https://github.com/user-attachments/assets/584e90af-51ab-4ead-8919-3f9475357af4" />

Opettajan ohjeistuksen mukaan, valitsin itselleni pienimmän Developer- vaihtoehdon, joka sisältää 1Gb RAM-muistia ja 10Gb tallennustilaa 3 € kuukausimaksua vastaan.

<img width="1341" height="842" alt="image" src="https://github.com/user-attachments/assets/ecdea5db-606a-4dbc-8843-213c84025c39" />

Kaksi seuraavaa kohtaa voidaan ohittaa tekemättä muutoksia, joissa kysytään tallennustilan lisätilaa, sekä automaattisia varmuuskopioita. Seuraavassa vaiheessa valitaan käyttöjärjestelmä, joka itsellä valikoitui myös käytössäni olevan käyttöjärjestelmän mukaan Debian 13:sta.

<img width="1352" height="823" alt="image" src="https://github.com/user-attachments/assets/cceffa47-12aa-4e92-83ec-6375359bff1c" />

Seuraavat kohdat Network ja Optionals pidetään muuttamattomina ja siirrytään kohtaan Login Method, jossa valitaan SSH Keys. Myös seuraava kohta Initialization script voidaan jättää huomioimatta ja siirtyä suoraan vimeiseen vaiheeseen, jossa oma virtuaaliserveri nimetään. Annoin itse Hostnameksi Juho ja Server name Juho. Määrä pidetään ennallaan (1) ja klikataan tämän jälkeen Deploy. 

<img width="1032" height="398" alt="image" src="https://github.com/user-attachments/assets/9b5783b1-93e6-4fe1-9edd-f7fda265bce0" />

#### B) Alkutoimet omalla virtuaalipalvelimella
Seuraavan vaiheen tein oppitunnin aikana opettajan ohjeistuksella. 

Ensimmäisenä haettiin SSH avainpari
```ssh keygen```
