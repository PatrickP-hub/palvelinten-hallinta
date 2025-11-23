# H5 Toimiva versio
## Oma ympäristö

Aloitin harjoituksen Sunnuntaina klo 13 aikoihin kotiympäristössä pöytäkoneellani

- Pöytäkone (Windows 11, 16GB RAM, AMD Ryzen 2600 6-ydin, 256GB SSD)

## x) Lue ja tiivistä

### Chacon and Straub 2014: https://git-scm.com/book/en/v2 ja https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F

- Tässä kirjassa kerrotaan Gitin käytöstä, komennoista, protokollista ja monista Git: in ominaisuuksista
- Getting started osiossa kerrotaan esimerkiksi että, tiedostot kulkevat tilojen modified, staged ja committed läpi
- Gitissä lähes kaikki toiminnot toimivat paikallisesti mikä eroaa muista versionhallintajärjestelmistä

### Gitin käyttö on lähinnä 'git add . && git commit; git pull && git push'. https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository ja https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes

- `Git add` tarkoittaa lyhyesti että tiedosto merkitään "staged" tilaan, eli tiedosto valmistellaan seuraavaan commit snapshottiin sellaisena kun se on lisäyshetkellä
  
- `Git commit` taas tallentaa tiedoston tekevät muutokset Git-historiaan
  
- `Git pull` hakee etärepositorion uudet commitit ja yhdistää ne automaattisesti paikalliseen haaraan
  
- `Git push` lähettää paikalliset commitit etärepositorioon ja päivittää paikalliseen haaraan

### Varaston [terokarvinen/suolax/](https://github.com/terokarvinen/suolax/) historia, eli loki ja muutokset. 

<img width="240" height="143" alt="image" src="https://github.com/user-attachments/assets/f03e34e6-fbbe-449e-b810-aa2f5b1569d1" />

- Teron tekemässä varastossa kävin katsomassa commits historiaa ja muutoksia 
- Huomasin että muutoksia oli tehty useampi Huhtikuun 10 päivä 2024. Siellä oli esimerkiksi tehty README.md tiedostoja, kommentteja miten ajetaan erilaisia komentoja ja mistä löytyy apua esimerkiksi saltin käyttöön

## a) Online. Tee uusi varasto GitHubiin

Aloitin tehtävän avaamalla Githubin ja tein uuden varaston

- Add new repository
- Repository name: "Uusivarasto"
- Description: snow
- Visibility : Public
- add README : kyllä
- add lisence: GNU 3.0 

<img width="807" height="766" alt="image" src="https://github.com/user-attachments/assets/6fc99ef1-e83e-4eb7-98d6-fc6468f8ecc3" />


## b) Dolly. Kloonaa edellisessä kohdassa tehty uusi varasto itsellesi

Aloitin eka komennoilla jotka otin talteen viime tunnilta käytyjen komennon avulla:

`sudo apt update`

`sudo apt-get install git` lataa gitin

Seuraavaksi kirjauduin virtuaalikoneella githubbiin , jotta voin hakea ssh avaimen sieltä kloonaamista varten 
Sitten kloonasin oman uuden varaston 

`git clone oman varaston URL`

<img width="884" height="157" alt="image" src="https://github.com/user-attachments/assets/abbec06f-acde-4e97-8a9d-26a7c63d7c3c" />

Sitten oli aika etsiä ssh avain gittiä varten komennolla 

`ssh-keygen`

Enteriä kolme kertaa että avain tallentaa sen oikeaan paikkaan
Sitten komennot 

`cd .ssh/` siirryin ssh kansioon mistä avain löytyyy

`cat id_ed25519.pub` #pub tärkeä sillä se on se julkinen avain


<img width="739" height="72" alt="image" src="https://github.com/user-attachments/assets/2f61d077-1c8c-417f-bce4-04b25980361d" />

Sitten tarkistin `cat` komennolla public avaimen osoitteen
Ja vein ssh public keyn tiedot Githubiin

<img width="691" height="245" alt="image" src="https://github.com/user-attachments/assets/788b93a6-3857-497a-aeae-6c7ec4847d22" />

Sitten siirryin uuteenvarastoon

`cd Uusivarasto`

Ja kokelin tehdä muutoksen 

`micro README.md`

<img width="421" height="75" alt="image" src="https://github.com/user-attachments/assets/50173116-dfcb-46b8-a55e-a14d738d99c3" />

Tein muutokset tallensin ja poistuin editorista
Ja sitten oli aika antaa git komennot

`git add .`

`git commit`

`git pull`

`git push`

Huomasin että git push komennon kohdalla se kysyi käyttäjätunnusta ja salasanaa joten tajusin etten ollut liittänyt SSH URL osoitetta vielä virtuaalikoneeseeni joten tein sen seuravaaksi

`git clone SSH URL`

<img width="979" height="45" alt="image" src="https://github.com/user-attachments/assets/ac1a81ca-5146-4abc-95b1-14ec24e8a487" />

ja sitten uudelleen komento 

`git push`

<img width="617" height="197" alt="image" src="https://github.com/user-attachments/assets/7ec99434-d792-455e-8777-1419a259b63a" />

<img width="649" height="204" alt="image" src="https://github.com/user-attachments/assets/9219b65f-2d0b-4472-be54-8a661a13bfb8" />

Ja sehän onnistui!

## c) Doh! Tee tyhmä muutos gittiin, älä tee commit:tia. Tuhoa huonot muutokset ‘git reset --hard’.

Tein uuden tiedoston 

`micro init.sls`

annoin nämä tiedot 

<img width="205" height="54" alt="image" src="https://github.com/user-attachments/assets/1d87f847-0bb2-4173-b0c7-f3eb137cba0a" />

Sitten katsoin lisäsin init.sls tiedoston mutta en committannu sitä vaan katsoin sen statuksen

`git add`

`git status`

<img width="552" height="180" alt="image" src="https://github.com/user-attachments/assets/68c3dddc-75c2-4819-81dc-7765437230e6" />

Kuten kuvasta näkyy tiedosto on siellä mutta se vaatii committaamista
Sitten tuhotaan muutokset ja katsotaan uudelleen

`git reset --hard`

`git status`

<img width="594" height="154" alt="image" src="https://github.com/user-attachments/assets/b8061e31-acd9-4907-9e22-4b0fd945db84" />

"nothing to commit, working tree clean" eli komento toimi eikä committavaa enään ole :-)

## d) Tukki. Tarkastele ja selitä varastosi lokia

Annoin komennon jolla pääsin katsomaan tekemiäni muutoksia 

`git log --patch`

<img width="904" height="687" alt="image" src="https://github.com/user-attachments/assets/04a59590-e210-4514-b135-91f68952caf7" />

Sieltähän tuli esiin tekemiäni muutoksia
Esimerkiksi muutoksia ja muutoksia pt2 kohdissa näkyy kuka on tehnyt muutoksia, koska ja mitä ollaan lisätty 
Vihreellä värillä näkyy alempana esimerkiksi teksti mikä lisättiin README.md tiedostoon

Sitten kun rullasin vielä alemmaksi sain esiin GNU public lisenssin tiedot

<img width="524" height="293" alt="image" src="https://github.com/user-attachments/assets/beadcb56-da56-4ba4-be95-854ae2c85ec3" />

## e) Suolattu rakki. Aja Salt-tiloja omasta varastostasi. Käyttäen Teron vinkkejä https://github.com/terokarvinen/suolax

Tein eka kansion salt tiedostoille

`mkdir -p /srv/salt/kansio` & `mkdir -p /srv/salt/kansio1`

Ja sitten tiedostot saltille jotka löysin Teron valmiista srv/salt kansiosta omiin kansioihin 

`sudo nano /srv/salt/kansio/init.sls`  & `sudo nano /srv/salt/kansio1/init.sls`

<img width="281" height="74" alt="image" src="https://github.com/user-attachments/assets/1845d403-8e84-4f77-808f-620b18eb542d" />

ja 

<img width="175" height="71" alt="image" src="https://github.com/user-attachments/assets/ee4880fb-3ac3-4130-a58d-a758c56a761e" />

Sitten tein vielä top.sls tiedoston

`sudo nano /srv/salt/top.sls`

<img width="185" height="124" alt="image" src="https://github.com/user-attachments/assets/2da86ef0-e82b-42b1-b5e7-ddc1e633e12d" />

Oli aika ajaa masterilla komento

`sudo salt-call --local state.apply`

<img width="922" height="753" alt="image" src="https://github.com/user-attachments/assets/19b4edc3-44f3-403f-88d3-e9f8286e9dce" />

Jes sehän toimi ja sit vielä uudelleen että saadaan idempotenssi

<img width="918" height="555" alt="image" src="https://github.com/user-attachments/assets/7d274483-d5ff-495e-9af6-1821ab56f3a6" />

Lopuksi annoin vielä samat git komennot ja katsoin tuliko ne githubiin näkyviin

`git add .`

`git commit`

`git pull`

`git push`

<img width="651" height="225" alt="image" src="https://github.com/user-attachments/assets/82ef73f1-2769-4eb8-ace9-09d11a45e03f" />

Boom siellähän ne!


## Lähteet

Palvelinten hallinta kurssi: https://terokarvinen.com/palvelinten-hallinta/

Git - Book: https://git-scm.com/book/en/v2

Git - Getting started: https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F

Git basics - Recording with basics: https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository

Git basics - Working with remotes: https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes

Tero Karvinen varasto: [terokarvinen/suolax/](https://github.com/terokarvinen/suolax/)

Tero Karvinen commit: https://github.com/terokarvinen/suolax/commit/45c80a7016bb7e7a541098580272ef8ac0904f46
