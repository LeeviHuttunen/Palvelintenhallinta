# Ensimmäinen kotitehtävä

## Ensimmäinen osio

x) Salt slavea asentaessa tarvittava komento on :"sudo apt-get -y install salt-minion". Nähdäkseen onnistuiko asennus, komennolla "sudo salt-call --version", näkee sen. 
Tein myös GitHubiin oman profiilin, jonne voin jatkossa laittaa eri kurssien töitä. Githubin käyttö vaikuttaa helpolta ja nopealta. 
Raportin kirjoittamisesta oli hyvät ohjeet. Harjoituksia on tärkeää tehdä aina raportin kanssa samaan aikaan, jotta kaiken tarvittavan saa ylös.

1.a) Saltin kanssa oli jonkun aikaa hankaluuksia, kunnes sain sen asennettua. Vaikka olin asentanut sen viimeksi, se piti silti jostain syystä asentaa uudestaan.
En saanut liitettyä tähän kuvaa, mutta komennolla "sudo salt-call --version", näin saltin olevan asennettu. Vastauksena Vagrant antoi "salt-call 3002.6".

1.b) Vagrantin näen toimivan, koska Powershellissä lukee Vagrant@bullseye: ~$. 

Seuraavissa tehtävissä en ole täysin varma, näkyykö kyseiset kuvat. 

## Toinen osio

2.b) Salt.pkg on paketti, jonka voi ladata omaan salt-systeemiinsä. Olemassa on lukuisia erilaisia paketteja mitä voi ladata. Niitä löytyy esimerkiksi nettisivulta:
https://docs.saltproject.io/en/latest/ref/states/all/salt.states.pkg.html.

<img width="318" alt="Näyttökuva 2024-03-31 194909" src="https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/a9c07340-9ec3-4c39-895a-7a684d384b38">

Filet ovat tiedostoja linuxissa. Filesta voi muokata tiedostoja. Tein uuden filen komennolla "sudo salt-call --local -l info state.single file.managed /tmp/hellotero"

<img width="827" alt="Näyttökuva 2024-03-31 205957" src="https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/a56535cc-1d4b-4e7a-aeb3-aa9dd9b364be">

Komento service.running käynnistää tai uudelleenkäynnistää esimerkiksi apache 2. Koitin tehdä asian komennolla "sudo salt-call --local -l info state.single service.running apache2 enable=True"
Ilmeisesti en ole kuitenkaan asentanut apachea vielä. Jostain syystä en voinut asentaa apachea. Seuraavassa kuva:
<img width="507" alt="image" src="https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/ea36425a-4746-4ca5-90fe-8d9f0333378d">

User on käyttäjä tilafunktio. Tein uuden käyttäjän nimeltä Leevi komennolla "sudo salt-call --local -l info state.single user.present Leevi" Käyttäjälle voi lisätä
myös salasanan, erilaisia ryhmiä käyttäjille ja niin edelleen. Ohessa vielä kuva:
<img width="239" alt="image" src="https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/0318a7be-2b48-4b49-9b8f-273e7e422fe8">

Cmd.run antaa erilaisia komentoja, millä voi automatisoida järjestelmää. Komennolla "sudo salt-call --local -l info state.single cmd.run 'touch /tmp/foo' creates="/tmp/foo"
tapahtui seuraavaa: 
<img width="309" alt="image" src="https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/daf8c88a-83ea-442d-8cdd-4a5ddf35c6d1">

Idempotenssi on automaatio, mikä suorittaa samant tuloksen joka kerta, jos se on tehty oikein. En nyt valitettavasti muistanut yhtäkään idempotentti komentoa

Laitoin komennon "sudo salt-call --local grains.items", jolloin sain koneen tiedot. 
Tässä kuvassa näkee, kuinka paljon muistia on:
<img width="91" alt="image" src="https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/d883c82f-8342-400e-bb0c-26d6b4b7393c">

Tässä näkee, että virtualbox on käytössä. 
<img width="121" alt="image" src="https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/f7cb64b3-4495-41c7-99de-5cbb6559a0dd">

Ja tässä näkee ip6-osoitteen
<img width="227" alt="image" src="https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/179dfc2b-b4fa-40f1-8543-c016b566e805">

Toivottavasti kaikki kuvat näkyvät :)

## Lähteet tehtäviin

https://saltproject.io/

https://terokarvinen.com/






