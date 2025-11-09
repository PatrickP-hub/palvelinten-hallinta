# H3 Soitto kotiin

## Oma ympäristö

Aloitin harjoituksen Sunnuntaina klo 13 aikoihin päivällä läppärilläni jonka speksit on.

- MacBook air M2 (8GB RAM, MacOS)
- ARM 64-bit
- Oracle VirtualBox Manager
- 4000 MB Base memory
- 20 GB Storage

<img width="511" height="378" alt="image" src="https://github.com/user-attachments/assets/8c0130b7-fc1c-4b5d-b140-fd9c7f7e206d" />

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
Josta latasin Vagrant tiedoston MacOS järjestelmälleni ARM64 pohjaisen version.

<img width="750" height="140" alt="image" src="https://github.com/user-attachments/assets/2aa95a99-c9ba-45cf-973a-c32fddac686d" />

Menin eteenpäin ja lopuksi installoin Vagrantin

<img width="396" height="251" alt="image" src="https://github.com/user-attachments/assets/7c9d7992-8633-4a06-9b0d-614b8b5037dd" />

Lopuksi varmistin vielä Terminaalissa komennolla `version -- vagrant` löytyykö Vagrant

<img width="316" height="26" alt="image" src="https://github.com/user-attachments/assets/1b712b39-9de5-4a0a-b4b8-602d87db829a" />

Sehän löytyi!

## b) Linux Vagrant



## c) Kaksin kaunihimpi

## d) Herra-orja verkossa

## e) Kokeile vähintään kahta tilaa verkon yli

## Lähteet

Palvelinten hallinta https://terokarvinen.com/palvelinten-hallinta/

Karvinen 2021: https://terokarvinen.com/2021/two-machine-virtual-network-with-debian-11-bullseye-and-vagrant/

Karvinen 2018: https://terokarvinen.com/2018/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/?fromSearch=salt%20quickstart%20salt%20stack%20master%20and%20slave%20on%20ubuntu%20linux

Karvinen 2023: https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file

Install Vagrant https://developer.hashicorp.com/vagrant/docs/installation

