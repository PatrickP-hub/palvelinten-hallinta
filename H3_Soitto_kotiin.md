# H3 Soitto kotiin

## Oma ympäristö

Aloitin harjoituksen Sunnuntaina klo 13 aikoihin päivällä läppärilläni jonka speksit on.

- MacBook air M2 (8GB RAM, MacOS)
- ARM 64-bit
- Oracle VirtualBox Manager
- 4000 MB Base memory
- 20 GB Storage

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

## b) Linux Vagrant

## c) Kaksin kaunihimpi

## d) Herra-orja verkossa

## e) Kokeile vähintään kahta tilaa verkon yli

## Lähteet

Palvelinten hallinta https://terokarvinen.com/palvelinten-hallinta/

Karvinen 2021: Two Machine Virtual Network With Debian 11 Bullseye and Vagrant

Karvinen 2018: Salt Quickstart – Salt Stack Master and Slave on Ubuntu Linux

Karvinen 2023: Salt Vagrant - automatically provision one master and two slaves

Install Vagrant https://developer.hashicorp.com/vagrant/docs/installation

