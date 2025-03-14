# Typischer Aufbau meines persönlichen Setups

## Aufbau des Verzeichnisbaums unterhalb von Home

Quellcode unter `~/src/`, danach Unterverzeichnis je nach Programmiersprache, z.B. `~/src/python`
Temporärer Dateien unter `~/temp/``

## Virtuelle Umgebungen für Python

immer als venv-Verzeichnis unterhalb des Projekts anlegen
find ~/src/ -type d -name "venv"

## Customizing der Shell

* iTerm2 installieren

* Fish installieren (z.B. über Homebrew `brew install fish`) https://fishshell.com/

* OMF-Package-Manager installieren `curl -L https://get.oh-my.fish | fish``
* Fisher Package Manager https://github.com/jorgebucaran/fisher
* Tide installieren https://github.com/IlanCosman/tide
* Agnoster-Theme für fish installiern `omf install agnoster`
* https://github.com/IlanCosman/tide#fonts MesloLGS NF Regular.ttf installieren und für iTerm2 aktivieren

* zur Standard-Shell machen (geht nur unter bash/zsh so)
```
echo $(eval which fish) | sudo tee -a /etc/shells
chsh -s `which fish`
```
* beim i386/ARM-Mischbetrieb bieten sich zwei iTerm2 an, ein ARM und eins x64
* in beide Homebrew installieren, was funktioniert, da je nach Architektur verschiedene Pfade genutzt werden, bei ARM:/opt/homebrew/bin bei Intel: /usr/local/bin)
* Architektur-spezifisches Config-Skript erstellen (in diesem Fall wird bei ARM automatisch fish als Shell gestartet)
```
r=$(eval uname -p)
if [[ "$r" == "arm" ]]
then
    echo "Using ARM Homebrew"
    eval "$(/opt/homebrew/bin/brew shellenv)"
    fish
else
    echo "Using Intel Homebrew"
    eval "$(/usr/local/bin/brew shellenv)"
fi
```
* beide Homebrew-Installationen sind dann komplett voneinander unabhängig


Für zsh mit Oh my Zsh ähnlich verfahren
* https://ohmyz.sh/#install

## Customizing VisualStudio Code

* Settings.Features-Terminal Font Family auf "Meslo LG S for Powerline" setzen

* Cmd+Shift+P "shell command" damit man den code-Befehl in der Kommandozeile hat (praktisch, um VS Code aus dem Terminal zu starten) sieh [Doku](https://code.visualstudio.com/docs/setup/mac)