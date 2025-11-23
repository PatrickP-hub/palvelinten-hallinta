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

<img width="707" height="61" alt="image" src="https://github.com/user-attachments/assets/e5e18ce7-e633-4292-a227-3d8c605c521d" />

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



## c) Doh! Tee tyhmä muutos gittiin, älä tee commit:tia. Tuhoa huonot muutokset ‘git reset --hard’.

## d) Tukki. Tarkastele ja selitä varastosi lokia

## e) Suolattu rakki. Aja Salt-tiloja omasta varastostasi.


## Lähteet

Palvelinten hallinta kurssi: https://terokarvinen.com/palvelinten-hallinta/

Git - Book: https://git-scm.com/book/en/v2

Git - Getting started: https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F

Git basics - Recording with basics: https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository

Git basics - Working with remotes: https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes

Tero Karvinen varasto: [terokarvinen/suolax/](https://github.com/terokarvinen/suolax/)

Tero Karvinen commit: https://github.com/terokarvinen/suolax/commit/45c80a7016bb7e7a541098580272ef8ac0904f46
