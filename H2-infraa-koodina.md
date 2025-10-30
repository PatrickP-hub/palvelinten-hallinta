# H2 Infraa koodina

## Työympäristö

Aloitin harjoituksen torstaina päivällä 30.10.2025 omalla läppärilläni.

<img width="510" height="511" alt="image" src="https://github.com/user-attachments/assets/534a4d5f-df8b-493a-a838-f8ef49492111" />

- Macbook Air M2 (8GB RAM, MacOS)
- ARM 64-bit
- Oracle VirtualBox Manager
- 4000 MB Base memory
- 20 GB Storage

## Tiivistelmät

### Hello Salt Infra as a code: https://terokarvinen.com/2024/hello-salt-infra-as-code/

- Saltin avulla pystyy kontrolloimaan tuhansia koneita ja yleensä kaikki alkaa "Hello world!", jolla tarkistetaan että tekstitiedosto on olemassa.
- Salt mahdollistaa infrastruktuurin hallinnan koodina
- Tärkeimpiä state- komentoja ovat esimerkiksi (pkg, file, service, user ja cmd.)

### Salt overview: https://docs.saltproject.io/salt/user-guide/en/latest/topics/overview.html#rules-of-yaml

**Rules of YAML**

- Saltissa käytetään oletuksena YAML- renderöijää.
- Sillä muutetaan YAML- tiedostot Python tietorakenteiksi.
- Avaimien pitää olla tarkkoja
- Älä käytä tabia vaan space näppäintä

**YAML simple structure**

- YAML koostuu kolmesta perus elementistä:
1. Scalars (Numero tai teksti)
2. Lists (Avaimen alla useita arvoja "-" viivalla ja kahdella välilyönnillä)
3. Dictionares (Pareja ja listoja)
  
**List and dictionaries - YAML block structures**

- YAML:issa rakenteet tehdään lohkoina:
- Sisennyksellä kerrotaan mihin jokin tietty asia tai arvo kuuluu.

### The top file: https://docs.saltproject.io/en/latest/ref/states/top.html

**Introduction**

- Useimmat järjestelmät koostuvat ryhmistä koneista, jotka toimivat yhdessä ja tekevät samanlaisia tehtäviä.
- Ylläpitäjä voi määrittää roolit näille eri ryhmille, jotka "palvelevat" verkkosivua
- Top tiedosto top.sls kertoo, mitkä roolit kuuluvat millekin koneiden ryhmille. 

**A basic example**

- Top tiedosto koostuu kolmesta osasta:
1. Environment (kansio jossa on state tiedostoja)
2. Target (ryhmä koneita, johon stateja sovelletaan)
3. State- tiedostot (tiedostot, jotka määrittelee asetukset kohteisiin)

Tiivistelmiin meni noin tunnin verran aikaa.

a) Hei infrakoodi! 

Kokeilin 'sudo salt-call --local' komennolla toimiko koodi paikallisesti. 

Sitten tein tyhjän tiedoston komennolla 'sudo salt-call --local state.single file.managed /tmp/tiedosto' 

<img width="864" height="726" alt="image" src="https://github.com/user-attachments/assets/5d8034ba-17dd-4a1e-a8d9-5531f8bef13e" />

Kuten kuvasta näkyy tyhjä tiedosto tehtiin onnistuneesti.

Sitten katsoin 'ls /tmp/tiedosto' komennolla, että tiedosto oli näkyvissä

<img width="864" height="76" alt="image" src="https://github.com/user-attachments/assets/a96cb766-0eae-449d-960b-3c516e1b3268" />

Ennen kuin aloitin niin komennolla 'sudo salt-call --local state.apply sls' testasin löytyykö tiedostoa, mutta sitä ei löydy koska en ole vielä tehnyt sitä.

<img width="607" height="92" alt="image" src="https://github.com/user-attachments/assets/61103612-1312-4464-ab6e-0ccb0c1f3c2c" />

Tämän jälkeen kirjoitin komennot 'ls /srv/salt' varmistin että kansio näkyy, mutta ei näy koska en vielä ole tehnyt sitä.

Sitten tein kansion 'sudo mkdir /srv/salt/' ja 'ls /srv/salt'. Nyt komento toimi.

<img width="920" height="110" alt="image" src="https://github.com/user-attachments/assets/694f92d6-2257-4328-95ca-76b98f15c870" />

Sitten siirryin 'cd /srv/salt' ja tarkistin että olin oikeassa kansiossa 'pwd'.

<img width="367" height="55" alt="image" src="https://github.com/user-attachments/assets/9184dfdf-b4b4-4cb7-9d83-c6198c51afbe" />

Tämän jälkeen tein salt kansioon "sls" kansion ja sitten siirryin 'cd' komennolla kansioon.

<img width="458" height="73" alt="image" src="https://github.com/user-attachments/assets/d6b8c1a4-2d9e-42e4-8329-f7d692a9cf8e" />

Kun tämä vaihe oli tehty tein esimerkkitiedoston 'sudoedit init.sls' GNU nano editorilla. 
Kirjoitin tiedostoon /tmp/slstiedosto: ja file.managed , mikä pitäisi tehdä esimerkkitiedoston onnistuneesti.

<img width="340" height="128" alt="image" src="https://github.com/user-attachments/assets/7de37cd0-5b29-4ad8-bbbc-272cbc6b0a6e" />

Ctrl + X, Y ja enter. Että sain tallennettua tiedoston. 
Nyt oli vihdoin aika antaa komento: 'sudo salt-call --local state.apply sls' 

<img width="449" height="363" alt="image" src="https://github.com/user-attachments/assets/55c13e71-10fe-471b-bda8-e6b47ceed6b8" />

Kuten kuvassa näkyy "slstiedosto created" tiedosto oli onnistuneesti tehty. 
Testasin viellä 'cat /srv/salt/sls/init.sls', jonka pitäisi näyttää että esimerkkitiedosto näkyy. 

<img width="601" height="58" alt="image" src="https://github.com/user-attachments/assets/2183f070-98c1-43d1-a8fc-7489ddfca373" />



b) Topping.

c) Viisikko tiedostossa.

d) Tee sls-tiedosto




## Lähteet

Karvinen 2014: https://terokarvinen.com/2024/hello-salt-infra-as-code/

Salt contributors: https://docs.saltproject.io/salt/user-guide/en/latest/topics/overview.html#rules-of-yaml

Salt contributors: https://docs.saltproject.io/en/latest/ref/states/top.html

H2 tehtävä https://terokarvinen.com/palvelinten-hallinta/

