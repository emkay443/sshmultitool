# SSH Multi Tool
Ein Multifunktionswerkzeug für SSH, mit Unterstützung für [Port knocking](https://en.wikipedia.org/wiki/Port_knocking), [OpenVPN](https://en.wikipedia.org/wiki/OpenVPN) und [Unison](https://en.wikipedia.org/wiki/Unison_(file_synchronizer))!

Dieses Programm ist in Bash geschrieben und besteht im Grunde genommen nur aus einer ausführbaren Datei, einem Bash-Skript, sowie den Profildateien, die in `~/.sshmultitool` gespeichert werden.    
Das Skript verwendet die Programme des [OpenSSH-Pakets](http://www.openssh.com) sowie [knockd](https://github.com/jvinet/knock). Beide Softwarepakete sollten in den Repositories aller größeren GNU/Linux-Distributionen enthalten sein.

Das Programm muss nicht kompiliert, sondern lediglich in einen Ordner, der in `$PATH` steht (z.B. `/usr/local/bin` oder `$HOME/bin`), kopiert werden. Dafür kann auch das `Makefile` (siehe [Installation](#installation)) verwendet werden.

SSH Multi Tool ist [freie Open Source Software](https://fsfe.org/about/basics/freesoftware.de.html) und steht unter der [GPL V3](https://www.gnu.org/licenses/gpl-3.0.de.html) (siehe [Lizenz](#lizenz)).

## Funktionen
* Verbinden zu entfernten Rechnern via SSH
* Dateiaustausch via SCP, SFTP und SSHFS
* Aufbau von SSH-Tunneln
* Automatisches "Anklopfen" an einem mit knockd gesicherten Rechner
* Automatisches Verbinden mit einem OpenVPN-Server
* Profile (mehrere Server mit eigener Konfiguration können gespeichert werden)
* Synchronisation mit Unison über SSH
* Zwei Interfaces: ncurses (semigrafisch) und command-line
* Automatische Updates

## Voraussetzungen
* Bash
* OpenSSH sowie sshfs (optional, aber empfohlen)
* knockd (bzw. den `knock`-Client, aber der ist in der Regel bei knockd dabei)
* dialog
* wget
* make (für die Installation)
* Texteditor (Konsole oder grafisch, frei nach Belieben)
* Optional: OpenVPN, Unison

### Installation der Abhängigkeiten
#### Ubuntu/Debian/Mint
`sudo apt-get install bash openssh-client sshfs knockd dialog wget vim nano make`

#### Arch
`sudo pacman -S bash openssh sshfs knockd dialog wget vim nano make`

#### Cygwin (mit [apt-cyg](https://github.com/transcode-open/apt-cyg))
```
apt-cyg install bash openssh dialog wget vim nano unzip
wget http://www.zeroflux.org/proj/knock/files/knock-cygwin.zip
unzip knock-cygwin.zip
mv knock_client/windows-cmd/knock.exe /bin/knock.exe
```    
Alternativ können die im oberen Befehl genannten Pakete auch manuell über den [Cygwin-Installer](https://cygwin.com/install.html) installiert werden, ohne `apt-cyg`.

### Unterstützte Betriebssysteme
* GNU/Linux (getestet auf Debian, Ubuntu und Arch)
* Mac OS X (mit [MacPorts](https://www.macports.org/))
* Windows (mit [Cygwin](https://www.cygwin.com/))

## Changelog
* 2015-12-22
  * Verschiebung von `$HOME/.homeconnect` zu `$HOME/.sshmultitool` ist jetzt optional (mit Symlinks zu den alten Verzeichnissen)
* 2015-12-20
  * Projekt auf github verschoben
  * Umbenannt in "SSH Multi Tool"

## Installation
### Automatisch
```
git clone https://github.com/emkay443/sshmultitool.git    
cd sshmultitool    
make
```

Führen Sie `sudo make install` statt `make` aus, wenn Sie das Programm systemweit, in `/usr/local/bin`, installieren wollen.    
Wenn Sie zusätzlich Autovervollständigung in Bash haben möchten, führen Sie zusätzlich `make bashcompletion` (bzw. mit `sudo` für systemweite Autovervollständigung) aus.

### Arch Linux User Repository (AUR)
`sshmultitool` ist jetzt im *Arch User Repository* enthalten und kann mit einem [AUR helper](https://wiki.archlinux.org/index.php/AUR_helpers) oder manuell, mit der [PKGBUILD](https://aur.archlinux.org/packages/sshmultitool/) und `makepkg`, installiert werden.

### Manuell
`sshmultitool` [herunterladen](https://raw.githubusercontent.com/emkay443/sshmultitool/master/sshmultitool), ausführbar machen (`chmod +x sshmultitool`) und in einen Ordner legen, der in der `$PATH`-Variable liegt, z.B. `/usr/local/bin` oder `$HOME/bin` (bei Debian und Ubuntu standardmäßig via `$HOME/.profile` in der `$PATH`-Variable).

## Lizenz
SSH Multi Tool steht unter der [GNU General Public Licsense Version 3](https://www.gnu.org/licenses/gpl-3.0.de.html) und ist somit [freie Software](https://fsfe.org/about/basics/freesoftware.de.html).    
Das heißt, Sie dürfen das Programm frei verwenden, verändern und weiterverteilen, solange Sie die Lizenz beibehalten.    
Zudem darf dieses Programm nicht in einem Paket mit proprietärer Software "als eins" verteilt werden, da das die Grundsätze von freier Software ad absurdum führt.

Zusätzlich wäre es wünschenswert, wenn Sie stets die originalen Autoren dieses Programms erwähnen bzw. die Nennungen im Code des Skripts beibehalten.

Eine Verwendung für militärische oder sonstige Zwecke, die die freiheitliche Grundordnung oder Menschenleben, mit welcher Begründung auch immer, bedrohen, lehne ich persönlich strikt ab, verbieten kann ich es Ihnen aber nicht.
