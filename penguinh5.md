# h4 Nimekäs

#### A) Nimi
Oppitunnilla ja oppimateriaaleissa suositeltu NameCheap valikoitui omaksikin palvelutarjoajaksi. Ajattelin, että vuokraan domainin itselleni aluksi nyt yhdeksi vuodeksi ja katson sen jälkeen, käytänkö kyseistä palvelua aktiivisesti esim. toisenkin opiskelijan tavoin portfolion ylläpitoon. 

Siirryin siis osoitteeseen https://www.namecheap.com/ ja kirjoitin hakukenttään ensin vain sukunimeni.

<img width="1901" height="652" alt="image" src="https://github.com/user-attachments/assets/c0d3d8ce-4e63-4980-840f-08f5822ebf9d" />

Pelkkää sukunimeä käyttäen domainin .com vuosihinta oli mielestäni aavistuksen liian kallis omaan tarkoitukseeni (831,23 € + seuraava vuosi 15,55 €), joten päädyin kokeilemaan seuraavaksi kokonimeäni.

<img width="1310" height="523" alt="image" src="https://github.com/user-attachments/assets/ffccbca0-70ed-4253-a628-b0092af40cbf" />

juhoarveli.com oli vapaana ja hinnaltaan huomattavasti kohtuullisemmat n. 9 €/ vuosi, joten siirrtyin sen varaukseen, syötin tietoni, jotta sain tilin luotua ja vuosimaksun maksettua ja vahvistin ostoksen. Sain sähköpostiini myös tilin vahvistuspyynnön, jonka kävin hyväksymässä puhelimella. 

<img width="1270" height="765" alt="juhoarveli com" src="https://github.com/user-attachments/assets/9bc4d833-7bc3-4bfa-9561-123f36e619b7" />

<img width="1275" height="590" alt="domain vuokrattu" src="https://github.com/user-attachments/assets/d3e376e8-9e42-4378-998a-94c870f665b8" />

Siirryin seuraavaksi sivustolla Account --> Dashboard --> Domain List. Sivun oikeasta laidasta valitsin domainin kohdalla Manage, ja siirryin Advanced DNS- kohtaan, jotta saan syötettyä oman palvelimeni tiedot. Oppintunnin opastuksen mukaan valitsin tyypiksi A record, Hostiksi @ ja www, sekä syötin palvelimeni IP-osoitteen kohtaan Value. Vahvistin molemmat painamalla vihreää nappia oikeassa laidassa. 

<img width="953" height="312" alt="nimipalvelin" src="https://github.com/user-attachments/assets/ed9e4f6e-cb4b-42f4-a18f-892364030a10" />

Lopuksi vielä syötin domainin selaimen osoitinkenttään juhoarveli.com ja www.juhoarveli.com ja testasin, että ohjaus toimii.

<img width="1278" height="205" alt="testaus nimipalvelin" src="https://github.com/user-attachments/assets/d9abd96e-af81-45f8-ae36-0265efe20a93" />

#### B) Alidomainit
Samassa Advanced DNS- kohdassa luodaan myös seuraavat kaksi alidomainia:
projektit.juhoarveli.com
cv.juhoarveli.com

Aloitin klikkaamalla Add new record ja valitsemalla molemmille alidomaineille tyypiksi A Record ja syöttämällä Host- kohtaan halutut alidomainit "projektit" ja "cv". Kopioin ja liitin IP-osoitteen aikaisemmista ohjauksista ja valitsin TTL 5min, kuten ylemmissäkin. 

<img width="948" height="303" alt="image" src="https://github.com/user-attachments/assets/58d31a14-6e7d-45b8-afe4-da1df6e54735" />

Vahvistin valinnat klikkaamalla vihreät merkit oikeasta reunasta. Testasin lopuksi, että ohjaus toimii.

<img width="1278" height="190" alt="image" src="https://github.com/user-attachments/assets/2788f0a6-d4c1-43f4-a09d-c15f4ba65178" />


#### C) Host- ja Dig- komennot
Aloitin selvittämällä komentojen tarkoituksia Googlettamalla asiaa ja kysymällä sitä myös tekoälyltä (ChatGPT LLM 5.2) ja sain näiden perusteella luotua itselleni näkemyksen, että molemmat ovat DNS- kyselytyökaluja ja niiden avulla kysytään nimipalvelimelta, mitä tietoja domainista on tallennettuna. 

```host``` 
- Tekee DNS-kyselyn ja näyttää ytimekkään, helposti luettavan tuloksen
- Sopii nopeaan tarkistukseen: “mihin IP-osoitteeseen nimi osoittaa” ja mitkä ovat MX-palvelimet
- Piilottaa suurimman osan DNS-protokollan yksityiskohdista.

<img width="652" height="130" alt="image" src="https://github.com/user-attachments/assets/722d64fd-327f-49d9-a403-3364a750394c" />

Kuten kuvassa näkyy, oman domainini ohjaus vie oikeaan IP-osoitteeseen. 

```dig```
- Tekee saman DNS-kyselyn, kuin aikaisempi komento, mutta näyttää koko nimipalvelimen palauttaman DNS-paketin
- Sopii laajempaan vianmääritykseen

Esim. oman domainini osalta juuri ```ANSWER SECTION:``` - näyttää oleliillisimmat tiedot, joista ```A``` merkaa IP-osoitteen mallia (IPv4), ```300``` merkkaa TTL- aikaa sekunteina (5 minuuttia) ja ```94.237.118.156``` kertoo sivuston IP-osoitteen. 

<img width="618" height="363" alt="image" src="https://github.com/user-attachments/assets/889e0e94-5bea-45d6-bd1c-3a88320e6f40" />

Kokeilin seuraavaksi komentoja omille alidomaineille. 

<img width="415" height="37" alt="image" src="https://github.com/user-attachments/assets/49ff7bf4-929d-4f60-abb4-ac5ad2da547f" />

<img width="616" height="552" alt="image" src="https://github.com/user-attachments/assets/9abdf14b-69da-4a0f-a315-4302d7f5d17c" />

Host- komento ei palauta alidomainille sähköpostin ohjauksia, kuten itse päädomain juhoarveli.com. Dig- komento pysyi miltei muuttumattomana, mutta kuten haun tulos osoittaa, on cv.juhoarveli.com oma DNS-tietueensa, eikä esim. alisivu kuten esim. juhoarveli.com/cv. 

Kokeilin samoja komentoja paikallisen pienpanimon sivuille olarinpanimo.fi.

```host olarinpanimo.fi``` kertoo sivuston IP-osoitteen, sekä sähköpostin välitykseen käytettävät tietueet. Olarin Panimo näemmä käyttää hostingservice.fi välittäjänään. 

```dig olarinpanimo.fi``` taas kertoo, että heillä on käytössään IPv4- osoite (A), IP-osoite 185.220.77.11 ja TTL 1200 sekuntia (20 minuuttia). 

<img width="630" height="432" alt="image" src="https://github.com/user-attachments/assets/e1cd1a9b-a653-4aec-bbd5-aaea50ae8aab" />

Kokeilin samoja komentoja myös kansainvälisesti tunnetumman yrityksen domainille pilsnerurquell.com.

```host pilsnerurquell.com``` näyttää jälleen sivuston IP-osoitteen ja sähköpostin välitykseen käytettävät tietueet.

```dig pilsnerurquell.com``` taas näyttää meille, että kyseessä on tälläkin kertaa IPv4- osoite (93.185.98.138) ja sivuston TTL on 900 sekuntia (15 minuuttia)

<img width="646" height="412" alt="image" src="https://github.com/user-attachments/assets/17e371f5-18d7-455f-a180-f048c02c8612" />


