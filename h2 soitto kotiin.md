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




