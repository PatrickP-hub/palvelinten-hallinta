# H4 Pkg-file-service
## Oma työympäristö

Aloitin harjoituksen Sunnuntaina klo 13 aikoihin kotiympäristössä
- Pöytäkone (Windows 11, 16GB RAM, AMD Ryzen 2600 6-ydin, 256GB SSD)
- Tehtävässä käytin Windowsin komentokehotetta

## x) Lue ja tiivistä
### Karvinen 2018 https://terokarvinen.com/2018/04/03/pkg-file-service-control-daemons-with-salt-change-ssh-server-port/?fromSearch=karvinen%20salt%20ssh

- (state) tila luodaan Saltin avulla, mikä tarkoittaa sitä että SSH-palvelin on asennettuna ja sen asetustiedosto on halutun mukainen
- SSHD- konfiguraatiota voidaan muokata esimerkiksi vaihtamalla porttia 8888
- Artikkelissa myös tarkistetaan että SSH vastaa uudessa portissa ja kaikki toimii

## a) SSHouto. Lisää uusi portti, jossa SSHd kuuntelee (Vagrantin avulla)

Aloitin tehtävän avaamalla Windows:in komentokehotteen ja tarkistin että vagrantti löytyy koneelta `vagrant --version`
Sitten loin kansion vagrantilla `mkdir uusivagrant` ja siirryin kansioon `cd uusivagrant`

<img width="339" height="173" alt="image" src="https://github.com/user-attachments/assets/0b8e1828-3a75-4589-9cfd-3b72e3b37ac7" />

Tämän jälkeen oli taas aika luoda tiedosto samallailla kuin edellisessä tehtävässä "H3 Soitto kotiin `vagrant init debian/bookworm64` ja laitoin Vagrantin päälle eli komennolla `vagrant up` 
Aikaa käynnistyksessä ei kulunut kun muutama sekuntti

Kun vagrant oli käynnistinyt, tein salt minionin ja masterin Teron valmiin vagrant tiedoston ohjeiden avulla notepadiin: https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-filehttps://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file

Tässä kesti taas hetken aikaa kun virtuaalikoneet avautuivat

Sitten oli aika taas siirtyä tmaster käyttäjälle `vagrant ssh tmaster`
Tämän jälkeen installoin curlin `sudo apt install curl`
Ja tein kansion avaimille `mkdir -p /etc/apt/keyrings`
Latasin myös tietenkin avaimet:

`curl -fsSL https://packages.broadcom.com/artifactory/api/security/keypair/SaltProjectKey/public | sudo tee /etc/apt/keyrings/salt-archive-keyring.pgp`
`curl -fsSL https://github.com/saltstack/salt-install-guide/releases/latest/download/salt.sources | sudo tee /etc/apt/sources.list.d/salt.sources`

Sitten päivitin vielä sudon jotta avaimet latautuvat `sudo apt update`
Ja latasin saltmasterin: `sudo apt-get -y install salt-master`
Varmistin vielä että masteri löytää itsensä `sudo systemctl status salt-master.service`

<img width="762" height="530" alt="image" src="https://github.com/user-attachments/assets/5281b011-0614-431d-804b-5d85a7b3210a" />
Löytyi!

Otin myös ip- osoitteen talteen jotta voin antaa masterin osoitteen minionille:

<img width="542" height="42" alt="image" src="https://github.com/user-attachments/assets/67e2b1ec-66fe-4d04-b9b3-7c55cad5156c" />

Seuraavaksi tein viellä samat asiat t001 käyttäjälle ja asensin sinne salt-minionin

`vagrant ssh t001`
`sudo apt install curl`
`mkdir -p /etc/apt/keyrings`

Latasin avaimet

`sudo apt update`
`sudo apt-get install -y salt-minion`

Seuraavaksi muokkasin nanolla minionin tiedostoa ja annoin sinne masterin ip osoitteen

`sudoedit /etc/salt/minion`

<img width="196" height="57" alt="image" src="https://github.com/user-attachments/assets/c2efcafd-90f9-465b-91db-bb00d9c27550" />

Sitten restarttasin minionin `sudo systemctl restart salt-minion`
Ja varmistin että se oli päällä `sudo systemctl status salt-minion`

<img width="775" height="270" alt="image" src="https://github.com/user-attachments/assets/8cfc6248-cb00-473a-8917-86ce38ef516b" />

Sitten lisäsin portti22 kuuntelemaan masterille `sudo nano /etc/ssh/sshd_config`

<img width="97" height="62" alt="image" src="https://github.com/user-attachments/assets/6857deba-8b5e-44a4-a36e-2c74c2b830f0" />

Sitten oli aika siirtyä kokeilemaan toimiiko, ensin piti vielä hyväksyä avaimet että minioniin saa yhteyden
`sudo salt-key -L` ja `sudo salt-key -A`

<img width="409" height="227" alt="image" src="https://github.com/user-attachments/assets/7f3f09cb-faa3-4581-9abf-bad7f3e7e654" />

Sitten aloin tekemään init.sls tiedostoa masterille. Tein srv ja salt hakemiston `sudo mkdir -p /srv/salt/ssh`
Ja siirryin hakemistoon `cd /srv/salt/ssh`
Ja menin muokkaamaan init.sls tiedostoa josta löysin tarvittavat Teron sivuilta: https://terokarvinen.com/2018/04/03/pkg-file-service-control-daemons-with-salt-change-ssh-server-port/?fromSearch=karvinen%20salt%20ssh#:~:text=%24%20cat%20/srv/salt/sshd.sls%0Aopenssh%2Dserver%3A%0A%20pkg.installed%0A/etc/ssh/sshd_config%3A%0A%20file.managed%3A%0A%20%20%20%2D%20source%3A%20salt%3A//sshd_config%0Asshd%3A%0A%20service.running%3A%0A%20%20%20%2D%20watch%3A%0A%20%20%20%20%20%2D%20file%3A%20/etc/ssh/sshd_config

<img width="357" height="236" alt="image" src="https://github.com/user-attachments/assets/dc82b2ad-54c4-4217-8c17-80bc7dc14833" />

<img width="765" height="549" alt="image" src="https://github.com/user-attachments/assets/5eeeea7e-3e1f-4e97-b9a9-e2c6a03e75ce" />

Tuloste näytti kuitenkin virheilmoitusta, huomasin että tiedostoon oli jäänyt ylimääräinen välilyönti joten korjasin sen ja kokeilin uudelleen

<img width="991" height="1136" alt="image" src="https://github.com/user-attachments/assets/71bfe79b-f9ce-4bc3-a069-92bad11a7d74" />

Sain onnistuneet ilmoitukset!

Näiden jälkeen kokeilin vielä yhteydet komennolla `nc -vz 192.168.12.100 1234` ja `nc -vz 192.168.12.100 22` nämä antoivat onnistuneet yhteydet!

<img width="852" height="122" alt="image" src="https://github.com/user-attachments/assets/ce5b50e7-dbac-4db2-b8ae-7d09f435c98b" />

Tehtäviin kului noin 3 tuntia ja menojen takia minulla ei löytynyt aikaa vapaaehtoisille tehtäville.

## Lähteet

Palvelinten hallinta: https://terokarvinen.com/palvelinten-hallinta/

Karvinen 2018: https://terokarvinen.com/2018/04/03/pkg-file-service-control-daemons-with-salt-change-ssh-server-port/?fromSearch=karvinen%20salt%20ssh

Salt Vagrant: https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file:~:text=Vagrantfile%20in%20place.-,Ready%20made%20Vagrantfile%20for%20three%20computers,end,-Run%20Three%20Computers

Pkg file service: https://terokarvinen.com/2018/04/03/pkg-file-service-control-daemons-with-salt-change-ssh-server-port/?fromSearch=karvinen%20salt%20ssh#:~:text=%24%20cat%20/srv/salt/sshd.sls%0Aopenssh%2Dserver%3A%0A%20pkg.installed%0A/etc/ssh/sshd_config%3A%0A%20file.managed%3A%0A%20%20%20%2D%20source%3A%20salt%3A//sshd_config%0Asshd%3A%0A%20service.running%3A%0A%20%20%20%2D%20watch%3A%0A%20%20%20%20%20%2D%20file%3A%20/etc/ssh/sshd_config
