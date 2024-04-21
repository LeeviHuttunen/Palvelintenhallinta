# X)

- Salt on todella hyödyllinen työkalu, jos haluaa ohjata montaa konetta samaan aikaan. Saltin asentaminen on varsinkin Linuxille helppoa ja nopeaa.
- YAML:llä voidaan listata erilaisia asetuksia saltille. YAML:llä voidaan käyttää vain listauksia, tai luetteloita. Ohessa esimerkki YAML-luettelosta:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/bcb06011-596a-41f2-a84f-1a8738bbbac8)

- Toki oikeassa luettelossa Saltissa luetellaan esimerkiksi tcp-portteja eikä hedelmiä.


# a) Hello SLS! Tee Hei maailma -tila kirjoittamalla se tekstitiedostoon, esim /srv/salt/hello/init.sls.

Ensimmäisenä tehtävänä oli luoda hello world-tila. Joten ensiksi loin kyseiseen osoitteeseen sls-tiedoston:

![Näyttökuva 2024-04-20 223330](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/591fa939-c67f-4013-b56e-e2ba5ae92042)

Jonne sitten laitoin kyseisen hello world-tilan:

![Näyttökuva 2024-04-20 223524](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/83de97b1-99d9-4450-847b-396806384c1a)

Sitten vielä tein .txt tiedoston, josta salt lukee kyseisen tilan:

![Näyttökuva 2024-04-20 223608](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/e6dd961c-7d83-4c89-bf72-4ee01aa98f31)

Ja sitten kokeilin toimiiko. Kyllä toimii! Eli näin on tehty hello world-tila

![Näyttökuva 2024-04-20 223730](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/60a4cb1d-81a3-4e7b-a458-d5e407d0b016)



# b) Top. Tee top.sls niin, että useita valitsemiasi tiloja ajetaan automaattisesti

Tein vielä toisen tilan samaan tiedostoon. Annoin käskyn asentaa paketti curl samalla hello worldin kanssa:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/5f54d8d4-46e1-4515-a063-0b3407e677aa)

Ja sitten vielä testasin, että salt tekee ne samaan aikaan. Ja kyllä teki.

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/c45a90b4-5b97-4dd3-98b5-2c109976ddb5)


# c) Apache easy mode. Asenna Apache, korvaa sen testisivu ja varmista, että demoni käynnistyy

Ensiksi koitin asentaa Apachen, mutta se olikin jo asennettu aikaisemmin:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/242d4bae-0b1f-4d81-83e9-85e5cf922fb9)

Seuraavaksi menin muokkaamaan Apache tiedostoja: Ensiksi kävin katsomassa sites-available ja muokkaamassa sitä kyseiseen muotoon:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/0f775261-7b9e-4653-8f1d-e980daf71c77)

Ja sitten tein paikkaan home/etusivu index.html tiedoston, jossa lukee tervehdys:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/48dd7f28-fc34-4dda-9558-ff280dc2869f)

Ja sitten restartin jälkeen vain testaaamaan, että toimiiko:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/b3f8f9c0-8941-4295-bfd6-350684a90295)

Ja näin se on tehty manuaalisesti. Seuraavassa vaiheessa pyydettiin automatisoimaan nämä asiat. Joten ensiksi laitoin muutaman komennon lisää sls-tiedostoon:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/c179e7ae-5586-46a8-84d5-af4d17d2280d)

Seuraavaksi restarttasin apachen ja katsoin toimiiko. Ilmeisesti kello oli väärässä ajassa:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/65e4e348-9602-49e0-a621-286cab799a2f)

Joten korjasin kellon ajan oikeaan seuraavalla komennolla:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/a0d2b2de-1bad-4d50-a040-9e6fe28441d6)

Kokeilin saltia uudelleen, jolloin tuli uusi virhe ilmoitus: salt-master ei vastaa:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/7dee3b03-5904-4228-bc59-4f5fd8427907)

Käynnistin Apachen jälleen uudelleen ja kokeilin uudelleen. Hetken kuluttua tuli ilmoitus, että homma toimii:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/e94aac22-9517-4fd0-9c33-0bb0f24ed477)


# d) SSHouto. Lisää uusi portti, jossa SSHd kuuntelee.

Ensiksi menin sshd_config tiedostoon:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/cd358b14-e231-40d2-91cc-67090c3be2a7)

Jossa pyydettiin jättämään port 22 auki. Käsitykseni mukaan se kuitenkin oli jo auki tässä tiedostossa ja otin # edestä pois.

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/0c61bcc0-f5f2-4469-ad2b-5db58921ade2)

Seuraavaksi tein uuden sls-tiedostoon muutoksia:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/426e0f9e-d622-45e8-acfd-2b0fdb560f76)

Ja sitten vielä srv/salt hakemistoon tilojen lisäys:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/69cfc31b-e475-466d-a7ea-7b2fc5c6e4ad)

Ja sitten testattiin, homma toimii:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/6ea8ffa7-57ab-446c-bd6d-7c4fb51e6c7f)

Näiden tehtävien jälkeen harjoittelin vielä hieman apachen asennusta tyhjälle virtuaalikoneelle, jotta se tulisi 
tutummaksi :)


## Lähteet:

Karvinen, T. Name Based Virtual Hosts on Apache. Luettavissa: https://terokarvinen.com/2018/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/?fromSearch=virtual%20host Luettu: 21.4.2024

Karvinen, T. Configuration management. Luettavissa: https://terokarvinen.com/2024/configuration-management-2024-spring/ Luettu: 21.4.2024

Karvinen, T. Salt Vagrant. Luettavissa: https://terokarvinen.com/2023/salt-vagrant/#infra-as-code---your-wishes-as-a-text-file Luettu 21.4.2024

Karvinen, T. Pkg-file-service. Luettavissa: https://terokarvinen.com/2018/04/03/pkg-file-service-control-daemons-with-salt-change-ssh-server-port/?fromSearch=karvinen%20salt%20ssh Luettu: 21.4.2024

Saltproject.io Salt overview. Luettavissa: https://docs.saltproject.io/salt/user-guide/en/latest/topics/overview.html#rules-of-yaml Luettu 21.4.2024
