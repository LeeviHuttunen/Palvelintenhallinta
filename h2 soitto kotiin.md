# Soitto kotiin
x) Luodakseen kaksi virtuaalikonetta samaan verkkoon Vagrantilla, pitää ensiksi olla vagrant asennettuna komennolla "sudo apt-get install vagrant virtualbox"
Seuraavaksi kyseisessä tehtävässä kannattaa tehdä uusi directory komennolla "mkdir twohost". Kahden virtuaalikoneen asennuksesta ja testaamisesta alempana.

Saltilla voi hallita useita eri tietokoneita. Saltin asennettua koneille voi asentaa mastereita ja slaveja. Master kone siis antaa käskyjä "orjatietokoneille", jotka tekevät,
mitä master käskee tehdä


## Klo 17:30-19:45
a) Ensimmäisessä tehtävässä tarkoitus on asentaa kaksi virtuaalikonetta samaan verkkoon. Aivan ensiksi tein kuitenkin uuden hakemiston kyseiseen tehtävään ja siirryin hakemistoon.

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/9ef7f24b-694c-4bc6-b166-64edd68429ab)

Yritin ensimmäiset 2 tuntia tallentaa scriptiä kyseiseen vagranttiedostoon, mutta jostain syystä komento ei toiminut. Sain komennon kirjoitettua, mutta mitään ei tapahtunut.
Yritin itsenäisesti selvittää, miksi mitään ei tapahdu, mutta en saanut asiaa selville.

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/36b40184-3cb8-41cf-9428-35722033f833)


![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/74bcd24f-3101-4287-80d5-d43d2ede7caf)


Yritän selvittää ensi oppitunnilla opettajan avustuksella, mikä meni vikaan ja kirjoitan sitten miten ongelma ratkaistiin. Käsitykseni mukaan scripti pitäisi kirjoittaa
oman tietokoneen nano-tekstieditoriin, mutta powershellissä ei toimi nano. Tallensin scriptin oman virtuaalikoneen nanoon, sekä omalle koneelle visual studioon.

## Klo 19:45-20:32
b)  Asensin masterin koneelleni komennolla:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/21fa8e1e-f6db-42d8-ae83-92121f73c7be)

Asensin slaven toiselle koneelleni, oli ilmeisesti jo asennettu aikaisemmin jo:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/ea9db130-f8ae-4ee3-b221-fddaf6bb6e9a)

Seuraavissa kohdissa en voinut tehdä kyseisiä tehtäviä fyysisesti, koska en saanut virtuaalikoneita samaan verkkoon. Teen kuitenkin nämä myös omilla virtuaalikoneillani
myöhemmin, kunhan saan yhdistettyä koneet samaan verkkoon. 

c) Ajoin shell komennon, mutta koneita ei oltu yhdistetty, joten sain seuraavan ilmoituksen:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/742175d7-97a6-4ad5-8cce-30dc1cd454df)

Oletan kuitenkin, että komento oli oikea.  

d) Seuraavaksi piti ajaa idempotentteja, tein tämänkin vaikka koneiden välillä ei ollut yhteyttä: 

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/58559728-5ab5-463f-98ca-e3a9959a05c6)

Virhettä kuitenkin pukkasi. Sama kohtalo myös muiden idempotenttien kanssa.

e) Seuraavaksi oli tarkoitus kerätä tietooja orjista verkon yli. Tämä onnistuisi komennolla  sudo salt '*' grains.items  $ sudo salt '*' grains.item virtual

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/21dda024-2eb6-4b4a-851b-0d04d925fd5e)

Mutta minioneita ei löydetty :(

## klo 21:02-21:25

f) Seuraavassa ja viimeisessä kohdassa on tarkoitus tehdä infraa koodina. Ensimmäisenä asensin micro-editorin:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/6e78daf9-3b9c-49d9-9999-043c49c95478)

Kun editori oli asennettu, tein uuden kansion "hello" ja menin kyseiseen kansioon. 

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/c50599b7-be2a-44f8-9f24-a359bab2d157)

Seuraavalla komennolla avasin micro-editorin:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/e7120cc1-6ae6-44dc-b995-3f00e0fd0581)

Laitoin sinne sitten koodia, mikä näkyikin Teron sivuilla esimerkissä:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/fe254cd7-362f-4d99-b318-507fe5335f7d)

Tallensin sitten vielä kyseisen tiedoston ja suljin micron. Nyt on uusi tiedosto tehty:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/a3ad04fd-b99a-4016-b0fa-9bc668ad73d8)

Ja näin idempotenssi pyörii: 

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/21a32b73-180f-46f1-aff3-7c7cf6936a1c)

Tämän tehtävän tekeminen oli hieman turhauttavaa yllämainittujen ongelmien vuoksi. Varsinkin kun kyseisiä ongelmia en kyenneyt ratkaisemaan itsenäisesti. 
Sain kuitenkin suurimman osan tehtyä ja teen loputkin, kunhan saan ratkaistua nettiyhteyden koneiden välille. 

# Edit

## Seuraava päivä maanantai 8.4. klo 12-17:56

Seuravana päivänä palasin heti tehtävän pariin. Poistin kaikki virtuaalikoneet ja asensin uuden jälleen tilalle. 
Jostain tuntemattomasta syystä, vagrant lähti tällä kertaa toimimaan odotetusti. Oletan, että kansioni oli jossain "oudossa" paikassa, tai jotain muuta vastaavaa. Tallensin scriptin oman koneeni Vagrantkansioon ja tällä kertaa Vagrant löysi koneet t001 ja t002. 

Tässä vielä kuva errorista, ennen virtuaalikoneiden poistoa:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/57c20d97-f1cc-496d-a053-532ecce4b93a)

Ja tässä kuva, kun poistin virtuaalikoneet, asensin uuden ja tein tarvittavat toimenpiteet:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/8b608cab-1831-45fd-9686-6a2bc2c1dd74)

Ja näin pääsin vihdoin t001 koneelle ja koitin pingata sitä samalla:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/7af89b82-997a-4299-8a1c-bc7ad9e28a90)

Ja myös kone t002 toimi myös:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/53343840-4037-40f4-ae5f-a1b3abbdb968)

## Master ja slave-roolien asetus
Sitten pääsin tekemään käytännössä niitä asioita, mitä eilen en päässyt tekemään. Ensimmäisenä tehtävänä oli asettaa toiselle koneelle master-rooli ja toiselle slave-rooli. Asensin koneeseen t001 master roolin komennolla:
  sudo apt-get -y install salt-master
  Ja slaven komennolla:  sudo apt-get -y install salt-minion
Ja sitten vielä tarkistin, että asennukset onnistuivat:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/10a48ad6-9172-4930-8adb-055bce6cca61)

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/cf852759-8abe-448e-b362-54cd40f21887)

Seuraavaksi piti kertoa slave-koneelle, mistä osoitteesta Master löytyy. Se tapahtui Slave-koneelta komennolla:
  sudoedit /etc/salt/minion

  ![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/f7b8dc17-9eab-41a0-9be1-9968b11b66e4)

Sitten restartattiin molemmat koneet uudelleen. Nyt minionin pitäisi tietää, missä master on.

Seuraavaksi koitin hyväksyä minionkoneen lähettämän avaimen master-koneella, mutta minion ei ollut lähettänyt avainta:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/939bcb66-5f3b-44b1-8fcc-920bb3416fe2)

Ongelmana on, että master kone ei ole siinä osoitteessa, missä pitäisi:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/98eb6fdf-fa5a-4745-8812-2b2bda9b8cf4)

Joten vaihdoin minioniin masterin oikean ip-osoitteen:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/282600d0-3b09-4a04-b5fd-fbec51e9c553)

Tallensin aluksi id:n nimelle tero, mutta vaihdoin sen myöhemmin nimeksi Leevi, koska kone 1 ei saanut avainta koneelta 2. Koneella 1 luki kuitenkin, että hyväksykö Teron avaimen:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/9084bf51-c69b-41b9-abbe-30700e7dea7c)

Hyväksyin avaimen, mutta erroria pukkasi, voi olla että tämä johtui nimenmuutoksesta?

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/4f27293c-6265-4b0d-840e-39697dbe5184)

Kirjauduin uudelleen koneelle 1, jolloin tuli avain Leeviltä:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/50f7e8f4-344e-451b-be06-6243dc0bdbde)

Mutta testissä pukkasi jälleen erroria:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/19305b46-faaf-43dd-9793-b833e98ea300)

Käynnistin molemmat koneet uudelleen pariin otteeseen, jonka jälkeen leevi minion alkoi vihdoin toimia. Taisi mennä noin 10 minuuttia kunnes alkoi toimimaan:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/dad64600-f7d4-4822-b545-1120d6da6a08)

## d)  Seuraavaksi loin moduulin "hello" ja menin kyseiseen moduuliin:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/602c851f-3597-48b7-aa0f-9571001864ee)

Ja tein vielä idempotentin, jossa loin tyhjän kansion:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/cfde095a-7d17-4db9-b500-2094680edfab)

## e) Keräsin tietoa orjista komennolla  sudo salt '*' grains.items
Tässä joitain tietoja orjista:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/772bf5d8-e69d-4365-8421-7acc1697a46c)

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/aa2cc79b-fc8f-4249-848c-c55a3b38520c)

Ja lopussa taas tero-minion ei suostunut vastaamaan:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/1ce0a980-2a1b-4451-a639-f83c20148859)

Pitää selvittää, miten kyseisen virheilmoituksen saa pois.

## f)

Viimeisenä piti tehdä infraa koodina. Ensiki laitoin komennon  /srv/salt/hello/init.sls. Tämän moodulin tein siis jo aikaisemmin tehtävässä d. Tässä vaiheessa loppui ymmärrys. En saanut jostain syystä ladattua micro-tekstieditoria 1 koneelle, joten viimeinen tehtävä ei onnistunut ohjeiden mukaan. 




# Lähteet

terokarvinen.com
https://terokarvinen.com/2024/configuration-management-2024-spring/#laksyt
https://terokarvinen.com/2018/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/?fromSearch=salt%20quickstart%20salt%20stack%20master%20and%20slave%20on%20ubuntu%20linux
https://terokarvinen.com/2024/hello-salt-infra-as-code/


