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
