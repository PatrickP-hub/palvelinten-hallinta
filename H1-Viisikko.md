# H1 Viisikko

## Lue ja tiivistä

### Install Salt on Debian 13 Trixie. https://terokarvinen.com/install-salt-on-debian-13-trixie/

- Salt on konfiguraatiohallintatyökalu, jonka avulla voi esimerkiksi hallita suurta määrää Windows ja Linux tietokoneita.
- Saltin avulla voi määritellä infrastruktuurin koodina.
- Apt repositorion lisäämisen jälkeen päivitykset tulevat automaattisesti.

### Run Salt Command Locally. https://terokarvinen.com/2021/salt-run-command-locally/

- Salt-komentoja voi suorittaa paikallisesti ja nähdä tulos heti.
- Windowsissa ja Linuxissa on samat komennot.
- Tärkeimmät toiminnot ovat: 'pkg', 'file', 'sevice', 'cmd' ja 'user'.
- Saltia käytetään hallitsemaan suurta määrää orjakoneita verkon yli.

### Salt Quickstart - Salt Stack Master and Slave on Ubuntu Linux. https://terokarvinen.com/2018/03/28/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/

- Saltin avulla voit hallita tuhansia tietokoneita.
- Orjakoneita voi hallita vaikka ne olisivat NATin, palomuurin takana tai tuntemattomassa osoitteessa.

### Raportin Kirjoittaminen. https://terokarvinen.com/2006/06/04/raportin-kirjoittaminen-4/

- Raportoi samalla kun teet tehtävää
- Viittaa lähteisiin, käytä väliotsikoita ja käytä mennyttä aikamuotoa
- Raportoi onnistuneet sekä epäonnistuneet tulokset

### a) Asenna Debian 13-Trixie
- Asensin debian-13.1.0-amd64-netinst.iso tiedoston ja seurasin Teron Install Debian on Virtualbox ohjetta: https://terokarvinen.com/2021/install-debian-on-virtualbox/. 
<img width="821" height="408" alt="image" src="https://github.com/user-attachments/assets/108a2be2-7336-4651-aee8-9f47bdb5469c" />
- Asennus sujui mutkattomasti.
  
### b) Asenna salt 
- Tässä käytin Salt asennus ohjeita sivustolta https://docs.saltproject.io/salt/install-guide/en/latest/topics/install-by-operating-system/linux-deb.html
- Aluksi varmistin että hakemisto on olemassa komennolla
  <img width="619" height="27" alt="image" src="https://github.com/user-attachments/assets/ea5f2b27-14b3-4604-b55d-9b0c0865d19c" />
- Sitten latasin julkisen avaimen komennolla
  <img width="798" height="69" alt="image" src="https://github.com/user-attachments/assets/f904357d-872d-4664-b697-f310f6b36c31" />
- Tämän jälkeen lisäsin apt-repositorion
  <img width="660" height="66" alt="image" src="https://github.com/user-attachments/assets/1965ab3f-70b8-412d-bbae-f4dbdd4fea58" />
  - Kun olin lisännyt repositorion päivitin paketti tiedot 'sudo apt update komennolla'
  <img width="658" height="243" alt="image" src="https://github.com/user-attachments/assets/df5f8f42-0777-4814-b4ca-de1aab3c9cad" />
- Päivitysten jälkeen valitsin salt-minion asennuksen
  <img width="639" height="21" alt="image" src="https://github.com/user-attachments/assets/0d080420-13a0-4eec-b9dc-415264757b51" />
  <img width="657" height="526" alt="image" src="https://github.com/user-attachments/assets/72746214-b15e-4fb2-b58c-2219558a0066" />
-  Tarkistin viellä että salt oli onnistuneesti lataantunut komennolla sudo systemctl status salt-minion
   <img width="658" height="328" alt="image" src="https://github.com/user-attachments/assets/6a59b275-096d-4f0f-96ba-35584641ed59" />
-  Terminaalissa näkyy "Active" running, joten tämä toimi
  
### c) Viisi tärkeintä Saltin tilafunktiota 
1 PKG
- Asensin komennolla 'sudo salt-call --local -l info state.single pkg.installed tree' paketin
<img width="713" height="530" alt="image" src="https://github.com/user-attachments/assets/34badc6f-8bb5-4401-a611-f83adf33f3b2" />
- Tulosteesta näkyi että paketti oli onnistuneesti asennettu
- Tietoja mitä tulosteessa myös näkyy on esimerkiksi: mitä asennettiin, mikä on latauksen lopputulos, kommentit mitä tapahtui, koska lataus aloitettiin ja kauan siinä kesti.
- Komennolla 'sudo salt-call --local -l info state.single pkg.removed tree' saa poistettua paketin
<img width="559" height="529" alt="image" src="https://github.com/user-attachments/assets/5fe8cbc5-a16f-4024-aae5-afc5272c661f" />
- Tuloksista voi huomata että lisänä tulosteissa on "tree new ja old" mikä kertoo paketin versionumeron ja sekä se että paketti poistettiin.
2. File
- Ajoin komennon sudo salt-call --local -l info state.single file.managed /tmp/filetehtävä
<img width="602" height="466" alt="image" src="https://github.com/user-attachments/assets/2bc55ff6-5251-4ff5-a267-0357825ebfc7" />
- Tämä komento teki tyhjän tiedoston nimellä "filetehtävä"
- Kuvasta voi myös huomata että tiedosto on tyhjä ja että se luotiin onnistuneesti
- Jotta pystyin muokkaamaan tiedostoa annoin komennon 'sudo salt-call --local -l info state.single file.managed /tmp/filetehtävä contents="uusi"'
<img width="493" height="528" alt="image" src="https://github.com/user-attachments/assets/7f8191ea-e03a-4342-bd8f-5cb689fb4171" />
- Tulosteeseen oli lisääntynyt tekstiä ja merkkejä diff: tulosteen perään. 
- Tämän jälkeen poistin myös tiedoston komennolla 'sudo salt-call --local -l info state.single file.absent /tmp/filetehtävä'
<img width="938" height="502" alt="image" src="https://github.com/user-attachments/assets/cdcb3b96-9ac8-4a46-bf39-51b1eb8096ca" />
- Kuten kuvasta näkyy tulosteessa näkyy "removed" /tmp/filetehtävä eli tiedosto oli poistettu onnistuneesti
3. Service
- Komennolla 'sudo salt-call --local -l info state.single service.running apache2 enable=True' sain näkyviin päällä olevan apache2 servicen
<img width="940" height="488" alt="image" src="https://github.com/user-attachments/assets/23121996-7cdf-43e4-a799-f1e33c4bbe26" />
- Kuten kuvasta näkyy ohjelmisto ei ole aktivoitu tai käynnissä, tähän pyysin apua tekoälyltä miten toimia vastaavassa tilanteessa.
- Annoin komennon 'sudo apt update' ja 'sudo apt install apache2' 
<img width="908" height="508" alt="image" src="https://github.com/user-attachments/assets/7f03c7ab-00f4-4fa6-b478-f8eaee0a19ba" />
- Tämän jälkeen kokeilin uudelleen sainko apache2 servicen toimimaan ja lopputulos oli onnistunut!
<img width="933" height="530" alt="image" src="https://github.com/user-attachments/assets/df315dcd-b669-4ff7-8db9-12d7583c6615" />
- Kuvasta huomaa siis että ohjelmisto on käynnissä ja siinä ei ole muita muutoksia.
- Seuraavaksi kokeilin apache2 ohjelmiston pysäyttämistä komennolla 'sudo salt-call --local -l info state.single service.dead apache2 enable=False'
<img width="916" height="527" alt="image" src="https://github.com/user-attachments/assets/d813dad4-9f40-480c-855d-229480c80f7c" />
- Tulosteessa lukee "apache2 has been disabled, and is dead" tarkoittaa siis se että apache2 ohjelmisto on pysäytetty ja se on "kuollut"
4. Cmd
- 'sudo salt-call --local -l info state.single cmd.run 'touch /tmp/uusi2' creates="/tmp/uusi2"' loin tyhjän tiedoston
<img width="612" height="529" alt="image" src="https://github.com/user-attachments/assets/0f287ed4-5fc6-4fcd-a5a0-42e533cc36d2" />
- Tulosteessa uudet kohdat "pid" tarkoittaa prosessin tunnistetta, "retcode" sitä että komento onnistui ja "stdout ja err" tarkoittavat ettei tulosteeseen tullut virheitä.
5. User
- Viimeisenä loin käyttäjän Saltin avulla
- Komennoksi annnoin 'sudo salt-call --local -l info state.single user.present pate123'
<img width="893" height="665" alt="image" src="https://github.com/user-attachments/assets/6a944008-635f-4e5f-8842-26dca0f5df71" />
- Tästä kuvasta voi päätellä että käyttäjä pate123 oli onnistuneesti luotu ja mihin käyttäjä on luotu
- Kokeilin vielä poistaa käyttäjän käyttämällä 'user.absent' komennolla ja pate123 käyttäjä oli poistettu
<img width="888" height="529" alt="image" src="https://github.com/user-attachments/assets/7a8615ed-f743-4303-bd53-930a24819749" />
- pate123 oli hävitetty onnistuneesti
  
### d) Idempotentti
- Tarkoittaa että useasti suoritetut komennot eivät tee muutosta ensimmäisen halutun muutoksen jälkeen
- Käytin tässä esimerkkinä äskösessä tehtävässä tekemääni käyttäjää pate123
<img width="303" height="166" alt="image" src="https://github.com/user-attachments/assets/8876792f-6958-4d65-880e-de1ce1eb04b0" />
- Kuvassa näkyy changed=1 eli komento suoritettiin ekaa kertaa ja kun annan saman komennon uudelleen ->
<img width="603" height="345" alt="image" src="https://github.com/user-attachments/assets/9ea5e5e7-37c4-48c2-b2d8-034dff34fbba" />
- Nyt kuvasta näkyy että "changed" tulostetta ei ole enään näkyvissä eli käyttäjä on jo tehty ja komento ei enään suorita sitä koska se on jo olemassa

 ### Kiitoksia ja seuraavaan kertaan
 
## Lähteet

Tero Karvinen 2025: Palvelinten Hallinta https://terokarvinen.com/palvelinten-hallinta/
Karvinen 2025: Install Salt on Debian 13 Trixie https://terokarvinen.com/install-salt-on-debian-13-trixie/
Karvinen 2023: Run Salt Command Locally https://terokarvinen.com/2021/salt-run-command-locally/
Karvinen 2018: Salt Quickstart - Salt Stack Master and Slave on Ubuntu Linux https://terokarvinen.com/2018/03/28/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/
Karvinen 2006: Raportin kirjoittaminen https://terokarvinen.com/2006/06/04/raportin-kirjoittaminen-4/
Karvinen 2024: Install Debian on Virtualbox https://terokarvinen.com/2021/install-debian-on-virtualbox/
Salt install guide https://docs.saltproject.io/salt/install-guide/en/latest/topics/install-by-operating-system/linux-deb.html

