# H3 Soitto kotiin

## Oma ympäristö

Aloitin harjoituksen Sunnuntaina klo 13 aikoihin päivällä pöytäkoneellani jonka speksit on.

- Pöytäkone (16GB RAM, Windows 11, AMD Ryzen 2600 6-ydin, 256GB SSD)
- AMD 64-bit
- Oracle VirtualBox Manager
- 4000 MB Base memory
- 60 GB Storage

<img width="539" height="392" alt="image" src="https://github.com/user-attachments/assets/f6ce02cd-c4d5-4422-b003-dbe9e595c512" />


## Lue ja tiivistä

### Karvinen 2021: https://terokarvinen.com/2021/two-machine-virtual-network-with-debian-11-bullseye-and-vagrant/

- Vagrant määrittää VirtualBox- koneet automaattisesti
- Siihen ei tarvita graafista käyttöliittymää
- Vagrant myös automatisoi SSH-kirjautumisen

### Karvinen 2018: https://terokarvinen.com/2018/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/?fromSearch=salt%20quickstart%20salt%20stack%20master%20and%20slave%20on%20ubuntu%20linux

- Tekstissä kerrotaan miten asennetaan Salt ja hallittavat koneet eli Slave-koneet
- Hallittavat koneet voivat olla NAT:in tai palomuurin takana tai tuntemattomassa osoitteessa.
- Slave:n täytyy aina tietää missä master sijaitsee sekä jokaisella slavella on oltava eri ID.

### Karvinen 2023: https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file

- Infra as Code - Your wishes as a text file
  * tärkeää on `init.sls` tiedostossa kahden välilyönnin sisennys
  * ennen `init.sls` on tärkeää luoda hakemisto johon se tehdään 
- top.sls - What Slave Runs What States
  * `top.sls` määrittelee mitkä statet ajetaan milläkin slavella
  * kaikki statet pystyy ajaa yhdella komennolla `sudo salt '*' state.apply`
    
## a) Hello Vagrant!

Löysin osoitteesta : https://developer.hashicorp.com/vagrant/downloads
Josta latasin Vagrant tiedoston Windows järjestelmälleni AMD64 pohjaisen version.

<img width="293" height="191" alt="image" src="https://github.com/user-attachments/assets/da2b524f-bba1-4431-8727-bb8b056ef045" />

Menin eteenpäin ja lopuksi installoin Vagrantin
Ja Vagrant pyysi restarttaamaan koneeni

Lopuksi varmistin vielä Terminaalissa komennolla `version -- vagrant` löytyykö Vagrant

<img width="291" height="43" alt="image" src="https://github.com/user-attachments/assets/f1219184-4895-45d2-87d1-ac6921650fb0" />

Sehän löytyi!

## b) Linux Vagrant

Sitten oli aika luoda Vagrant file
Aluksi tein kansion mkdir vagrantti
Siirryin kansioon cd vagrantti
Ja loin tiedoston vagrant init debian/bookworm64

<img width="602" height="180" alt="image" src="https://github.com/user-attachments/assets/7f4f5c51-9428-42bd-8471-e1ca7ff4f00b" />

Tämän jälkeen käynnistin Vagrantin komennolla vagrant up

<img width="928" height="217" alt="image" src="https://github.com/user-attachments/assets/2549a7ac-892f-4900-a2c9-8522348649cb" />

Kuten kuvasta näkyy tähän kului noin aikaa 4 minuuttia



## c) Kaksin kaunihimpi

## d) Herra-orja verkossa

## e) Kokeile vähintään kahta tilaa verkon yli

## Lähteet

Palvelinten hallinta https://terokarvinen.com/palvelinten-hallinta/

Karvinen 2021: https://terokarvinen.com/2021/two-machine-virtual-network-with-debian-11-bullseye-and-vagrant/

Karvinen 2018: https://terokarvinen.com/2018/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/?fromSearch=salt%20quickstart%20salt%20stack%20master%20and%20slave%20on%20ubuntu%20linux

Karvinen 2023: https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file

Install Vagrant https://developer.hashicorp.com/vagrant/docs/installation

