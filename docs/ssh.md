Inloggen met een sleutel is makkelijker dan het onthouden van een ingewikkeld wachtwoord. Sleutels zijn echter ook te kraken, enorm veel moeilijker dan wachtwoorden. De sterkte van je eigen sleutel hangt af van de wijze waarop hij versleuteld wordt. Je kan die versleutelen met de volgende bits:

* 512
* 1024
* 2048
* 4096
* 8192
* 16384

De tijdspanne om het aanmaken van een eigen sleutel, hangt af van je hardware. Als je voor de 16384 bits versleuteling gaat, kan dit een tijdje duren voor hij klaar is.

Een sleutel maak je aan met het volgende commando:

```bash
ssh-keygen -t rsa -b 4096
```


4096 bits is de standaard en wereldwijd ondersteund.

Als je de sleutel aanmaakt ga je een vraag krijgen waar hij de sleutel moet opslaan. Druk gewoon op enter om de default te kiezen.

Vervolgens gaat hij vragen voor een wachtwoord zin. Druk hier ook gewoon op enter zonder een wachtwoord in te geven.

```
    ssh-keygen -t rsa -b 4096
    Generating public/private rsa key pair.
    Enter file in which to save the key (/home/serge/.ssh/id_rsa):
    Created directory '/home/serge/.ssh'
    Enter passphrase (empty for no passphrase):
    Enter same passphrase again:
    Your identification has been saved in /home/serge/.ssh/id_rsa
    Your public key has been saved in /home/serge/.ssh/id_rsa.pub
    The key fingerprint is:
    SHA256:ng328qUhKzQ4XngR37Q//x2d1p4OKfe37SB480F40tU serge@Ryzen7-WDC
    The key's randomart image is:
    +---[RSA 4096]----+
    |                 |
    |      .   .     .|
    |       o o .    E|
    |      . . o  o . |
    |     o .S  .o +  |
    |    + =o = .o+. +|
    |   . = .= =.=*o+o|
    |    . .  = =o+=+*|
    |       .. o   oBO|
    +----[SHA256]-----+
     
```

De sleutel werd opgeslagen in ~/.ssh als id\_rsa.pub

Als je nu deze sleutel wenst te gebruiken op een server dan doe je dit zo.

```bash
ssh-copy-id UW_INLOGNAAM@IP_ADRES of UW_INLOGNAAM@SITE_NAAM.
voorbeeld:
ssh-copy-id user@192.168.5.201 of ssh-copy-id user@www.essetee.be
```
De server zal jouw wachtwoord vragen dat je normaal gebruikt om aan te melden. Hij zal dan vervolgens vragen om te testen of het werkt.

Dan kan je gewoon ssh user@server doen. Zonder een wachtwoord te vragen zou het moeten lukken om in te loggen nu.

Stel nu dat je usernaam jean-pierre.klaplopereersteklas@devergeetmijnietjesclub.be is. Dan is het nog steeds lastig om dat in te tikken. Maar we kunnen dit ook oplossen.

Maak nu in je .ssh folder een nieuw bestand aan met de naam config en met de inhoud:

```
Host bloem
    User jean-pierre.klaplopereersteklas
    Port 22
    IdentityFile ~/.ssh/id_rsa
    HostName www.devergeetmijnietjesclub.be
```


Nadat je het bestand hebt opgeslagen kan je nu gewoon **_ ssh bloem_** doen om te verbinden met die server. Veel makkelijker toch :) Dit bestand kan meerdere verschillende hosts bevatten. Voeg een blanco regel in en daaronder vul je dan een nieuwe host in.

In het bestand /etc/ssh/sshd_config kan je deze zo aanpassen dat je enkel kan inloggen met een publieke sleutel. Eenmaal je een sleutel hebt, maak een backup van je .ssh folder en bewaar die zorgvuldig. Mocht je om één of andere reden je OS opnieuw installeren, plaats de backup van je ssh folder terug. Anders kan je nooit meer op afstand inloggen op een server waarvoor je deze sleutel gebruikt. En de .ssh folder is "for your eyes only" ! Dus doe het volgende:

```bash
chmod -R 0600 ~/.ssh
```

Cheers!
