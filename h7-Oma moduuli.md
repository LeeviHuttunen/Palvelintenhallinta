# Miniprojekti Leevi Huttunen 2024

Lisenssi: GNU General Public License, versio 3


# Projektin tarkoitus:
Projektin tarkoituksena oli aluksi tehdä jalkapallojoukkueelle kotisivut, jonne lisätään Saltilla uusille käyttäjille käyttäjänimet ja salasanat. Ladataan tarvittavat paketit ja määritellään palomuurin ja apachen asetukset. Tähän tuli kuitenkin muutos, kun en päässytkään enää virtuaalikoneeseen sisälle yön jälkeen. Onneksi minulla on kuitenkin vielä kurssin alusta jäänyt virtuaalikone, joten koitetaan siellä tehdä vielä hommaa eteenpäin.

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


## 
Noniin, ensiksi katsotaan, mitä tällä virtuaalikoneella on. Olen käyttänyt tätä virtuaalikonetta aina välillä edellisissä tehtävissä. 
Koneella on valmiiksi asennettuna herra-orja arkkitehtuuri. 

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/dff6590d-56af-40ff-ac3d-3261e141eed9)

Okei, katsotaan nopeasti hello world tilalla saltin toiminta:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/03e3dcf8-ed2f-4212-a23f-0097cb41e7d1)

Jaahas, sinne oltiin jo laitettu vaikka mitä. Ylimpänä kuitenkin näkyy hello world-tila. Apachen asennus on myös tehty. Katsotaas Curl localhost.

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






