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
Aluksi tein kansion `mkdir vagrantti`
Siirryin kansioon `cd vagrantti`
Ja loin tiedoston `vagrant init debian/bookworm64`

<img width="366" height="60" alt="image" src="https://github.com/user-attachments/assets/786f465c-dd60-4ba4-99d6-e6e71263d410" />

Tämän jälkeen käynnistin Vagrantin komennolla vagrant up

<img width="928" height="217" alt="image" src="https://github.com/user-attachments/assets/2549a7ac-892f-4900-a2c9-8522348649cb" />

Kuten kuvasta näkyy tähän kului noin aikaa 4 minuuttia
Sitten kun lataus valmistui VirtualBox:iin ilmestyi uusi virtuaalikone

<img width="602" height="180" alt="image" src="https://github.com/user-attachments/assets/7f4f5c51-9428-42bd-8471-e1ca7ff4f00b" />

Seuraavaksi muodistin ssh yhteyden virtuaalikoneeseen komennolla `vagrant ssh`

<img width="813" height="175" alt="image" src="https://github.com/user-attachments/assets/412b441a-8902-441d-a436-725985949ecb" />

Kokeilin vielä komennoilla että vagrant löysi itsensä `whoami` ja sitten poistuin siitä `exit` komennolla

<img width="249" height="80" alt="image" src="https://github.com/user-attachments/assets/76cac6a2-0573-42fe-9fce-a5e22a124a26" />

Sitten vielä tuhosin vagrantin `vagrant destroy` komennolla + y 

<img width="656" height="82" alt="image" src="https://github.com/user-attachments/assets/f3e484e6-8b1b-484d-8067-a1c09db019e1" />

## c) Kaksin kaunihimpi

Aloitin tehtävän tekemällä uuden kansion `mkdir kaksin-kaunihimpi`ja siirryin kansioon `cd`komennolla
Sitten loin taas tiedoston `vagrant init debian/bookworm64`

<img width="596" height="219" alt="image" src="https://github.com/user-attachments/assets/8eb3496d-596c-45b1-9358-c92c208cd7d8" />

Kun olin tehnyt tiedoston otin yhteyden virtuaalikoneeseen `vagrant up` komennolla, tämä kesti taas muutaman minuutin käynnistyä

Muokkasin nanosta tiedostoa ja annoin Teron ohjeiden mukaan nämä tiedot tältä sivulta: https://terokarvinen.com/2021/two-machine-virtual-network-with-debian-11-bullseye-and-vagrant/ 

Eli avasin notepadin `notepad C:\Users\palmr\kaksin-kaunihimpi\Vagrantfile`

<img width="759" height="674" alt="image" src="https://github.com/user-attachments/assets/1d94126f-23ee-4ad0-8aa8-ac0cb0cae6a7" />

Muokkasin vain kohtaa bullseye -> bookworm että tämä toimii windowsilla 

<img width="500" height="618" alt="image" src="https://github.com/user-attachments/assets/02f62657-fd5c-4d70-9beb-ae9b1dc9168b" />

Tallensin notepadin
Sitten käynnistin uudet koneet `vagrant up` Tähän meni hetki aikaa kun koneet käynnistyivät VirtualBoxissa.
Kun koneet olivat käynnissä kirjauduin komennolla `vagrant ssh t001` sekä `vagrant ssh t002` Kun molempiin pääsin onnistuneesti oli aika poistua `exit` komennolla 

<img width="777" height="268" alt="image" src="https://github.com/user-attachments/assets/3a5c7d8b-d0ea-4b58-b3c4-e6575dd23f19" />

Testasin vielä pingata toisella koneella ja katsoin toimiko tämä `ping -c 1 192.168.88.101` ja sehän toimi!

<img width="549" height="129" alt="image" src="https://github.com/user-attachments/assets/23f6ce87-5358-4051-a165-9ee8f87d7e51" />

Ja tämän jälkeen poistin virtuaalikoneet ja pääsin aloittamaan taas puhtaalta pöydältä :)

## d) Herra-orja verkossa 

Aloitin tekemällä kansion "herraorja" ja siirryin sinne `cd`komennolla, sekä tein `vagrant init` komennolla tiedoston
Seuraavaksi tein taas notepadiin muokkaukset teron sivujen antamilla ohjeilla https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file

<img width="631" height="25" alt="image" src="https://github.com/user-attachments/assets/ac12eae6-48e6-4cd6-a09c-b69e2ef3f2cc" />

Vaihdoin osiosta taas "bullseye" -> "bookworm" ja tallensin notepadin ja sitten käynnistin vagrantin `vagrant up`

<img width="506" height="802" alt="image" src="https://github.com/user-attachments/assets/444e3ffe-cc51-44cc-9dce-0aeb5a131fdb" />

Käynnistämiseen meni taas jotakuinkin 3minuuttia.

<img width="366" height="172" alt="image" src="https://github.com/user-attachments/assets/ac4e4b2c-8ad3-437e-bff5-94a09e10bae2" />

Sitten oli aika siirtyä tmaster käyttäjälle `vagrant ssh tmaster` komennolla ja sitten installoin curl:in `sudo apt install curl`
Tämän jälkeen tein avaimille kansion `mkdir -p /etc/apt/keyrings` sekä latasin avaimet: 
`curl -fsSL https://packages.broadcom.com/artifactory/api/security/keypair/SaltProjectKey/public | sudo tee /etc/apt/keyrings/salt-archive-keyring.pgp` ja `curl -fsSL https://github.com/saltstack/salt-install-guide/releases/latest/download/salt.sources | sudo tee /etc/apt/sources.list.d/salt.sources
`
Sitten jokaisen sudo muutoksen jälkeen päivitin `sudo apt update` ja latasin salt-masterin `sudo apt-get -y install salt-master`
Tehtävän annossa oli tärkeää pistää masterin ip muistiin joten katsoin sen `hostname -I` komennolla ja pistin muistiin

<img width="518" height="36" alt="image" src="https://github.com/user-attachments/assets/8ffa3fcd-5a23-461d-9447-4b07bf095574" />

Sitten siirryin tekemään salt-minionia `vagrant ssh t001` komennolla ja asensin samoilla komennoilla curlit ja avaimet.
Latasin salt-minionin `sudo apt-get install -y salt-minion` ja menin muokkaamaan `sudoedit /etc/salt/minion` antamalla masterin osoitteen sekä ID:n minionille

<img width="178" height="63" alt="image" src="https://github.com/user-attachments/assets/18f54de6-0127-44ee-a794-99f00bbec304" />

Ctrl X + y ja tiedosto oli tallennettu
Lopuksi vielä annoin komennot `sudo apt update` ja `sudo systemctl restart salt-minion.service` mutta se ei näyttänyt toimivan joten annoin `stop` ja `start`

Sitten oli aika siirtyä takaisin masterille ja siellä katsoin komennolla `sudo salt-key -L` avaimet ja hyväksyin kaikki avaimet `sudo salt-key -A` 








## e) Kokeile vähintään kahta tilaa verkon yli

## Lähteet

Palvelinten hallinta https://terokarvinen.com/palvelinten-hallinta/

Karvinen 2021: https://terokarvinen.com/2021/two-machine-virtual-network-with-debian-11-bullseye-and-vagrant/

Karvinen 2018: https://terokarvinen.com/2018/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/?fromSearch=salt%20quickstart%20salt%20stack%20master%20and%20slave%20on%20ubuntu%20linux

Karvinen 2023: https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file

Install Vagrant https://developer.hashicorp.com/vagrant/docs/installation

