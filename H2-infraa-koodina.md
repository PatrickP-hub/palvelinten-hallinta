# H2 Infraa koodina

## Työympäristö

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

a) Hei infrakoodi! 



b) Topping.

c) Viisikko tiedostossa.

d) Tee sls-tiedosto




## Lähteet

Karvinen 2014: https://terokarvinen.com/2024/hello-salt-infra-as-code/

Salt contributors: https://docs.saltproject.io/salt/user-guide/en/latest/topics/overview.html#rules-of-yaml

Salt contributors: https://docs.saltproject.io/en/latest/ref/states/top.html

H2 tehtävä https://terokarvinen.com/palvelinten-hallinta/

