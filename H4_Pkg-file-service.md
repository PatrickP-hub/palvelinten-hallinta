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





## Lähteet

Palvelinten hallinta: https://terokarvinen.com/palvelinten-hallinta/
Karvinen 2018: https://terokarvinen.com/2018/04/03/pkg-file-service-control-daemons-with-salt-change-ssh-server-port/?fromSearch=karvinen%20salt%20ssh
Salt Vagrant: https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file:~:text=Vagrantfile%20in%20place.-,Ready%20made%20Vagrantfile%20for%20three%20computers,end,-Run%20Three%20Computers

