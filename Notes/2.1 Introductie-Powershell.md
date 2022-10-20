01-10-2022

# Windows Server 1 Opdracht PS1: introductie PowerSHell - Pieter Dc

## A. Basisconcepten

- Voer het commando Get-Help uit (zonder parameters). Welke parameter kan je gebruiken bij dit commando om de Online versie van een helppagina in de browser te openen?

        get-help get-help -online

- Ga op zoek naar het commando uit om de help files van het internet te downloaden en installeren. Voer dit commando uit.

        Update-help

- Toon de Help voor het commando Get-Alias (output in terminal). Toon hierbij de volledige (“full”) output inclusief voorbeelden. Welke parameters zijn verplicht bij gebruik van het commando Get-Alias?

        get-help get-alias -full
        geen verplichte parameters

- Toon een overzicht van alle werkwoorden die gebruikt worden binnen commando’s in PowerShell.

        get-verb

- Idem als vorige vraag, maar toon enkel werkwoorden die ergens de letter X in de naam hebben

        get-verb *x*

- Toon een overzicht van alle commando’s die ingeladen zijn.

        get-command

- Toon een overzicht van alle commando’s die beginnen met Get- en ergens User in de naam hebben

        get-command Get-*User*

- Toon een overzicht van alle PowerShell providers die momenteel ingeladen zijn

        get-psprovider

### Pipeline | wordt gebruikt om het resultaat van een commando door te geven aan een volgend commando.

- Maak gebruik van de pipeline in combinatie met where om enkel werkwoorden te tonen uit de common groep.

        get-verb | where{$_.group -eq 'common'}

- Geef een overzicht van alle commando’s die als CommandType de waarde Alias hebben.

        get-command | where{$_.commandtype -eq 'Alias'}

- Vraag een overzicht op van alle commando’s die je reeds uitgevoerd hebt.

        get-history
        of gebruik de alias: h

## B. Getters en Setters

- Vraag de huidige werkdirectory op via een Get commando.

        get-location
        of gebruik de alias: pwd

- Wijzig de huidige werkdirectory naar C:\Users via een Set commando.

        set-location C:\Users
        of gebruik de alias: chdir C:\Users

- Vraag de huidige datum en tijdstip op via een Get commando.

        get-date

- Idem als de vorige vraag, maar in het jaar 2019.

        get-date -year 2019

- Gebruik hetzelfde Get commando om na te gaan welke dag van de week 1/1/2000 was.

        get-date -year 2000 -month 1 -day 1

- Vraag een overzicht op van alle disks die gekend zijn binnen Windows.

        get-psdrive
        of get-volume

- Vraag een overzicht op van alle partities die gekend zijn binnen Windows.

        get-partition

- Vraag een overzicht op van alle lokale gebruikers.

        get-localuser

- Vraag een overzicht op van alle lokale gebruikers die niet actief zijn.

        get-localuser | where{$_.enabled -eq $false}

- Vraag een overzicht op van alle IP-adressen die gebruikt worden op jouw VM.

        get-netipaddress

- Vraag een overzicht op van alle netwerkkaarten in jouw VM.

        get-netadapter

- Idem als de vorige vraag, maar sorteer deze op basis van het MAC adres. Gebruik hiervoor een pipeline in combinatie met Sort.

        get-netadapter | sort macaddress

- Idem als de vorige vraag, maar sorteer de interfaces op basis van de ifIndex in aflopende volgorde.

        get-netadapter | sort ifindex
