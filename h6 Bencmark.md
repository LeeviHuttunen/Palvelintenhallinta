# X) Windows package manager
- Windows package managerin asentaminen saltilla helpottaa erilaisten sovellusten ja pakettien lataamista Windowsille. Uusia sovelluksia ja paketteja ei tarvitse enää hakea 
netistä, vaan niitä voidaan ladata muutamalla käskyllä. Aivan kuin Linuxilla. 
- Pitäisi ladata git-varasto Saltin sivuilta, jotta .sls tiedostoja voidaan käyttää.
- Seuraavaksi päivitetään database komennolla "salt-call --local pkg.refresh_db" Tämä siis paikallisesti, jos koneella ei ole herra-orja arkkitehtuuria.
- Seuraavaksi pitäisi tulla seuraavanlainen ilmoitus, että päivitys onnistui:

  ![image](https://github.com/LeeviHuttunen/Palvelintenhallinta/assets/165004822/27114151-fde7-4789-a3af-44f61a05f0c3)

- Sitten package managerin pitäisi toimia. Komennolla "pkg.install" voi ladata erilaisia sovelluksia ja paketteja.
- Komennolla "pkg.remove" voi poistaa paketin. Paikallisesti siis koko komento on vaikka Mozilla Firefoxin poistoon "salt-call --local pkg.remove firefox_x64".
- Komennolla "salt-call --local pkg.list_pkgs" salt tekee listan sovelluksista ja paketeista, jotka on asennettu.
