# LinuxPalvelimet-h2-komentaja-Pingviini
    Kirjoittanut: Jesse Reunamo
    Kurssi:       Linux-palvelimet
    Linkki:       https://terokarvinen.com/2023/linux-palvelimet-2023-alkukevat/

## Tiivistelmä
Raportti linuxin komentorivin käyttämisestä, ja erinäisten ohjelmien asentamisesta.

## Linux komentorivin perusteet
Komentorivillä pystyy tekemään paljon operaatoita, jotka windows järjestelmällä vaatisivat graafisen käyttöliittymän käyttöä. Esimerkiksi ohjelmia voidaan asentaa käyttämällä komentoriviä. Käyttäjä voi navigoida linuxin tiedostojärjestelmässä pelkästään komentorivin avulla. Hyvä komento aloittelijalle muistettavaksi on:

    man <komento>
    
Man komennolla voit hankkia lisää tietoa kirjoitetun komennon käyttämisestä.

## Mikro tekstieditorin asennus
Ajettavat komennot:

    sudo apt update
    sudo apt install micro
    micro --version

Ensimmäisellä komennolla haemme uusimmat mahdolliset paketit linuxin paketinhallintajärjestelmästä, tämä varmistaa, että ohjelma, jonka haluamme asentaa on uusin mahdollinen versio. Toinen komento asentaa micro ohjelman. Kolmannella komennolla voimme vielä tarkistaa, että ohjelma on asentunut ja sen versionumeron. Katso kuva:

![Mikro3](https://user-images.githubusercontent.com/112503770/213953395-63898721-27a8-49dd-9111-4c6bf74f167d.png)


## Koneen raudan selvittäminen lshw komennolla
Linux tietokoneen raudan sisältö voidaan selvittää käyttämällä lshw ohjelmaa, mikäli sinulla ei ole ohjelmaa asennettuna aja komennot:

    sudo apt update
    sudo apt install lshw
    
Ensimmäisellä komennolla haemme uusimmat mahdolliset paketit linuxin paketinhallintajärjestelmästä, tämä varmistaa, että ohjelma, jonka haluamme asentaa on uusin mahdollinen versio. Toinen komento asentaa lshw ohjelman.

Ajamalla komennon:
    
    sudo lshw -short -sanitize
    
Tulostaa ohjelma komentoriville kuvauksen tietokoneen raudasta ks. kuva. Komennon vaihtoehdoilla -short ja -sanitize muokataan tulosteen dataa, että siitä tulisi luettavampaa (-short) ja se ei sisällä mahdollisesti arkoja tietoja (-sanitize).

![lshw1](https://user-images.githubusercontent.com/112503770/213954447-049daf79-328c-4268-9e36-c4d34c1f1955.png)

Listauksessa ilmenee tietokoneen järjestelmä, joka on VirtualBox, koska ajamme linuxia virtual boxissa. Tietokoneen järjestelmän biosin ja ramin muisti. Tietokoneen prosessori AMD Ryzen 7 5800x 8-core Processor. Listauksessa tulee ilmi tietokoneen osat, jotka ovat virtualisoituja tai emojärjestelmän kautta saatuja. Bridge kuvastaa järjestelmän erilaisia liitäntä laitteita, jotka pitävät huolen eri komponenttien välisestä keskustelusta. 

## Ohjelmien asentaminen
Seuraavaksi asennamme useamman komentoriviohjelman yhdellä komenolla. Ohjelmat, jotka asennamme ovat: Terminator, Cool retro term ja terminology. Kokeilemalla eri komentoriviohjelmia saat enememmän vaihtoehtoja hienosäätämiseen ja mahdollisuuden antaa visuaalista ilmettä komentoriville. 

    sudo apt update
    sudo apt-get install terminator cool-retro-term terminology
    
Terminator:

![terminal1](https://user-images.githubusercontent.com/112503770/213959446-f1ba1cc5-8e7f-4e22-be40-65deb471b763.png)

Cool retro term:

![terminal2](https://user-images.githubusercontent.com/112503770/213959467-c49501d7-4b64-494e-9e7b-53c912fa7387.png)

Terminology:

![terminal3](https://user-images.githubusercontent.com/112503770/213959471-0db3310b-6a33-4fa5-a393-077530f6ff70.png)

## Linux järjestelmän talletuspaikat
Hakemistojen peruskomentoja:

    cd <hakemiston nimi> komennolla voit siirtyä haluttuun hakemistoon.
    cd /                 esimerkiksi siirtää juuri hakemistoon
    ls <hakemiston nimi> näyttää hakemiston sisällön
    
Lyhyt listaus tärkeistä linuxin tallenuspaikoista, ja niistä esimerkit    

    /               Juuri hakemisto, jonka alapuolella on kaikki järjestelmän tiedostot
    
Sisältää tärkeän home kansion.

![fhs1](https://user-images.githubusercontent.com/112503770/213962801-6c9575e8-f0ce-4649-9e65-42bd112e7af2.png)

    /home/          Kaikkien käyttäjien tiedostot
    
Sisältää jokaiselle käyttäjälle tärkeän user kansion

    /home/user/     User käyttäjän tiedostot. Ainoa paikka johon käyttäjä user voi tallettaa tietoa
    
Sisältää käyttäjille tarkoitettuja kansioita esimerkiksi documents johon käyttäjä voi tallentaa tärkeitä raportteja.    

![fhs2](https://user-images.githubusercontent.com/112503770/213962868-de30cb62-8af1-4570-8104-314d55e7d522.png)

    /etc/           Järjestelmän asetukset
    
Järjestelmän epämääräisiä tiedostoja ja kansioita, esimerkkinä /etc/issue jossa ilmenee linuxin ennen kirjautumista oleva viesti.

![fhs3](https://user-images.githubusercontent.com/112503770/213962907-ff22b68b-fd3a-4d2b-80f3-7efeb4ee23f1.png)

    /media/         Poistettava media kuten cd tai usb
    
Järjestelmään liitetty media, tärkeitä media/cdrom tai media/usbdisk
    
    /var/log/       Järjestelmän logi tiedot
    
![fhs4](https://user-images.githubusercontent.com/112503770/213962957-b812effb-900f-4e13-b8ae-5c983d73403e.png)

## Grep-komennon käyttäminen
Erittäin hyödyllinen komento kun halutaan etsiä jotain tietoa, hieman samanalainen kuin windows ctrl + f toiminnallisuus.

Esimerkkejä:

    apt-cache search version control | grep 'terminal'
    
Komento ensin hakee kaikki version controlissa olevat paketit. Putkittamalla komennon tuloste merkillä-| grep komennolle voidaan laittaa '' sisään haettavissa oleva termi, jonka jälkeen koko komento tulostaa vain ne version controlissa olevat paketit joissa on hipsuissa oleva sana.

![grep1](https://user-images.githubusercontent.com/112503770/213964302-ef7cd49f-e571-4629-9984-d65c626fd66e.png)


    micro testi.txt
    grep 'kissa' testi.txt
    
Aikaisemmin tässä raportissa asennetulla micro editorilla voit luoda uuden tiedoston ensimmäisellä kommennolla. Syötettyäsi kommenon voit kirjoittaa tiedostoon mitä haluat, mutta tässä esimerkissä kannattaa kirjoittaa kissa yhdelle riville. Toinen komento tulostaa kaikki ne rivit testi.txt tiedostosta joissa lukee kissa.

![grep2](https://user-images.githubusercontent.com/112503770/213964314-01132545-a771-4d49-b6a4-a6e9aba0cdcc.png)


## Lähteet

    https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited
    https://linuxhint.com/install-micro-text-editor-linux/
    https://linux.die.net/man/1/lshw
    http://www.dba-oracle.com/linux/important_files_directories.htm
    
