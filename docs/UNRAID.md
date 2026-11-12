# Zumbyte Remote auf Unraid

Version 0.3.0-alpha.1. Alle Pakete stehen unter [Downloads](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases).

## 1. Container direkt laden

Das öffentliche Image lässt sich ohne Anmeldung laden:

```sh
docker pull ghcr.io/zumbyte-appsolution/zumbyte-remote-server:0.3.0-alpha.1
mkdir -p /mnt/user/appdata/zumbyte-remote
chown 99:100 /mnt/user/appdata/zumbyte-remote
chmod 700 /mnt/user/appdata/zumbyte-remote
```

Der Download braucht keinen GitHub-Token. Das Appdata-Verzeichnis wird unabhängig vom Image erhalten. Für ein schon vorhandenes Datenverzeichnis dessen Inhalt und Rechte prüfen; die Befehle löschen keine Daten.

Falls du ohne Registry arbeiten möchtest, liegt im Release weiterhin das fertige Imagearchiv. Mit `docker load --input ZumbyteRemote-DockerImage-0.3.0-alpha.1-linux-amd64.tar.gz` importieren. Dieses Archiv verwendet den lokalen Imagenamen `zumbyte-remote-server:0.3.0-alpha.1`; dann diesen Namen im Feld **Repository** der Vorlage eintragen.

## 2. Unraid-Vorlage verwenden

1. `templates/zumbyte-remote.xml` aus dem öffentlichen Repository oder `deploy/unraid/zumbyte-remote.xml` aus dem Docker-Paket als `/boot/config/plugins/dockerMan/templates-user/my-zumbyte-remote.xml` ablegen.
2. Unter **Docker → Container hinzufügen** die Vorlage **zumbyte-remote** wählen.
3. **Öffentliche Adresse** auf die eigene HTTPS-Domain setzen, z. B. `https://remote.meine-domain.de`.
4. Port 8787 und Appdata-Pfad kontrollieren. Die Vorlage verwendet UID 99/GID 100.
5. Den vorhandenen HTTPS-Reverse-Proxy auf `UNRAID-LAN-IP:8787` richten und WebSockets erlauben.
6. Container starten und im Browser die konfigurierte HTTPS-Adresse öffnen. Den WebUI-Link bei Bedarf ebenfalls auf diese Domain setzen; der direkte HTTP-Portlink ist nur eine Erreichbarkeitsprüfung.

Es wird kein privilegierter Container und kein Docker-Socket benötigt. Die Dateien für Community Apps liegen unter `templates/` und als `ca_profile.xml` im Repository-Stamm. [Einreichung und alle benötigten Dateien](COMMUNITY-APPS.md). Der Katalogeintrag erfordert eine gesonderte Prüfung durch Community Apps.

## Alternative: Compose oder eigener Build

Das Docker-Paket enthält einen fertig vorbereiteten Anwendungsordner und ein Dockerfile. Im entpackten Paket bauen:

```sh
docker build -t zumbyte-remote-server:0.3.0-alpha.1 .
cp deploy/.env.example deploy/.env
docker compose --env-file deploy/.env -f deploy/compose.yaml up -d
```

Vorher Domain, Appdata, UID/GID und Bind-Adresse in `.env` anpassen. Bei einem Reverse Proxy in einem anderen Container die interne Unraid-IP als `ZR_BIND_ADDRESS` setzen; ein Proxy auf dem Host kann `127.0.0.1` verwenden. Ein Caddy-Beispiel liegt im Paket.

## 3. Erstes Konto anlegen

Einmaligen Einrichtungscode auslesen:

```sh
docker exec zumbyte-remote cat /data/setup-token.txt
```

Auf der eigenen HTTPS-Adresse den Code eingeben und das erste Administratorkonto mit mindestens zwölf Zeichen Passwort anlegen. Es gibt keine voreingestellten Konten und keine öffentliche Registrierung. Nach der Einrichtung wird der Code gelöscht. Weitere Benutzer können unter **Benutzer** angelegt werden; jedes Konto sieht seine eigenen Geräte.

## 4. Windows-Geräte zuordnen

Windows-Installer starten, Serveradresse eintragen und anmelden. Unter **Dieser Computer** kann die App selbst oder der Windows-Systemdienst zugeordnet werden. Für Zugriff ohne offene App und vor der Windows-Benutzeranmeldung den Dienst verwenden.

Neue Geräte verlangen standardmäßig lokale Bestätigung. Beim Dienstgerät unter dem Zahnrad **Mein Konto: ohne weiteres Passwort** oder ein zusätzliches Gerätepasswort einstellen. Diese Änderung verlangt das zentrale Anmeldepasswort. Windows-Anmeldedaten werden nicht gespeichert; sie werden bei Bedarf direkt am Windows-Anmeldebildschirm eingegeben.

## Updates ohne GitHub-API

`AUTO_UPDATE=true` ist im Container voreingestellt und in der Unraid-Vorlage umschaltbar. Der Launcher liest den GitHub-Release-Feed, prüft Signatur und SHA-256 und aktualisiert die Serveranwendung unter `/data/updates`. Der aktive Stand bleibt auch nach einem Containerneustart erhalten. Ein fehlerhafter Start führt zur vorherigen Laufzeit zurück. Laufende Fernverbindungen verhindern den Austausch, bis sie beendet sind.

Das aktualisiert die Anwendung im Container. Für eine neue Node.js-/Linux-Basis das neue öffentliche Image laden oder das Imagearchiv aus dem Release importieren und den Container mit demselben Appdata-Ordner ersetzen. Weder bei einem normalen Anwendungsupdate noch beim Imageaustausch muss jedes Gerät neu gekoppelt werden.

Mit `AUTO_UPDATE=false` erfolgen Anwendungsupdates über **Updates → Eigener Server** in der Administratoroberfläche. Die Updateprüfung braucht keinen GitHub-Token und nutzt keine GitHub-API.

## Netzwerk

Nach außen wird die HTTPS-Adresse des eigenen Reverse Proxys verwendet. Der interne HTTP-Port 8787 bleibt im eigenen Netz. Die Windows-Dienstverbindung transportiert Bild und Eingaben über diese Verbindung. Der normale App-Zielteil nutzt WebRTC und benötigt zwischen getrennten NAT-/Firewallnetzen gegebenenfalls einen eigenen TURN-Server. Beispiele und die Variablen `TURN_URLS`/`TURN_SECRET` liegen dem Paket bei.

Ein isolierter LAN-Test ist mit `PUBLIC_URL=http://UNRAID-IP:8787`, `ALLOW_INSECURE_HTTP=true` und in der Windows-App zusätzlich `ZR_ALLOW_HTTP=1` möglich. Für den regulären Betrieb HTTPS verwenden.

## Sicherung und Wiederherstellung

Den Container für eine dateibasierte Sicherung stoppen und den gesamten Appdata-Ordner einschließlich `/updates` sichern. Bei Wiederherstellung denselben Ordner und passende UID/GID verwenden. Der Serverbackup enthält Geräte-IDs und öffentliche Schlüssel; private Windows-Geräteschlüssel bleiben auf den jeweiligen Computern geschützt gespeichert.

Die Version bleibt eine Alpha; weitere Praxistests auf Unraid stehen aus.
