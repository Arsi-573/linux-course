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

<img width="618" height="363" alt="image" src="https://github.com/user-attachments/assets/889e0e94-5bea-45d6-bd1c-3a88320e6f40" />

