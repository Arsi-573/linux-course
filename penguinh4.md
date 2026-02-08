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
```ssh keygen``` - komennolla ja hakattiin Return- näppäintä niin kauan, että päästään taas komentosyötteeseen. Tämän jälkeen tarkastin hakemiston komennoilla ```ls``` ja ```ls -a```. Hakemistossa löytyy tämän jälkeen .ssh, joka avattiin komennolla ```cd .ssh``` .

<img width="1280" height="892" alt="Terminal0 - SSH" src="https://github.com/user-attachments/assets/74653f95-6563-4fef-ad0e-265681e49a4a" />

Valmiit avaimet tulostuu, joista ensimmäisenä on salainen avain ja seuraavana julkinen avain, jonka tunnistaa ```.pub``` - päätteestä.

Ylempi id- tunniste kopioitiin ja annoin komennon ```.ssh$ cat id_ed25519.pub```, joka tulostaa julkisen avainparin. Tämän jälkeen yhdistin virtuaalipalvelimeni antamalla sen IP-osoitteen, joka löytyy luomani virtuaalipalvelimeni Overview- kohdasta IP.

<img width="1047" height="483" alt="image" src="https://github.com/user-attachments/assets/22bf55ba-3236-466c-8794-1aaaa0543870" />

IP-osoitteen kopioinnin jälkeen syötin komennoksi ```ssh root@94.237.118.156```. Kun terminaali kysyy "Are you sure you want to continue connecting?", annetaan komento ```yes``` ja lyödään return- näppäintä. 

<img width="874" height="322" alt="image" src="https://github.com/user-attachments/assets/104d8965-5e6b-459b-bb34-873baf6a9a18" />

Tämän jälkeen loin käyttäjän juho, komennolla ```sudo adduser juho``` ja täytin nimen, sekä salasanan pyydettäessä, ja jätin muut tyhjäksi. Loppuun vastaukseksi ```y``` ja Return. 

<img width="698" height="300" alt="image" src="https://github.com/user-attachments/assets/224c5078-a391-4233-bba4-2e00353c01ec" />

Jatkoin antamalla käyttäjälle pääkäyttäjän oikeudet komennoilla ```sudo adduser juho sudo``` ja ```sudo adduser juho adm```.

<img width="482" height="50" alt="image" src="https://github.com/user-attachments/assets/9cd7f69e-d781-45a8-b060-f7d5710b819a" />

Yhdistin oman koneeni virtuaalipalvelimeeni komennolla ```ssh juho@94.237.118.156```. 

<img width="1038" height="195" alt="image" src="https://github.com/user-attachments/assets/75a73662-193d-40ee-be9e-e08fdf66a81a" />

Ja poistin myös root- tunnuksen käytöstä komennolla ```sudo usermod --lock root``` ja poistin .ssh- hakemiston rootin alta komennolla ```sudo rm/root/.ssh/authorized_keys```.

<img width="561" height="112" alt="image" src="https://github.com/user-attachments/assets/edea059a-f921-464e-b5e8-136ce515da3c" />

#### C) Testisivun korvaus.
Seuraavaksi yhdistin itseni takaisin virtuaalipalvelimeeni komennolla ```ssh juho@94.237.118.156``` ja tämän jälkeen asensin apache2 komennoilla ```sudo apt update``` ja ```sudo apt install apache2```.  Tämän jälkeen tarkistin selaimesta, että apache2- oletussivu näkyy osoitteessa http://94.237.118.156, kuten näkyikin. Siirryin siis takaisin terminaaliin ja siirryin muokkaamaan html- tiedostoa komennolla ```sudo micro /var/www/html/index.html```. Poistin sivun sisällön, painamalla pohjaan Ctrl + K, joka tyhjenti rivit ylhäältä alas pikaisesti ja kirjoitin tilalle oman sisältöni lainaten ideoita tekoälyltä kysymyksellä: "Anna ehdotus räväkästä sivusta, joka ei sisällä muuta kuin tekstiä ja sitäkin vain hyvin vähän.". Varsinaisen tekstin keksin itse sivuston sisällöksi. 

<img width="815" height="237" alt="image" src="https://github.com/user-attachments/assets/264f91d7-1e1e-4472-8e6c-fe085ec4c398" />

Lopputuloksen tarkistin vielä siirymällä Windowsin Chrome- selaimeen ja syöttämällä sivuni selaimeen. Lopputulos on toimiva.

<img width="762" height="356" alt="image" src="https://github.com/user-attachments/assets/5b35a499-5d3a-47cf-9074-385658b303dd" />


### Lähteet 

https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/

https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/

https://terokarvinen.com/linux-palvelimet/

https://upcloud.com/

ChatGPT LLM 5.2 käytetty oman sivun sisällön luontiin. 
