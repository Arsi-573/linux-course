# h7 Maalisuora

#### A) Hei maailma kolmella eri kielellä.

Ajattelin käyttää tässä oppitunnilla läpikäytyjä kieliä, eli Bash, Python ja C. 

#### Bash 
Aloitin luomalla tiedoston "Halojata Maailma" microlla komennolla ´´´micro halojata´´´. Microon kirjoitin scriptiksi:
```
Bash
#!/bin/bash

# Tervehdys
echo "Halojata Muailma!"
```

<img width="342" height="131" alt="image" src="https://github.com/user-attachments/assets/d66a340f-a840-460c-99f5-d80aa7e70a5f" />

Tallensin skriptin Microssa ```Ctrl + S``` ja suljin sen ```Ctrl + Q```. Seuraavaksi kokeilin komentoa nykyisessä hakemistossa ```./halojata```, joka kertoi, että oikeuteni eivät tähän leikkiin riitä. Korjasin tilanteen komennolla ```chmod ugo+x /home/juho/halojata```, joka antaa tarvittavat oikeudet, että saan tulosteen annettuani komennon nykyisessä hakemistossa. Tämän jälkeen uudestaan ```./halojata``` ja sain vastaukseksi microssa aikaisemmin kirjoitetun "Halojata Mualima!".

<img width="568" height="126" alt="image" src="https://github.com/user-attachments/assets/4739c50b-e096-4a01-ac1e-b9f67777d3db" />

Seuraavaksi tämä "halojata" tuli saada missä tahansa kohdassa terminalia kirjoitettavaksi komennoksi, eli omaksi "ohjelmakseen". Katsoin ensin, että aikaisemmilla komennoilla sain nuo oikeudet kuntoon, joten komento: ```ls -l /home/juho/halojata``` sain tulokseksi ```-rwxrwxr-x ...```, eli tiedoston omistajalla juho ja ryhmällä juho on kaikki tarvittavat oikeudet. 

Seuraavaksi kopioin kirjoitetun skriptin omille ohjelmille varattuun hakemistoon komennolla ```sudo cp halojata /usr/local/bin``` hyväksyin kopioinnin salasanalla kokeilin tämän jälkeen komentoa ```halojata```.

<img width="735" height="158" alt="image" src="https://github.com/user-attachments/assets/871a509d-b586-4dfc-9c78-aae30bb28269" />

#### Python3 
Aloitin antamalla komennoksi ```micro halojata.py```, jotta pääsen luomaan skriptin. Microssa kirjoitin ensin shebangin, että sain tulkkauksen päälle, jolloin koko scripti näytti kuvassa osoitetulla tavalla:

<img width="461" height="105" alt="image" src="https://github.com/user-attachments/assets/baacb344-7c29-476a-8808-76d98d0e3ce4" />

Seuraavaksi tarkistin oikeudet ```ls -l /home/juho/halojata.py``` ja huomattuani, että suorituslupa puuttuu, komensin ```chmod +x halojata.py```. Tämän jälkeen kopioin skriptin ohjelmistohakemistoon ```sudo cp halojata.py /usr/local/bin``` laitoin salasanan, ja kokeilin lopuksi vielä ```halojata.py```, ja tämähän toimi myös moitteetta. 

<img width="775" height="181" alt="halojata python" src="https://github.com/user-attachments/assets/a8325536-c890-4215-aa8c-a709a460824e" />

#### C
Aloitin tarkastamalla, että minulla on oikea kääntäjä GCC käytettävissä, joten laitoin vuoronperään komennot ```sudo apt update``` ja ```sudo apt install gcc```. GCC olikin asennettu jo aikaisemmin ja oli peräti viimeisimmässä versiossaan, joten pääsin etenemään itse skriptin tekoon!

<img width="918" height="317" alt="image" src="https://github.com/user-attachments/assets/2093faa4-6e24-4d62-8258-9c6170a224e1" />

Itse skriptin syöttöön ryhdyttiin taas Microlla ```micro halojata.c``` ja microssa syötin kuvassa näkyvän skriptin:

<img width="503" height="161" alt="image" src="https://github.com/user-attachments/assets/8e2fa89e-118a-4bfc-93da-c5867abac0db" />

Kokeilin seuraavaksi suorittaa äskein kirjoitetun ohjelman ```./halojata.c```, mutta oikeidet eivät riittäneet. Tarkistin oikeudet ```ls -l /home/juho/halojata.c``` ja lisäsin suoritusoikeudet ```chmod +x halojata.c```. Seuraavaksi kokeilin uudelleen ```./halojata.c```, mutta sain kuvassa näkyvän virheilmoituksen:

<img width="753" height="211" alt="image" src="https://github.com/user-attachments/assets/26454433-3c5b-47a9-a525-bed7f53fdc0e" />

Virhe johtui siis siitä, että käännös ei ole vielä valmis. Koska GCC oli meillä jo asennettuna sain käännöksen tehtyä komennolla ```gcc -o halojata_c halojata.c```, ja tämän jälkeen kokeilin komentoa uudelleen nykyisessä hakemistossa ```./halojata.c```. 

<img width="510" height="81" alt="image" src="https://github.com/user-attachments/assets/c0cc68ab-5891-4118-b1f2-e4ec2a7a8efd" />

Kun kokeilu oli valmis, kopioin skriptin ohjelmistohakemistoon ```sudo cp halojata_c /usr/local/bin/``` ja tämän jälkeen kokeilin kirjoittamalla ```halojata.c```. Sain tulokseksi hieman huolestuttavasti "Command not found", kunnes tajusin, että olin epähuomiossa kirjoittanutkin koodin väärin, joten korjasin tilanteen kirjoittamalla komennon uusiksi oikealla tavalla ```halojata_c```, jolloin koodi toimi toivotulla tavalla.

<img width="627" height="184" alt="image" src="https://github.com/user-attachments/assets/af7b7b3b-8cad-4514-9c7a-69c1a241c613" />

#### C) Itse keksimä komento
Ajattelin, että terminaali kaipaa komennon, joka eroaa hieman muista, joten kirjoitin komennon ```pepe```.

Koska halusin komennon tulostavan "kuvan" ASCII- muodossa, hain internetistä hakusanalla "ASCII pepe" ja löysin komentooni sopivan ASCII-art pohjan, kopioin sen ja avasin terminalissa micron komennolla ```micro pepe```. Microssa kirjoitin ensimmäiselle riville ```#!/bin/bash``` ja toiselle riville ```cat << 'EOF'```. EOF (End-of-File) pitää huolen, että bash antaa tekstin juuri siinä muodossa kun se on syötetty microon. 

<img width="517" height="500" alt="image" src="https://github.com/user-attachments/assets/28326b4d-3a66-4518-a8bb-4ed1d8c58feb" />

Lopuksi kirjoitin loppuun uudestaan ```EOF``` tallensin ja suljin micron ja siirryin antamaan oikeudet, ja siirtämään tiedoston komentohakemistoon. 

<img width="495" height="555" alt="image" src="https://github.com/user-attachments/assets/b134e385-63a3-49e6-92bb-3b50435c2515" />

Lopuksi vielä kokeilin komentoa kirjoittamalla ```pepe```. 

<img width="455" height="463" alt="image" src="https://github.com/user-attachments/assets/1acc5d56-c49c-4eb2-b5e5-4cab2feb4f4c" />

#### D) Laboratorioharjoitus
Valitsin tehtäväksi IoT12 Oy:n ympäristön perustamisen:

https://terokarvinen.com/2016/arvioitava-laboratorioharjoitus-linux-palvelimet-ict4tn021-1-uusi-ops-alkusyksylla-2016/

Aloitin luomalla uuden virtuaalikoneen tätä harjoitusta varten nimeämällä sen Virtuaboxissa IoT12oy- nimellä. 

<img width="915" height="673" alt="image" src="https://github.com/user-attachments/assets/e6ccdd4d-64b8-48e9-9979-5f032d46a757" />

Ensimmäisenä tehtävässä tuli varmistaa, että eri resurssien käyttö on tilastoitu koko harjoituksen ajalta. Ajoin tätä varten heti terminalin aikaistuani komennon ```vmstat 10 > resurssit.txt &``` Tällä komennolla resursseista otetaan näyte 10 sekunnin välein ja ne viedään tiedostoon resurssit.txt. ```&``` merkki lopussa pitää ohjelman aktiivisena taustalla, jotta voin jatkaa harjoituksen tekemistä. 

Seuraavaksi asensin palomuurin komennoilla ```sudo apt update``` ja ```sudo apt install ufw```. Sallin palomuurissa SSH- yhteyden ottamisen koneelle komennolla ```sudo ufw allow ssh``` ja kytkin palomuurin aktivoitumaan automaattisesti koneen käynnistyessä ```sudo ufw enable```. Lopuksi tarkistin, että portti 22 on muurissa auki komennolla ``` sudo ufw status verbose```.

<img width="610" height="276" alt="image" src="https://github.com/user-attachments/assets/17064c7d-825b-4098-aa65-c859c7a93923" />

Seuraavaksi asensin SSH:n komennolla ```sudo aot install ssh``` ja siirryin etähallintaohjelmiston asennukseen. kirjoitin komennoksi tehtävän ohjeistuksessa olleen ```wget http://terokarvinen.com/qrs/terorep/pool/main/t/terorep/terorep_0.0.3_all.deb```, mutta valitettavasti tulos tästä oli 404, not found. 

<img width="933" height="181" alt="image" src="https://github.com/user-attachments/assets/5ab4c74e-dd86-47f4-b4bb-274c025f11f1" />

Koska sivua ei enää ole, käyn asian nyt teoriapohjaisena läpi:
Etähallintaohjelmiston asennus:
```
sudo dpkg -i terorep_0.0.3_all.deb
sudo apt-get update
sudo apt-get -y install terowatch ssh
```

Näillä komennoilla etähallinta ohjelma olisi asennettuna ja toiminnassa. 

Seuraavaksi vaiheessa oli käyttäjien luonti. Kaikilla tulee olla esimerkkisivu ja kaikkien käyttäjätunnukset ja salasanat tulee listata lab.txt. Kyseinen tiedosto tulee suojata niin, ettei sitä voi muut lukea. Alla listaus käyttäjistä:
- Maija Mehilälinen
- Peter Ö
- Oskar Jäärä
- John Do
- Verner Vrij
- Mikko Möttönen
- Jalmari Ähkä
- Håkan Swarz
- Maija Maitoparta

Aloitin asentamalla apache2:n ja PHP-ohjelmointikielen, sekä ```libapache2-mod-php``` -moduulin, joka yhdistää Apachen ja PHP:n toisiinsa. 

<img width="777" height="137" alt="image" src="https://github.com/user-attachments/assets/2b7e81c5-2c9b-4696-a864-19341f2cc529" />

seuraavaksi aktivoin ```userdir``` -moduulin komennolla ```sudo a2enmod userdir``` ja käynnistin apaschen uudestaan ```sudo systemctl restart apache2```. Asensin Micron ```sudo apt install micro -y``` ja avasin ```sudo micro /etc/apache2/mods-available/php*.conf``` -tiedoston, josta kävin poistamssa rivin ```php_admin_flag engine Off```. Debian kieltää oletusasetuksena PHP:n suorituksen käyttäjien kotihakemistoissa, joten asennustiedostoa on muokattu tästä syystä. 

<img width="913" height="578" alt="image" src="https://github.com/user-attachments/assets/f860a9e7-8520-4b6e-bc4e-b0a08f567761" />

Lopuksi käynnistin apachen uudestaan ```sudo systemctl restart apache2```. Koska käyttäjälistaus on pitkä ja yksittäisten käyttäjien luonti on todella työlästä, aikaa vievää ja puuduttavaa, luodaan skripti, joka tekee käyttäjätunnukset, generoi vahvat salasanat, luo PHP-sivun ja asentaa oikeudet Apachea varten. 

Luodaan siis skripti Microlla ```micro asenna_kayttajat```. Kysyin tähän apua tekoälyltä skriptin luomiseen syötteellä "Tee minulle bash skripti, jossa luodaan käyttäj(koko nimi ja nimeen viittaava käyttäjätunnus) + salasana + luodaan jokaiselle käyttäjälle oma PHP-sivu niin että Apache2 voi lukea sivun ja lopuksi tallennetaan käyttäjän koko nimi, käyttäjätunnus ja salasana lab.txt- tiedostoon, johon oikeudet on vain minulla". Sain vastauksena valmiin skriptin, jonka syltin omilla muutoksillani Microon.

<img width="1158" height="750" alt="image" src="https://github.com/user-attachments/assets/27eef5a1-6741-40ad-a550-e271d126f5a5" />

Annoin ohjelmalle oikeudet ```chmod +x asenna_kayttajat.sh``` ja kokeilin ajaa ohjelman ```./asenna_kayttajat.sh```, syötin salasanan ja sain kuvan mukaisen virheen, joka viittasi, että jonkin käyttäjätunnuksen kohdalta puuttui ```:```.

<img width="785" height="187" alt="image" src="https://github.com/user-attachments/assets/25593b97-9ad9-4ba5-8db7-57ff27888db5" />

Avasin skriptin uudelleen ```micro asenna_kayttajat.sh``` ja huomasin, että olin kirjoittanut Verner Vrijn kohdalla ```Verner Vrij_vernerv```, joten korjasin tämän vaihtamalla ```_``` tilalle ```:```. 

<img width="496" height="317" alt="image" src="https://github.com/user-attachments/assets/e9af5035-4424-407b-9079-c5d9ff09572f" />

Tallensin ja suljin skriptin Microssa ja tämän jälkeen poistin vanhan ```lab.txt``` -tiedoston, jotta vältytään tuplamerkinnöiltä komennolla ```rm ~/lab.txt```. Tämän jälkeen ajoin skriptin uudelleen (joka myös luo automaattisesti tiedoston uudelleen) ```./asenna_kayttajat.sh```.

<img width="671" height="266" alt="image" src="https://github.com/user-attachments/assets/5fa217fa-bf14-4958-83d3-bb420c5fc6c5" />

Koska muut käyttäjät oli jo aiemmin luotu, Terminaali ilmoittaa, että nämä käyttäjät ovat jo olemassa. Skripti kuitenkin generoi käyttäjille uudet salasanat ja tallensi uudet tiedot lab.txt- tiedostoon. Verneri puuttuu listasta, koska hänen käyttäjäänsä ei luotu kirjoitusvirheen vuoksi aiemmalla kerralla ohjelmaa suorittaessa, mutta nyt sekin on luotu. Tarkistin vielä käyttäjälistauksen ajamalla komennon ```cat ~/lab.txt```.

<img width="982" height="267" alt="image" src="https://github.com/user-attachments/assets/4d487ca1-863d-4583-b538-69f30445e42e" />

Testasin vielä seuraavaksi parin eri käyttäjän PHP-sivujen luonnin kokeilemalla selaimella. Ajoin ensin terminalissa komennon ```hostname -I```, jotta sana palvelimen IP-osoitteen ylös, joka on 10.0.2.15. Tämän jälkeen kokeilin selaimessa Maija Mehiläisen ja Peter Ön sivut syöttämällä selaimen osoitinkenttään:
http://10.0.2.15/~maijam/

<img width="1607" height="267" alt="image" src="https://github.com/user-attachments/assets/b6f33ced-799e-4fab-b804-50c80881b645" />

Ja http://10.0.2.15/~petero/

<img width="1615" height="267" alt="image" src="https://github.com/user-attachments/assets/28841fe9-0441-42c3-b90c-2f8e2e0a6f19" />

