# Miniprojekti Leevi Huttunen 2024

# Projektin tarkoitus:
Projektin tarkoituksena on tehdä jalkapallojoukkueelle kotisivut, jonne lisätään Saltilla uusille käyttäjille käyttäjänimet ja salasanat. Aloitetaan kuitenkin ns. Nollasta, eli
ladataan tarvittavat paketit ja määritellään palomuurin ja apachen asetukset. 

## Aloitus:
Aivan ensiksi loin uuden virtuaalikoneen komennolla    `vagrant init debian/bullseye64` Sitten kirjauduin koneelle sisään.
Ensimmäisenä latasin varmuuden vuoksi uusimmat päivitykset komennolla    `sudo apt-get update`

Asensin seuraavaksi apachen Komennolla `sudo apt install apache2`
Ja näin apache2 löytyi /etc hakemistosta.

Sitten asensin Saltin, jota hyödynnetään myöhemmin tässä tehtävässä. Komennolla `sudo apt-get install salt-master` asensin saltin. Sitten vielä tarkistin, että salt löytyy:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/0ea95b12-96ac-4b8d-8ff4-2dbfe87b05a0)

Ufw-palomuuri löytyy jo valmiiksi, joten sitä ei tarvitse asentaa.



