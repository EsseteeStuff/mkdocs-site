Stel je voor dat je als software ontwikkelaar een python applicatie ontworpen hebt met de naam Test. Je bent nu heel fier dat het programma heel goed werkt en je wilt een paar vrienden je programma laten zien. Je maakt een zip bestand van je folder Test en je zendt het naar je vrienden. Je vrienden willen het programma opstarten, maar bij geen enkele wil het programma werken. Dan is jou reactie, maar hoe kan dat, hier op mijn computer werkt het perfect.

Inderdaad op jouw computer werkt het omdat jij ook verschillende onderdelen op je computer hebt geinstalleerd, dat zij dan niet op hun computer hebben. Misschien hebben zij zelfs Python niet op hun computer.

Om deze problemen te verhelpen, hebben ze de virtuele omgeving uitgevonden. Een virtuele omgeving werkt los van de software op je computer. Je werkt dus in een soort sandbox. Als jij een virtuele omgeving opzet zal jouw versie van python bv 3.12 zijn. Je vriend zijn python versie  is bv 3.8. Python versies zijn compatibel met versies lager, maar nooit met versies hoger. Dus je vriend zal hoogstwaarschijnlijk niet in staat zijn om jouw python code op zijn computer uit te voeren. Met een virtuele omgeving, zal je vriend jouw versie van python installeren op zijn computer. De virtuele omgeving zal ervoor zorgen dat de versie van Python op zijn computer niet gewijzigd zal worden en dit om conflicten te vermijden.

**Het opzetten van een virtuele omgeving.**

1. _Windows_

    Open een powershell terminal en geef de volgende commando's in:

```
mkdir Test
cd Test
pip install virtualenv
python -m venv .venv
.venv/Scripts/activate
```

    Je gaat nu zien dat je shell veranderd. In mijn geval **(.venv) PS C:\Users\serge\Test>**. (.venv) zal waarschijnlijk in het groen zijn. Alles wat je nu doet in deze omgeving zal enkel in deze omgeving werken, los van alle software op je computer.

2. _Linux_

    Open een terminal en geef de volgende commando's in:

```
mkdir Test
cd Test
python3 -m venv .venv
source .venv/bin/activate
```

    Onder linux zal je nu ook de (.venv) zien verschijnen aan het begin van de shell.

3. _De virtuele omgeving delen._

    Er moet nu een middel zijn om deze virtuele omgeving door te geven naar anderen. Pip heeft daar een mechanisme voor. Geef het volgende commando in:

```
pip freeze > requirements.txt
```

    Als je nu dit bestand gaat openen zul je iets zien als:

```
Babel==2.15.0
certifi==2024.6.2
charset-normalizer==3.3.2
click==8.1.7
colorama==0.4.6
ghp-import==2.1.0
idna==3.7
Jinja2==3.1.4
Markdown==3.6
MarkupSafe==2.1.5
[...]
```

    Dit bestand bevat nu alle python onderdelen en hun betreffende versies om te kunnen werken in deze omgeving. Met het volgende commando:

```
pip install -r requirements.txt
```

    zullen alle nodige bibliotheken op een andere computer in een virtuele omgeving worden geinstalleerd. Het is dus belangrijk om het commando **pip freeze > requirements.txt** uit te voeren vooraleer je jouw project naar iemand anders stuurt. Als die dan op zijn computer in een virtuele omgeving de installatie uitvoert van het requirements.txt bestand, zal jou programma evengoed werken als op jouw computer.

Hopelijk zie je het nut in van een virtuele omgeving in.


Cheers!
