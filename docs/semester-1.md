# Semester 1

## Git installeren en configureren

We raden aan om een package manager te gebruiken voor de installatie van software, ook op Windows ([Winget](https://learn.microsoft.com/en-us/windows/package-manager/winget/)) of macOS ([Homebrew](https://brew.sh/)).

Om met Git te kunnen werken heb je op zijn minst de Git CLI client nodig. Er bestaan ook verschillende GUI clients en daar bevelen we Gitkraken aan. Gitkraken is een commerciële tool (weliswaar met een gratis basisversie), maar verderop vind je instructies voor gratis toegang.

=== "Windows"

    Open Windows Terminal met Administrator-rechten en voer volgende commando's uit:

    ```console
    > winget install Git.Git
    > winget install Axosoft.GitKraken
    ```

    Als je toch verkiest om Winget niet te gebruiken, dan kan je de software downloaden via de website: <https://git-scm.com> en <https://www.gitkraken.com>.

=== "macOS"

    Open een terminal en voer volgende commando's uit:

    ```console
    $ brew install git
    $ brew install --cask gitkraken
    ```

=== "Linux"

    Open een terminal en voer het volgende commando uit:

    ```console
    $ sudo apt install git
    ```

    Gitkraken zit niet in de default repositories van de meeste Linux-distributies. Je kan het downloaden van de website als .deb: <https://www.gitkraken.com/download>. Vervolgens kan je het installeren met:

    ```console
    $ sudo apt install ./gitkraken-amd64.deb
    ```

=== "RedHat/Fedora/SuSE"

    Open een terminal en voer het volgende commando uit:

    ```console
    sudo dnf install git
    ```

    Gitkraken zit niet in de default repositories van de meeste Linux-distributies. Je kan het downloaden van de website als .rpm: <https://www.gitkraken.com/download>. Vervolgens kan je het installeren met:

    ```console
    $ sudo dnf install ./gitkraken-amd64.rpm
    ```

Op elk toestel waar je gebruik maakt van Git (later ook binnen virtuele machines!) moet je een aantal basisinstellingen configureren. Open een terminal en voer volgende commando's uit (vervang de placeholders in hoofdletters door je eigen gegevens):

```console
> git config --global user.name "VOORNAAM ACHTERNAAM"
> git config --global user.email "VOORNAAM.ACHTERNAAM@student.hogent.be"
> git config --global push.default simple
> git config --global core.autocrlf true   # <- Windows
> git config --global core.autocrlf input  # <- macOS/Linux
> git config --global init.defaultBranch main
> git config --global pull.rebase true
> git config --global rebase.autoStash true
> git config --global core.ignorecase false
```

## Een Github-account aanmaken

Voor de vele opdrachten in verschillende vakken van de opleiding zal je een Github-account nodig hebben. Je kan een account aanmaken op <https://github.com>. Daarbij is het belangrijk om volgende zaken in acht te nemen:

- Kies een gebruikersnaam die **professioneel** oogt.
- Vul je echte naam in bij je profiel.
- Je kan meerdere emailadressen koppelen aan een Github-account. Koppel op zijn minst je **HOGENT-emailadres** (met de extensie `@student.hogent.be`) aan je account. Dit is nodig om jouw bijdragen aan een teamopdracht te kunnen identificeren en om toegang te krijgen tot bepaalde commerciële features van Github (zie verder). Eventueel kan je ook je primaire persoonlijke emailadres koppelen zodat je nog toegang hebt tot je account na je afstuderen.

Als student aan HOGENT kan je aanspraak maken op het [Github Student Developer Pack](https://education.github.com/pack). Dit is nodig om gebruik te kunnen maken van bepaalde commerciële features van Github, zoals private repositories. Volg de link naar de website en klik door op de groene knoppen "Sign up for Student Developer Pack" > "Get Student benefits". Lees vervolgens aandachtig de instructies! Het proces om goedkeuring te krijgen kan enkele dagen duren, maar daarna heb je zolang je student bent toegang tot de voordelen.

## Read-only gebruik van een repository

Als je enkel de inhoud van een repository wil bijhouden op je pc, dan kan je de repository clonen. Dit betekent dat je een lokale kopie maakt van de repository, inclusief de volledige historiek. Je kan dan de inhoud van de repository bekijken, maar je kan geen wijzigingen aanbrengen en je kan de wijzigingen van anderen niet pushen naar de repository. Sommige vakken zullen cursusmateriaal op deze manier ter beschikking stellen.

Ga naar de repository op Github via de link die je van de lectoren hebt gekregen. Klik op de groene knop "Code". Je vindt hier verschillende manieren om de repository te downloaden naar je eigen pc.

![Github repository download](./assets/github-code.png)

- Met download ZIP haal je de laatste revisie van de code binnen als een zip-bestand. Je hebt echter geen historiek en kan latere wijzigingen aand e code op Github niet makkelijk bijhouden.
- De HTTPS-link kan je gebruiken om de repository lokaal te klonen (d.w.z. een kopie downloaden met de volledige historiek). Hiermee heb je enkel leestoegang tot de repository. Kopieer de URL in het tekstveld.
- De SSH-link zal je later leren gebruiken om ook schrijftoegang te krijgen tot een Github-repository.
- Github CLI en Github Desktop zijn optionele tools om repositories te beheren, maar hier gaan we niet verder op in.

Open een terminal en navigeer naar de map waar je de repository wil clonen. Voer het volgende commando uit (maar dan met de URL die je daarnet gekopieerd hebt):

```console
> git clone https://github.com/USERNAME/REPOSITORY.git
```

Er wordt nu een nieuwe subdirectory aangemaakt met daarin de laatste toestand van de code zoals die nu ook op Github te zien is.

Als de code op de repository is aangepast, kan je de lokale kopie updaten met de laatste wijzigingen. Ga naar de map van de repository en voer het volgende commando uit:

```console
> cd REPOSITORY
> git pull
```

Let op: in deze opstelling is het niet de bedoeling dat je wijzigingen aanbrengt aan de code in de repository. Kopieer bestanden die je wilt wijzigen naar een andere directory buiten de repository.
