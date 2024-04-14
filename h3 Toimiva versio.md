# Tehtävä x)
- Git on kätevä työkalu tiedostojen muokkaamiseen, varsinkin jos mukana on useampia ihmisiä. Gitillä pystyy helposti tarkastamaan, kuka on tehnyt päivityksiä ja mihin
kellonaikaan
Seuraavassa selitän hieman Gitin komentoja. Kun tiedostoa on muokattu ja muokatut tiedot haluaa tallentaa, pitää ajaa komento  "git add . && git commit; git pull && git push"
-   "Git add" tarkoittaa tiedostoa, johon aikoo tehdä muutoksia, tai jonka aikoo poistaa. Jos laittaa git add-komennon perään pisteen, se tarkoittaa päivitysten tekemistä kaikkiin
tiedostoihin kyseisessä varastossa. Komento   "git add <path>" tekee päivityksen vain tiettyyn tiedostoon. Git add ei siis tee muuta, kuin valitse tiedoston, mihin muutos tehdään.
-   "Git commit" komento on vähän niin kuin tallenusnappula, joka tehdään muokatulle tai poistetulle tiedostolle.  "Git commit" ei kuitenkaan toimi ilman komentoa  "git add".
-   "Git pull" komennolla päivitetään sivustolle tehdyt muutokset paikallisesti, jotta muutokset tulee näkyviin.
-   "Git push" komennolla päivitetään sivuston muutokset myös etäyhteydellä.

 # Tehtävä a)
  Ensimmäisenä tehtävänä oli rakentaa uusi varasto GitHubiin ja lisätä sinne muutama tiedosto. Tein uuteen varastoon vielä ylimääräisen testitiedoston, jota voi sitten muokata
  myöhemmin gitillä.

  ![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/71bd4e3d-937d-46d0-8dfc-c3895a07e90b)

# b) Dolly. Kloonaa edellisessä kohdassa tehty uusi varasto itsellesi, tee muutoksia omalla koneella, puske ne palvelimelle, ja näytä, että ne ilmestyvät weppiliittymään.
Ensiksi kloonasin varaston itselleni:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/59ccb068-191d-48c7-aa9b-9fb52e9ca89b)

Ja näin kloonaus on tehty ja avaimen kautta päästy palvelimelle.

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/945085ac-411c-4f1b-b8c2-3740ef13ad49)

Tässä vielä näkyvät samat kansiot, mitkä ovat webbiliittymässä.

Ja tässä muokkasin yhtä tiedostoa:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/083944f8-25f0-4a20-a9ce-462f13f9c993)

Jonka jälkeen kuuluisat sanat:   git add . && git commit; git pull && git push
Ainakin palvelimella näkyi, että muutoksia tehty:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/d66d874f-16b9-41c1-b336-61a4feee32c6)

Ja sinnehän se kissa ilmestyi:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/6d368f10-ec4a-4acd-b2df-3f3f3e8c0368)

# c) Doh! Tee tyhmä muutos gittiin, älä tee commit:tia. Tuhoa huonot muutokset ‘git reset --hard’. Huomaa, että tässä toiminnossa ei ole peruutusnappia.

Seuraavaksi harjoittelin muutosten peruuttamista. Tässä kirjoitin vahingossa Hepreaa Gittiin:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/b340d113-0e72-4c2c-a56f-7eb8a83660a9)

Jonka jälkeen en kuitenkaan ajanut komentoa  "git add . && git commit; git pull && git push". Vaan laitoin komennon  "git reset --hard", josta seurasi seuraavanlainen ilmoitus:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/03c00d05-438a-40f5-9017-5b7ab18e4183)

Ja näin virheellinen teksti oli saatu pois:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/61db4711-0739-4857-a95a-bc99880a80a4)


# d) Tukki. Tarkastele ja selitä varastosi lokia. Tarkista, että nimesi ja sähköpostiosoitteesi näkyy haluamallasi tavalla ja korjaa tarvittaessa.
Komennolla  "git log" pääsee tarkastelemaan, ketkä ovat tehneet muutoksia varastossa ja mihin aikaan.

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/87a4ca70-b4dd-41d4-9bd4-d1b5a0dda1bb)

Kuvassa näkyy, kuka on tehnyt muutoksia gitissä ja mihin aikaan. Lokissa näkyy myös millaisia muutoksia on tehty mihinkin tiedostoon. Jos samassa projektissa samoissa
tiedostoissa on useampia työntekijöitä, on tärkeää kirjoittaa aina selitys, että mitä muutoksia on tehty tiedostoille.

# e) Suolattu rakki. Aja Salt-tiloja omasta varastostasi.
Ensiksi tein nano-tiedoston ja kirjoitin sinne salt-tilan:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/3b03ee1d-001c-45df-ba99-dcc3caa07d78)

Jonka jälkeen koitin ajaa tilan  "state.apply", mutta erroria pukkasi. Myöskään  "grains.items" komento ei toiminut, jonka pitäisi näyttää edes koneen tiedot.
Olin asentanut saltin virtuaalikoneelle Linuxiin, johon se on paljon helpompaa, kuin Powershelliin.
Koitin asentaa Saltin uudelleen koneelle, mutta Salt ei silti suostunut yhteistyöhön:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/e7735e65-52f4-4423-b94c-f1100203dc3b)

Yritin myös tarkkaa polkua, mutta ei silti toiminut.
Selvittelen ensi tunnilla, kuinka ratkaista kyseinen ongelma.

# Lähteet

terokarvinen.com

https://github.com/git-guides

https://git-scm.com/

Kurssin tehtäväsivut
