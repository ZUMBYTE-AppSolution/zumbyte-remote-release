# Server ohne Docker starten

Das Serverpaket benötigt **Node.js 24**. Es enthält die Anwendung und ihre Laufzeitabhängigkeiten; eine Paketinstallation ist nicht nötig.

1. `ZumbyteRemote-Server-0.2.0-alpha.2.tar.gz` vollständig entpacken.
2. Einen eigenen dauerhaften Datenordner anlegen.
3. Im entpackten Ordner `runtime` die folgenden Einstellungen setzen und den Launcher starten.

Unter Linux oder macOS:

```sh
export DATA_DIR=/pfad/zu/zumbyte-remote-data
export PUBLIC_URL=https://remote.meine-domain.de
export HOST=127.0.0.1
export PORT=8787
export AUTO_UPDATE=false
node apps/launcher/server.mjs
```

Unter Windows in PowerShell:

```powershell
$env:DATA_DIR = 'D:\ZumbyteRemote-Daten'
$env:PUBLIC_URL = 'https://remote.meine-domain.de'
$env:HOST = '127.0.0.1'
$env:PORT = '8787'
$env:AUTO_UPDATE = 'false'
node apps/launcher/server.mjs
```

Den HTTPS-Reverse-Proxy auf den internen Port 8787 richten und WebSocket-Verbindungen erlauben. Der Launcher muss für die Nutzung laufen. Einen automatischen Prozessstart bei Bedarf über den Dienstmanager des jeweiligen Servers einrichten. Der Windows-Systemdienst der Desktop-App ist der Fernzugriffs-Zielteil; er ersetzt diesen zentralen Server nicht.

Beim ersten Aufruf deiner HTTPS-Adresse ein Administratorkonto erstellen. Der einmalige Code liegt unter `setup-token.txt` im gewählten Datenordner und wird danach gelöscht. Weitere Konten legst du unter **Benutzer** an.

Mit `AUTO_UPDATE=true` darf der Launcher signierte Anwendungsversionen automatisch übernehmen. Sonst erfolgt die Installation über **Updates → Eigener Server**. Der Datenordner muss für Konten, Datenbank und Updateordner beschreibbar bleiben. Zum Sichern den Launcher beenden und den gesamten Datenordner kopieren. [Mehr zu Updates](UPDATES.md).
