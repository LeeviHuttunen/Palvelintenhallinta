# X) Windows package manager
- Windows package managerin asentaminen saltilla helpottaa erilaisten sovellusten ja pakettien lataamista Windowsille. Uusia sovelluksia ja paketteja ei tarvitse enää hakea 
netistä, vaan niitä voidaan ladata muutamalla käskyllä. Aivan kuin Linuxilla. 
- Pitäisi ladata git-varasto Saltin sivuilta, jotta .sls tiedostoja voidaan käyttää.
- Seuraavaksi päivitetään database komennolla "salt-call --local pkg.refresh_db" Tämä siis paikallisesti, jos koneella ei ole herra-orja arkkitehtuuria.
- Sitten pitäisi tulla seuraavanlainen ilmoitus, että päivitys onnistui:

  ![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/27114151-fde7-4789-a3af-44f61a05f0c3)

- Sitten package managerin pitäisi toimia. Komennolla "salt-call --local pkg.install firefox_x64" voi ladata esimerkiksi firefoxin. 
- Komennolla "pkg.remove" voi poistaa paketin. Paikallisesti siis koko komento on vaikka Mozilla Firefoxin poistoon "salt-call --local pkg.remove firefox_x64".
- Komennolla "salt-call --local pkg.list_pkgs" salt tekee listan sovelluksista ja paketeista, jotka on asennettu.

# a)  Asenna Windowsiin tai Macciin ohjelmia Saltin pkg.installed -funktiolla.
Asensin package managerin jo tunnilla, mutta tässä lyhyt kertaus siitä, mitä tein:
Ensiksi latasin gir-repon seuraavalla komennolla: 
![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/2f88f0f9-0b1a-4964-b109-0ab0a06e9b0e)

Jonka jälkeen päivitin databasen:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/664d286b-8baa-4ab3-a874-6af57722c081)

Ja sitten vain asentamaan paketteja. Tässä lataan mozilla firefoxin:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/df9ec09e-1732-4fa1-ac71-6b6475e5897f)

Näin Mozilla on kätevästi ladattu yhdellä komennolla. Tunnilla huomasin, ettei kaikkia sovelluksia ja paketteja pysty lataamaan. Esimerkiksi Cowsayta ei pysty lataaamaan.
Mietin, voisiko se johtua tietokoneen virusturvasta?


# b) Benchmark. Etsi 3-7 keskitetyn hallinnan projektia, esimerkiksi tämän kurssin "Oma moduli" lopputyötä.

1. Ensimmäisenä silmiini osui Joonas H:n mielenkiintoinen projekti viime joulukuulta, jossa aikomuksena oli tulostaa eri paikkakuntien säätietoa Saltilla 30 minuutin välein.
Kyseisessä moduulissa oli GPL-3.0-lisenssi, joka siis tarkoittaa, että kyseistä työtä saa muokata ja jakaa. Tässä työssä käytettiin Vagrantin virtuaalikoneita.

Muutamia mielenkiintoisia pointteja oli, että kyseissä työssä käytettiin crontab-tiedoston muokkausta, jota me emme ole käyneet läpi. Tekijä myös vaihtoi lennosta aihetta,
kun säätiedotukset eivät tulostuneet hänen haluamallaan tavalla. Työ oli kokonaisuudessa hyvin tehty ja onglemia oli hienosti ratkaistu matkan varrella. 
Tässä vielä kyseinen moduuli :https://github.com/hautadata/palvelintenhallinta-jh-moduuli/blob/main/h7-moduuli.md

2. Seuraavaksi selasin läpi Liisa Lesosen miniprojektin. Aiheena oli rakentaa Lamp-stack, eli tässä moduulissa käytettiin Linuxia, Apachea, MariaDB:tä ja Pythonia.
Moduulissa koneena toimi Vagrant ja sen orjat. Tässä moduulissa ei ollut mitään lisenssiä. Työ oli tehty Joulukuussa 2023.

Liisan ei saanut työssään asennettua MariaDb:tä orjakoneille. Tuli mielenkiintoinen error, jossa luki, että Mariaa ei voi ladata orjakoneille 15 tuntiin. 
Muuten kaikki sujui niin kuin pitikin. Ohessa vielä linkki moduuliin: https://github.com/LiisaLesonen/palvelintenhallinta/blob/main/h7.md

3. Viimeisenä otin hieman vanhemman moduulin tutkittavaksi. Tommi Muhosen vuonna 2020 tehty miniprojekti käsitteli palomuurin asetuksia, asennettiin apache, curl ja git.
Määriteltiin myös ssh:n asetuksia.

Tämä moduuli tehtiin wordpress.comiin, joten lisenssejä ei ollut näkyvissä. Harjoitus tehtiin virtuaalikoneella. Harjoitus näytti sujuvan ilman suurempia ongelmia. 
Linkki projektiin: https://tommimuhonen334781833.wordpress.com/palvelinten-hallinta-harjoitus-7/


# c) Aja toisen tekemä tila

Valitsen Liisan modulin, koska haluan nähdä, tuleeko itselle sama ongelma, mikä Liisalle tuli.

Eli ensiksi kirjaudun virtuaalikoneelleni. Siellä on jo masterkone t001 ja orjakone t002 valmiina. Olin asentanut virtuaalikoneelleni jo valmiiksi curlin ja apachen edellisten tehtävien yhteydessä. 
Asensin ensiksi master-koneelle Mariadb:n, jonka asennus onnistui: 

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/6430a622-da8c-42c2-9b15-9dc460c698b8)

Jonka jälkeen asensin saltilla Marian orjakoneelle. Ja taisi ilmeisesti onnistua:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/bf5b9c75-c349-4ede-9a51-64931fc400c3)

Ja serverin asennus onnistui myös:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/ef2fd487-d953-46d4-acc9-7aa0e5e762f8)

Tässä vielä vertailunvuoksi virheilmoitus Liisan moduulista, jossa asennus ei onnistunut:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/997471f1-3b71-465d-9c2c-1e84251f431f)

Moduli oli 


