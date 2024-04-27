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


# c) 


