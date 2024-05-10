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

Ai niin! Tarvitaan vielä Curl Apachea varten. Asennetaan Curl Salt apuna komennolla `sudo salt-call --local -l info state.single pkg.installed curl` 




