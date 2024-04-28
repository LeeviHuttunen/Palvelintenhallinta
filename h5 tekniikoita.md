# x) 


# a) Asenna Salt Windowsille tai Macille. Osoita 'salt-call --local' komentoa ajamalla, että asennus on onnistunut.

Salt oli jo aikaisemmin asennettu Windowsille. Olin myös aikaisemmin tehnyt hello world-tiedoston. Joten koitin ajaa hello world-tilan komennolla 
"\srv\salt> salt-call --local -l info state.apply hello --file-root C:/srv/salt/"

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/862486e1-753e-4e24-9504-e41d9a51a8ef)

 Ja heipat sieltä tuli, kuten pitikin.


 # b) Kerää Windows- tai Mac-koneesta tietoa grains.items -toiminnolla

Aluksi pukkasi erroria kun koitin hakea tietoja komennolla "salt-call grains.items" Sitten koitin hakea tietoja paikallisesti komennolla "salt-call grains.items --local"
josta sain sitten tiedot:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/060de9e1-d382-4ee3-8faa-ff424c31211c)

Muutama valinta tiedoista:

Ip-osoite ja verkon alipeite:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/8725cc6e-0735-4b55-9d94-34f5014a61f5)

Koneen kokonaismuisti:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/2805b03d-8e41-4ccc-98e7-2640f52ca013)


# c)  Kokeile Saltin file -toimintoa Windowsilla tai Macilla.

Tein uuden file.managed-tilan tekstieditorilla kohteeseen /srv/salt/Hello.

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/1ea23a71-0093-4213-ae9b-48c403c13032)

Sitten ajoin tilan komennolla "salt-call --local -l info state.apply Hello --file-root C:\srv\salt\Hello\" 
Tila suoritettiin, vaikka se ei onnistunut:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/79e4a4b8-b755-484b-bc4e-e1dc6f02478e)



# d) Näytä 'find' avulla viimeisimmäksi muokatut tiedostot /etc/-hakemistosta ja kotihakemistostasi

Aluksi ihmettelin, missä etc-hakemistoni on windowsissa. Pienen etsinnän jälkeen se löytyi polusta C:/Windows/System32/drivers/etc
En ole koskaan käynyt kyseisessä hakemistolla omalla koneella, kuten alla olevan kuvan muokkaus päivämääristä voidaan päätellä. 

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/ef10c9c4-0eda-4547-b774-a782b1f9ab3f)

"Get Child-Item" komennolla saadaan tietoja 
Asetin kuvassa olevat tiedostot järjestykseen komennolla "Sort-Object LastWriteTime" ja valitsin viisi tiedostoa komennolla "Select-Object -First 5"

Ja tässä vielä sama juttu omasta kotihakemistostani:

![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/c0415c17-44c4-4c73-8e17-8a55d428a140)


# e) Tee Salt-tila, joka asentaa järjestelmään uuden komennon.




