# Miniprojekti Leevi Huttunen 2024

Lisenssi: GNU General Public License, versio 3


# Projektin tarkoitus:
Projektin tarkoituksena oli tehdä jalkapallojoukkueelle kotisivut, jonne lisätään https-sertifikaatti. Ladataan tarvittavat paketit, käytetään hieman saltia ja määritellään palomuurin ja apachen asetukset. Tähän tuli kuitenkin muutos, kun en päässytkään enää virtuaalikoneeseen sisälle yön jälkeen. Onneksi minulla on kuitenkin vielä kurssin alusta jäänyt virtuaalikone, joten koitetaan siellä tehdä vielä hommaa eteenpäin niin paljon, kuin ehtii.

## Aloitus:
Aivan ensiksi loin uuden virtuaalikoneen komennolla    `vagrant init debian/bullseye64` Sitten kirjauduin koneelle sisään.
Ensimmäisenä latasin varmuuden vuoksi uusimmat päivitykset komennolla    `sudo apt-get update`

Asensin seuraavaksi apachen Komennolla `sudo apt install apache2`
Ja näin apache2 löytyi /etc hakemistosta.

Sitten asensin Saltin, jota hyödynnetään myöhemmin tässä tehtävässä. Komennolla `sudo apt-get install salt-minion` asensin saltin. Sitten vielä tarkistin, että salt löytyy:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/10c7971f-f060-4850-9559-905e2b9bd1ef)

Ja katson vielä hello world-tilalla, että homma toimii.

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/85637a44-95c8-4b66-b10b-e52bc58b9aa3)


Ai niin! Tarvitaan vielä Curl Apachea varten. Asennetaan Curl Salt apuna komennolla `sudo salt-call --local -l info state.single pkg.installed curl` 

Ja vielä ladataan ufw-palomuuri `sudo apt-get install ufw`

Näillä pääsee alkuun, voi olla, että joudutaan vielä myöhemmin latailemaan lisää joitain paketteja.


## Apachea ja palomuuria

No niin, sitten päästään konfiguroimaan apachea ja ufw:tä. Ensiksi aletaan temppuilemaan ufw:n kanssa, jotta palomuuri päästää apachen siitä läpi. Katsotaan mitä appeja ufw antaa käyttää:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/aac622c0-f52e-4ca2-9dc9-c4d3f34ad58c)

Hmm.. Jännä juttu, siellä pitäisi olla apache..
Valitaan kuitenkin sieltä OpenSSH, jotta palomuuri sallii ssh-yhteyden. Joten komennolla `sudo ufw allow OpenSSH` annettiin lupa ssh-yhteydelle:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/3935ce07-10d0-498a-a27a-1e8eaf6c84d9)

Annetaan lupa http:lle. 

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/385e787b-c05f-4eed-8e68-39e09cc12e84)

Ja varmuuden vuoksi vielä portti 80:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/31a4d304-78e3-4f7e-9e7e-1db4bf7e29c5)

Sallitaan lupa ulos lähtevälle liikenteelle:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/9e697819-b49b-4715-b2f1-9cb411726f62)


## Seuraavana päivänä

Noniin jätin tämän tähän kohtaan ja koitin jatkaa projektia seuraavana päivänä. En päässyt enään tuolle samalle Vagrant-koneelle sisään. Curl localhost kuitenkin toimi tässä vaiheessa, jota en ehtinyt laittaa tähän.

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/36dc16f4-0adb-4849-bf6f-0c84aa7304ac)

Pitää vaihtaa taktiikkaa. Aikaa edellisissä kohdissa meni jo paljon ja aika alkaa loppumaan. Onneksi minulla on toinen virtuaalikone, joten jatketaan hommia sillä niin paljon, kuin ehditään.


## Apachea ja suolaa
Noniin, ensiksi katsotaan, mitä tällä virtuaalikoneella on. Olen käyttänyt tätä virtuaalikonetta aina välillä edellisissä tehtävissä. 
Koneella on valmiiksi asennettuna herra-orja arkkitehtuuri. Se asennettiin tehtävässäni h2 soitto kotiin.

Katsotaan vielä saltin cmd.run-tilalla:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/dff6590d-56af-40ff-ac3d-3261e141eed9)


![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/8eefa6d8-d5f4-4ebc-b81e-a9b40f5200bd)


Okei, asennetaan saltiin paketinhallinnalla apache ja curl:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/03e3dcf8-ed2f-4212-a23f-0097cb41e7d1)

Jaahas, siellä se Leevi-minion pyörii ja olinkin sinne laittanut alkuvaiheen kannalta hyödyllisiä paketteja Saltin paketinhallinnalla. Ylimpänä kuitenkin näkyy hello world-tila. Apachen ja Curlin asennus on myös varmistettu.. 
Muokataan etusivu.conf seuraavaan muotoon :

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/93947762-562a-4b89-90e2-7e2f0e2fbfed)

Ja laitetaan se polkuun /etc/apache2/sites-available ja /etc/apache2/sites-enabled/

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/d61b05be-c640-4cd8-abf8-2c43fc9b34b7)

Restartataan demoni ja katsotaan toimiiko. Komento `sudo systemctrl restart apache2` käynnistää apachen uudelleen.

Okei, ainakin etusivu.conf näyttää turkoosilta:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/e3dc687a-7a78-497d-8517-6c991f6c9a87)

Katsotaas Curl localhost.

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/b27b5c98-571f-4dc3-8637-d39e14fcd727)

Näkyyhän se. Katsotaan näkyykö sama web-selaimessa komennolla `hostname -I` ja sieltä laitetaan browseriin ip-osoite:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/ae8ba025-bb9a-49a7-8c48-4f8849d184d9)

Jeejee näkyy sekin. Seuraavaksi koittaa mielenkiintoinen kohta. Pitäisi koodata nettisivuille jonkinlainen sisältö. Ainakin laatikko, mistä voi kirjautua sisään. Ainut ohjelmistokehitys-kurssi tähän mennessä on vuosi sitten käyty javascript-peruskurssi vuosi sitten.

Menin siis tässä vaiheessa muokkaamaan index.html:llää. Tässä jonkinlainen alkeellinen nettisivu:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/baecafe0-3c37-44f5-b896-eb358743e6d2)

Aloitan tässä kohtaa "matalilla roikkuvista hedelmistä", eli teen ensin pienemmän koodin pätkän ja katson toimiiko se.
Kyllähän se harmittaisi koodata monta tuntia jotain huomatakseen, ettei homma toimi. Tässä kohtaa käytin apuna kätevää sivua html:llän alkeisiin https://www.w3schools.com/html/html_forms.asp

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/a6c0ecdd-252c-4f48-95ba-b3684120c628)

Noniin, nettisivu päivittyi, eli homma toimii. Pitää muistaa, ettei html näytä tykkäävään ääkkösistä. 

Seuraavaksi kokeilin tehdä command idempotentin apachelle. Laitoin seuraavan koodin uuteen init.sls-tiedostoon, johon laitoin seuraavat konfiguroinnit: (otettu terokarvisen materiaaleista https://terokarvinen.com/2018/04/03/apache-user-homepages-automatically-salt-package-file-service-example/)

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/7a1829cc-db97-4277-a574-4ff51efb3793)

Ja sitten ajoin konfiguroinnin:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/e952e909-7158-4f96-994d-8137e1721b1c)

Hmm.. Joku ei onnistunut. Katsotaas mikä näyttää punaista:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/14f18832-d3c0-424d-b295-9afd03bf0fdf)

Index.html ei taida olla oikeassa paikassa, kopsataan se oikeaan paikkaan ja koitetaan ajaa komento uudelleen.

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/d1e3781c-447e-49b8-8dbe-830ec0578f10)


Mutta ei silti onnistunut. Noh, ei se mitään. Koitin tätä selvitellä pitkään, mutta en saanut selville, missä vika. Ainakin sivu toimii vielä, muut osat näyttävät vihreetä ja sivu näkee vieläkin selaimessa:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/da6a2b24-7b0a-4ace-8bc5-bf735e2ee542)


## Certbot

Noniin, katsotaas minulle uuden tuttavuuden Certbotin toimintaa. Certbot on avoimen lähdekoodin työkalu, jolla voi saada omalle nettisivulleen https-sertifikaatin. Sertifikaatti uusiutuu 60 päivän välein. Muistaakseni, kun sivun vaihtaa https:ssään, se menee hetkeksi hakutuloksissa viimeiseksi. 


Ensimmäiseksi pitäisi asentaa snap. Snap on paketinhallintajärjestelmä, saman tyyppinen kuin apt. Snapin pitää olla päällä taustalla, jotta se toimii. 

Asennetaan snap kommennolla `sudo apt install snapd` 
Seuraavaksi pyydettiin käynnistämään kone uudelleen, jotta snapin polut menevät oikeille paikoille? :D
Toki voi olla, että tällä tarkoitettiin apachea, en ole täysin varma.

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/a752fe53-4557-47dc-932a-5fffeb73e46b)

Tein kuitenkin työtä käskettyä.

Seuraavaksi asennetaan uusin snapin versio komennolla `sudo snap install core`

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/8228bc3c-1969-4892-8da3-0143d4071acf)

Asennus onnistui. 

Sitten asennetaan vielä snapilla hello world. 

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/71e1ecfd-e2f9-4719-9f1d-fd61102d81f5)

Hello worldin asennus onnistui. 

Komennolla `hello-world` näkee toimiiko se:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/477b0dc8-b4cb-4827-8fa5-1935f1a30933)

Toimii, Jee!

Noniin, sitten asennetaan se Certbot komennolla `sudo snap install --classic certbot` Certbottia ei siis voi vissiin asentaa apt-paketinhallinnan kautta?

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/b5cf3c44-81a8-4be7-b8ba-1d3b21cbb024)

Sitten pitää laittaa Certbot toimintavalmiuteen. Eli laitetaan komento `sudo ln -s /snap/bin/certbot /usr/bin/certbot`

Komento laitettu, mutta mitään ei tapahtunut:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/12ba4725-fe09-4693-99e2-51ca1adf1ac5)

Noniin, sitten viimeinen ja ratkaiseva vaihe. Asennetaan Certbot apacheen. Tällä hetkellä web-serverillä lukee, ettei apachella tehty nettisivu ole turvallinen:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/c5c98cdb-d377-4c64-8a87-3075e70404be)

Niin yksinkertaisella komennolla kuin `sudo certbot --apache` Certbotin pitäisi antaa sertifikaatti Apachen nettiserverille.
Kokeillaan pelonsekaisin tuntein: 

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/431bff68-69ac-4662-8ab8-4238d6200b4e)

Jaahas, sähköposti pitää laittaa.  Tässä vielä varoitellaan, että sertifikaattia ei voi jatkaa tulevaisuudessa, jos ei laita sähköpostia tähän.

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/70706358-421a-408b-852c-1236afb769ac)

Laitoin sähköpostin ja seuraavaksi kyseltii suostumuksia:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/dfc05171-2bc7-4b61-8da3-111693af592d)

Ja sitten kyseltiin, saako lähetellä mainoksia sähköpostiin:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/3a25131b-4a57-434f-8de5-b545001009fc)

Seuraavaksi kysyttiin domain nimeä. Laitan tähän ip-osoitteen, toivottavasti se kelpaa:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/601bfd43-9a3c-4472-a96c-cb291ca32dff)

Certbot ei myönnä pelkästään ip-osoitteille sertifikaattia, vaan pitäisi olla domain nimi. 

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/ccb1874b-ae1e-442d-945b-3799b2c35f8f)

Jaahas, taitaa jäädä domain-nimi hankkimatta. Uskon kuitenkin, että homma olisi onnistunut, mutta en näe tarvetta maksaa testisivun domainista.

Nettisivu jäi nyt "ei turvalliseksi" Domain nimen ostamalla ja Certbottia käyttämällä siitä olisi saatu "turvallinen".

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/416b291e-ade2-43b0-80de-1602a4474a45)

Olen kuitenkin suht tyytyväinen lopputulokseen, jos ottaa huomioon ekan Vagrant-koneen ongelmat. Olisi ollut kiva vielä tutustua Snap-paketinhallintaan, mutta se taitaa jäädä omalle ajalle.


# Lähteet

- Apachen serverin asetuksia. Luettavissa: https://ubuntu.com/server/docs/how-to-configure-apache2-settings Luettu 11.5.2024

- Certbotin sivut. Luettavissa: https://certbot.eff.org/instructions?ws=apache&os=debianbuster Luettu 11.5.2024

- Omat aikaisemmat kotitehtävät

- Karvinen, T. Apachen automatisointia https://terokarvinen.com/2018/04/03/apache-user-homepages-automatically-salt-package-file-service-example/

- Karvinen, T. Infra as code https://terokarvinen.com/2024/configuration-management-2024-spring/
