![Einrichtung eines Arbeitsplatzes für das Informatik-Studium](./img/header.png)
# Einrichtung eines Arbeitsplatzes für das Informatik-Studium

Den Anstoß für die Idee ein solches Tutorial zu erstellen, lieferte [Felix Rieseberg](https://github.com/felixrieseberg/windows-development-environment).

## Einleitung

### Thematische Schwerpunkte

Im Rahmen des Tutorials entsteht ein Arbeitsplatz mit dem die typischerweise in 2020/2021 genutzten Entwicklungstechnologien und Werkzeuge genutzt werden können.
Aus Sicht des Autors sind dies:
* Paketverwaltungswerkzeuge
* Git
* Visual Studio Code
* Bash und das Windows Subsystem for Linux
* Wichtige Kommandozeilenwerkzeuge (curl, wget etc.)
* Virtuelle Maschinen und Containervirtualisierung
* VPN-Clients
* Werkzeuge zum Datenaustausch mittels SFTP und SCP
* SQL-Clients (geplant)

Der Fokus des Tutorials ist es, unter Windows 10 arbeitsfähig zu werden.
Linux- und Mac-Nutzer*innen benötigen die Sektion zum Thema "Bash und das Windows Subsystem for Linux" nicht, da ihnen diese Funktionalität bereits über das Terminal zur Verfügung steht.

### Ein Vorwort zur englischen Sprache

Eine langfristige Beschäftigung mit dem Feld der Informatik ohne (zumindest) der Fähigkeit, englische Texte lesen zu können, ist wenig sinnvoll. Auch wenn regelmäßig deutsche Fachliteratur erscheint, ist die primäre Publikationssprache Englisch. Der Vorteil der Publikationen in der Informatik ist jedoch, dass diese meistens formal sehr ähnlich aufgebaut sind, was deren Lesbarkeit erhöht.

Selbst wenn man keine wissenschaftliche Karriere anstrebt, ist zu bedenken, dass die Dokumentation fast jeder Open-Source-Software auf Englisch vorliegt. Außerdem sollten Sie auch zu Beginn Ihres Studiums bemerkt haben, dass eigentlich jeder Fachbegriff englisch ist.

Da dieses Tutorial Ihnen einen ersten Einstieg vermitteln soll, wurde es auf Deutsch verfasst. Regelmäßig werden jedoch englische Quelle verlinkt.

## Paketverwaltungswerkzeuge

Unter Paketverwaltungswerkzeugen oder _Package Managern_ versteht man Werkzeuge, welche die Installation, Konfiguration und Deinstallation von Software-Paketen vereinfacht und vereinheitlicht. Typischerweise integrieren Package Manager auch noch einen Mechanismus zur Auflösung von Softwareabhängigkeiten. Das heißt, das der Package Manager Abhängigkeiten von Programmbibliotheken erkennt und fehlende Programmpakte automatisiert nachinstalliert. Voraussetzung für die Verwendung eines Package Managers ist, dass ein Programm als Packet im vom Package Manager verstanden Format und in einem Repository vorliegt.Traditionell sind Package Manager auf Linux- oder BSD-basierten Betriebssystemen üblich.

Sie haben sich mittlerweile jedoch auch auf weiteren Plattformen durchgesetzt und erleichtern den Umgang, gerade mit Open-Source-Software, enorm, da auch komplexe Softwarepakete mit wenigen Befehlen installiert werden können.

### Paketverwaltung unter Windows

Seit Windows 10 gibt es eine in Windows integrierte Paketverwaltung namens _OneGet_, für die aber bisher kaum Pakete existieren.
Eine gut einsetzbare Lösung für Windows ist [Chocolatey](https://chocolatey.org/).

Nach der erfolgreichen Installation von Chocolatey lässt sich mittels Kommandozeile z.B. der bekannte Medienplayer [VLC](https://www.videolan.org/vlc/index.de.html) einrichten:
```
choco install vlc
```
### Paketverwaltung unter MacOS

Unter MacOS existieren verschiedene Lösungen wie [Fink](https://finkproject.org/index.php?phpLang=de), [MacPorts](https://www.macports.org/) oder [Homebrew](https://brew.sh/index_de). Der Vorteil der letztgenannten Lösung liegt darin, dass sich Software auch ohne Administratorenrechte installieren lässt.

Die Installation von Git mittels Homebrew geschieht im Terminal wie folgt:
```
brew install git
```

### Paketverwaltung unter Linux

Der konkrete Package Manager hängt von der verwendeten Linux-Distribution ab. In Debian-basierten Distributionen, wie z.B. Ubuntu, ist dies das Advanced Packaging Tool (APT).

Der Webserver [nginx](https://www.nginx.com/) lässt sich damit vergleichbar einfach installieren.
```
apt-get install nginx
```

## Installation von Git
Das Arbeiten ohne eine Versionscontrolle ist möglich, aber sinnlos (frei nach Loriot). Aktuell ist Git das wohl am weitesten verbreitete Kommandozeilentool aus diesem Bereich. Sie werden es auch benötigen, um Beispielcode oder Programme von GitHub oder GitLab herunterzuladen bzw. um Repositories zu clonen.

### Windows
Die Installationsdateien für Windows können Sie [hier](https://git-scm.com/download/win) herunterladen.

Alternativ können Sie _chocolatey_ nutzen:
```
choco install git
```

### MacOS

Wenn Sie Xcode bereits installiert haben, verfügen Sie über eine lauffähige Git-Installation.

Alternativ bietet sich die Installation mittels Homebrew an:
```
brew install git
```

### Linux
Unter einem Debian-basierten Linux installieren Sie Git wie folgt:
```
apt-get install git
````

### Weiterführende Dokumentation 
* [Generelle Dokumentation zu Git (engl.)](https://git-scm.com/doc)
* [Pro Git eBook (engl.) - HTML, PDF und ePub](https://git-scm.com/book/en/v2)
* [Einführungsvideos zu Git (engl.)](https://git-scm.com/videos)
* [GitHubs Git Cheat Sheet (engl.)](https://training.github.com/downloads/github-git-cheat-sheet.pdf)


### Git-GUI-Clients

Die [Git-Website](https://git-scm.com/downloads/guis) listet aktuelle GUI-Clients für Git auf, wenn Sie die Kommandozeile scheuen.

Sollten Sie Visual Studio Code installieren, benötigen Sie prinzipiell keine separate Git-GUI-Installation, da der Editor alles direkt unterstützt. Git per GUI steht dann aber nur dort zur Verfügung.

## Installation von Visual Studio Code

Microsofts Visual Studio Code (VS Code) ist ein mächtiger Quellcode-Editor, der sich durch eine Vielzahl an Plugins an die eigenen Bedürfnisse, wie z.B. die verwendete Programmiersprache, anpassen lässt. VS Code ist zum [Download für Windows, Linux und MacOS](https://code.visualstudio.com/) verfügbar.

Markdown-Preview `Ctrl/Cmd+K V`
### Sinnvolle Plugins

VS Code ist bereits in seiner Grundinstallation recht mächtig und unterstützt den Umgang mit Markdown oder Git.

Der [Marketplace](https://marketplace.visualstudio.com/vscode) stellt den ersten Anlaufpunkt für die Suche nach Plugins dar.

* Rechtschreibkontrolle
    1. [Code Spell Checker installieren](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
    1. [Deutsches Sprachpaket für Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker-german)
    1. Die Rechtschreibkontrolle kann dann mittels Druck auf `F1` und Eingabe von `Enable German Spell Checker Dictionary` in die erscheinende Command Palette aktiviert werden (Alternativ per Menu: View-Command Palette...)

to do
* [Git History](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory)

* [Path Autocomplete](https://marketplace.visualstudio.com/items?itemName=ionutvmi.path-autocomplete)

* [Automatisierte Erzeugung von Inhaltsverzeichnissen für Markdown-Dokumente](https://marketplace.visualstudio.com/items?itemName=AlanWalk.markdown-toc)

### Relevante Einstiegspunkte in die Dokumentation von VS Code

* [Using Version Control in VS Code](https://code.visualstudio.com/docs/editor/versioncontrol)
* [Markdown and Visual Studio Code](https://code.visualstudio.com/docs/languages/markdown)

## Bash und das Windows Subsystem for Linux

Ein großer Teil von Open Source Software wird unter [Linux](https://de.wikipedia.org/wiki/Linux) entwickelt und betrieben, von daher ist es sehr wahrscheinlich, dass Sie (mindestens) einmal in Ihrem Studium mit Linux konfrontiert werden. Um eine [Linux-Distribution](https://de.wikipedia.org/wiki/Linux-Distribution) zusätzlich zu Windows in Betrieb zu nehmen, haben Sie im Wesentlichen drei Möglichkeiten:

1. Dual-Boot-Installation, d.h. sie entscheiden zum Bootzeitpunkt, in welches Betriebssystem Sie booten wollen
1. Nutzung der Windows Subystem for Windows, Cygwin o.ä.
1. Betrieb von Linux in einer virtuellen Maschine (siehe unten)

### Windows Subsystem for Linux

Seit Windows 10 besteht die Möglichkeit, Linux-Distributionen wie Ubuntu direkt nutzbar zu installieren. Hierfür ist es nötig, das Windows Subsystem for Linux (WSL) zu installieren, was Microsoft gut [dokumentiert](https://docs.microsoft.com/de-de/windows/wsl/install-win10).

Nach der Auswahl einer Linux-Distribution aus dem Microsoft Store, erhalten Sie eine weitestgehend komplette Linux-Umgebung, welche Sie ohne Reboot nutzen können.

### Cygwin

Vor Windows 10 war [Cygwin](https://cygwin.com/) die einzige Möglichkeit das "Linux feeling - on Windows" (Eigenaussage Cygwin) zu erleben. Cygwin bundelt eine Vielzahl an GNU- und Open-Source-Tools, u.a. die [Bash](https://www.gnu.org/software/bash/).

### Cmder

Bei [Cmder](https://cmder.net/) handelt es sich um einen Console Emulator der nach Aussage des Autors aus reiner Frustration über die Abwesenheits eines solchen Tools unter Windows entstand. In der Vollversion enthält Cmder sowohl Git als auch eine Vielzahl an häufig genutzten Linux-Befehlen.

In Kombination mit dem WSL (siehe oben), welches Sie direkt aus Cmder mittels dem Befehl `bash` starten können, erhalten Sie ein leistungsfähiges Terminal wie man es aus Linux oder MacOS kennt.

### SSH-Clients

Wenn Sie sich nur mit einem Linux-Server (oder einer virtuellen Maschine) per SSH (siehe unten) verbinden möchten, bietet sich unter Windows die Nutzung von [Putty (Open Source)](https://www.putty.org/) oder [MobaXTerm](https://mobaxterm.mobatek.net/), wobei letzteres eine etwas zeitgemäßere Benutzerschnittstelle bietet und in einer kostenfreien Version erhältlich ist.


### Wichtige Kommandozeilenwerkzeuge

Der Heise-Verlag stellt eine Übersicht über die [20 wichtigsten Linux-Kommandos](https://www.heise.de/tipps-tricks/Linux-Befehle-Die-20-wichtigsten-Kommandos-3843388.html) bereit. Neben diesen Basisbefehlen, gibt es noch weitere Programme, die Sie höchst wahrscheinlich in der Kommandozeile nutzen werden, wenn Sie mit Web-basierten Softwaresystemen, z.B. mittels [REST-APIs](https://de.wikipedia.org/wiki/Representational_State_Transfer), kommunizieren müssen.

#### man

Mittels `man <befehl>` können Sie zu vielen Befehlen, die Sie noch nie gehört haben im Terminal Hilfe erhalten. In der Hilfsseite scrollen Sie mithilfe der Cursortasten, zum Beenden tippen sie `q`.
#### ssh

`ssh` ist der SSH-Client, den Sie nutzen, um sich mit Servern oder sonstigen entfernten Rechner verbinden werden.
#### curl

Das Werkzeug `curl` dient dem Abruf von URLs. So können Sie beispielsweise Webseiten von einem Webserver ohne die Nutzung eines Browsers abrufen. Im REST-Umfeld können Sie so aber auch einfach Anfragen an Server stellen und Antworten empfangen, was das folgende Beispiel für eine Anfrage an einen [Elasticsearch](https://de.wikipedia.org/wiki/Elasticsearch)-Server illustriert:
````
curl -X GET "localhost:9200/bank/_search?pretty" -H 'Content-Type: application/json' -d'
{
  "query": { "match_all": {} },
  "sort": [
    { "account_number": "asc" }
  ]
}
'
````
Die entsprechende Antwort wird auf der Kommandozeile ausgegeben.

#### wget

Zum Herunterladen beliebiger Dateien aus dem Internet, kann `wget` genutzt werden. Außerdem ist `wget` dafür geeignet, Spiegelungen aller Dateien auf einem Webserver zu erstellen, um diese offline nutzen zu können.

### vim
Häufig werden Sie auf einem Rechner, mit dem Sie sich per SSH verbunden haben, Änderungen an Textdateien vornehmen wollen. Auf eigentlich jedem Linux-Server steht dazu der Textedior `vim` zur Verfügung. Der Editor ist ohne Zweifel sehr leistungsfähig, kann auf jüngere Computernutzer*innen jedoch abschreckend wirken.
Wenn Sie den Editor öffnen und nicht wieder beenden können: drücken sie zweimal ESC und geben Sie dann `:q!` ein.

Um die komplexen Funktionen kennenzulernen, bietet sich das Studium dieses [Tutoriums](https://www.selflinux.org/selflinux/pdf/vim.pdf) an.

### nano
Der Texteditor `nano` verbreitet sich immer mehr auf Linux-Servern und glänzt durch seine einfache Bedienung, da am unteren Ende des Bildschirms die wichtigsten Befehle eingeblendet werden. Hiermit gelingt es Ihnen relativ einfach und fast wie von einer GUI gewohnt, Texte zu editieren.

## Virtuelle Maschinen und Containervirtualisierung

### Virtuelle Maschinen

Es gibt viele kommerzielle Anbieter von Virtualisierungslösungen, für die meisten Einsatzzwecke in Ihrem Studium wird jedoch die Lösung [VirtualBox](https://www.virtualbox.org/) ausreichen. VirtualBox ist für alle Betriebssysteme verfügbar.

Mithilfe einer Virtualisierungssoftware können Sie verschiedene Betriebsysteme unter einem Host-Betriebssystem (z.B. Windows oder Linux) in einer [virtuellen Maschine (VM)](https://de.wikipedia.org/wiki/Virtuelle_Maschine) betreiben. Das ist insofern ein Vorteil, dass Sie auf Ihrem Rechner auch weitere Betriebssysteme zu Testzwecken betreiben können und diese jederzeit in einen vorigen Zustand zurücksetzen können, da VMs zumeist auch Snapshot-Funktionen bieten, welche den Zustand einer VM zu einem bestimmten Zeitpunkt sichern.

### Containervirtualisierung

Eine leichtgewichtigere Alternative zum Einsatz von virtuellen Maschinen stellt die [Containervirtualisierung](https://de.wikipedia.org/wiki/Containervirtualisierung) dar. Bei der Containervirtualisierung werden bestimmte Ressourcen des Betriebssystems, wie z.B. das Dateisystem oder Peripheriegeräte, vor ausgeführten Programmen verborgen. Im Gegensatz zur VM ist es jedoch nicht möglich, das Betriebssystem zu virtualisieren, d.h. Container und Host-Betriebssystem bleiben gleich. Aus der Sicht der Softwareentwicklung sind Container praktisch, da sie es ermöglichen, auf einem Rechner Anwendungen zu betreiben, die isoliert voneinander, beispielsweise verschiedene Versionsstände von Programmbibliotheken nutzen. Dies wird durch die Isolierung des Dateisystems möglich.

Durch seine nutzerfreundlichen Tools hat [Docker](https://de.wikipedia.org/wiki/Docker_(Software)) der Containervirtualisierung zum Durchbruch auf weiter Front verholfen. Viele Open-Source-Werkzeuge werden auch als Docker-Image angeboten. Die notwendige Laufzeitumgebung und Konfigurationswerkzeuge für Docker können für alle Betriebssysteme [heruntergeladen](https://www.docker.com/get-started) werden.
## VPN-Clients

[Virtual-Private-Network](https://de.wikipedia.org/wiki/Virtual_Private_Network)-Clients dienen dazu, dass Sie sich von Ihrem Privatgerät aus z.B. mit dem Netzwerk Ihrer Hochschule verbinden können. Dadurch kommen Sie in die Lage, Server zu erreichen, die nur im Hochschulnetz erreichbar sind. Ein weiterer Anwendungsfall ist der Zugriff auf Ressourcen Ihrer Bibliothek, die auch meistens nur im Hochschulnetz zur Verfügung stehen, da die Verlage keinen freien Zugriff zulassen. Durch die Verbindung mittels VPN wirkt es jedoch als ob Sie aus dem Hochschulnetz auf beispielsweise ein eBook zugreifen.

Welchen VPN-Client Sie nutzen können, hängt von Ihrer Hochschule ab. Folgen diesen jedoch dem OpenVPN-Standard, können Sie aus einigen Alternativen wählen. Details dazu erhalten Sie durch das Rechenzentrum Ihrer Hochschule.

Die Wikipedia bietet einen Überblick über [VPN-Clients](https://de.wikipedia.org/wiki/OpenVPN#Windows).

## Datenaustausch mittels SFTP und SCP

Zum Datenaustausch mit entfernten Servern (oder virtuellen Maschinen) kommen häufig zwei Protokolle zum Einsatz: [SFTP](https://de.wikipedia.org/wiki/SSH_File_Transfer_Protocol) oder [SCP](https://de.wikipedia.org/wiki/Secure_Copy).
* Für SFTP bietet sich [Filezilla](https://filezilla-project.org/) an, welches für Linux, MacOS und Windows erhältlich ist.
* Zur Verwendung von (u.a.) SCP hat sich unter Windows [WinSCP](https://winscp.net/eng/download.php) durchgesetzt.
* Vergleichbare Funktionalität unter MacOS und Windows bietet [Cyberduck](https://cyberduck.io/). Hierbei ist allerdings zu beachten, dass für eine SCP-Verbindung SFTP als Verbindungstyp gewählt werden muss.
## SQL-Clients (geplant)
