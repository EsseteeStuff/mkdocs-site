**A. Downloaden en importeren van de Oracle VirtualBox gpg sleutel.**
   
```
wget -O- -q https://www.virtualbox.org/download/oracle_vbox_2016.asc | sudo gpg --dearmour -o /usr/share/keyrings/oracle_vbox_2016.gpg
```

**B. De VirtualBox repositry toevoegen.**

```
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/oracle_vbox_2016.gpg] http://download.virtualbox.org/virtualbox/debian bookworm contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
```

Na het toevoegen geef het volgende commando in:

```
sudo apt update && sudo apt install virtualbox-7.0
```
   
**C. Het extention pack installeren.**

Het uitbreiden van VirtualBox met het extention pack voegt het volgende toe:

* USB 2 and USB 3 support
* VirtualBox [Remote Desktop](https://linuxiac.com/remote-desktop-with-linux/) Protocol (VRDP)
* Host webcam passthrough
* [Disk image](https://linuxiac.com/best-free-hard-disk-imaging-software/) encryption with AES algorithm
* Intel PXE boot ROM

De versie van het extention pack moet overeenkomen met de VirtualBox versie. Om de juiste versie te downloaden geef het volgende commando:

```
vboxmanage -v | cut -dr -f1
```
In mijn geval geeft dat:
  
```
serge@debian:~/Downloads$ vboxmanage -v | cut -dr -f1
7.0.20
 ```

Download de juiste versie van: [https://download.virtualbox.org/virtualbox/](https://download.virtualbox.org/virtualbox/)

Ga dan naar de folder waar je het bestand hebt gedownload en geef het commando:

```
sudo vboxmanage extpack install Oracle_VM_VirtualBox_Extension_Pack-7.0.10.vbox-extpack
```
Om gebruik te kunnen maken van de de uitbreidingen moet de gebruiker in de groep vboxusers zitten. We doen dat als volgt:

  ```
  sudo usermod -aG vbosxusers JOUW_USER_NAAM
  ```

Reboot jouw computer en geniet van VirtualBox



Cheers!


