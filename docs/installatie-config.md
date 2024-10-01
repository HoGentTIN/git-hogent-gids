# Git installeren en configureren

## Installatie

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

## Basisconfiguratie

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

