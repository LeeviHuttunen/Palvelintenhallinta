# Miniprojekti Leevi Huttunen 2024

# Projektin tarkoitus:
Projektin tarkoituksena on tehdä jalkapallojoukkueelle kotisivut, jonne lisätään Saltilla uusille käyttäjille käyttäjänimet ja salasanat. Aloitetaan kuitenkin ns. Nollasta, eli ladataan tarvittavat paketit ja määritellään palomuurin ja apachen asetukset. 

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
Valitaan kuitenkin sieltä OpenSSH, jotta palomuuri sallii ssh-yhteyden. Joten komennolla `sudo ufw allow OpenSSH` annettin lupa ssh-yhteydelle:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/3935ce07-10d0-498a-a27a-1e8eaf6c84d9)

Annetaan lupa http:lle. 

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/385e787b-c05f-4eed-8e68-39e09cc12e84)

Ja varmuuden vuoksi vielä portti 80:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/31a4d304-78e3-4f7e-9e7e-1db4bf7e29c5)

Sallitaan lupa ulos lähtevälle liikenteelle:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/9e697819-b49b-4715-b2f1-9cb411726f62)








