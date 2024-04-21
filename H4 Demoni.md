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

# c) 




