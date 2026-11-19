# zRemote auf Unraid

Das Containerimage enthält **0.3.0 Alpha 5** mit Downloadfortschritt für Serverupdates. [Downloads](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases/tag/v0.3.0-alpha.5)

## Vorhandenen Container umstellen

1. In Unraid unter **Docker** den zRemote-Container bearbeiten.
2. Im Feld **Repository** genau `ghcr.io/zumbyte-appsolution/zumbyte-remote-server:alpha` eintragen.
3. Netzwerk, feste IP, Appdata-Pfad und eigene Einstellungen beibehalten. Bei einer eigenen br0-Adresse bleibt diese Adresse bestehen.
4. **Anwenden** wählen. Unraid lädt das Image und erstellt den Container mit demselben Datenordner neu.

Danach laufen weitere Imageupdates über **Docker → Auf Updates prüfen → Update**. Der Kanal **alpha** zeigt jeweils auf das neue geprüfte Alpha-Image. Ein festes Versionstag wie `:0.3.0-alpha.5` und ein nur lokal importiertes Image verfolgen diesen Kanal nicht.

Konten, Computer und Gerätezuordnungen bleiben im vorhandenen Appdata-Ordner. Diesen Ordner nicht löschen und keine neue Ersteinrichtung starten. Vor dem Umstieg empfiehlt sich eine Sicherung bei gestopptem Container.

## Neu installieren

Das öffentliche Image benötigt keine Anmeldung:

```sh
docker pull ghcr.io/zumbyte-appsolution/zumbyte-remote-server:alpha
mkdir -p /mnt/user/appdata/zumbyte-remote
chown 99:100 /mnt/user/appdata/zumbyte-remote
chmod 700 /mnt/user/appdata/zumbyte-remote
```

Bei einem vorhandenen Datenordner dessen Inhalt und Rechte prüfen. Die Befehle löschen keine Daten.

1. [Die Unraid-Vorlage](../templates/zumbyte-remote.xml) als `/boot/config/plugins/dockerMan/templates-user/my-zumbyte-remote.xml` ablegen.
2. Unter **Docker → Container hinzufügen** die Vorlage **zumbyte-remote** wählen.
3. Die eigene HTTPS-Adresse unter **Öffentliche Adresse** eintragen.
4. Appdata und Port kontrollieren. Die Vorlage verwendet UID 99/GID 100, ein schreibgeschütztes Dateisystem und keine zusätzlichen Rechte.
5. Den HTTPS-Reverse-Proxy auf **HTTP**, Container-IP und Port **8787** einstellen; WebSockets aktivieren. Bei bridge wird der veröffentlichte Port der Unraid-IP verwendet, bei br0 die eigene Container-IP.
6. Für den direkten Verbindungsaufbau aus dem Internet zusätzlich UDP **3478** an den Container weiterleiten. Der Server stellt die Verbindung her; Bild, Eingaben und Dateien laufen direkt zwischen den Geräten. Ein eigener TURN-Relay ist nicht erforderlich und wird nicht als Ersatzverbindung benutzt.

Der Container benötigt weder privilegierten Modus noch Docker-Socket. Der WebUI-Link öffnet den internen HTTP-Port; für die Einrichtung und den täglichen Zugriff die konfigurierte HTTPS-Adresse verwenden.

## Erstes Konto und Geräte

Einrichtungscode auslesen:

```sh
docker exec zumbyte-remote cat /data/setup-token.txt
```

Auf der eigenen HTTPS-Adresse den Code eingeben und das erste Administratorkonto mit einem Passwort aus mindestens zwölf Zeichen anlegen. Anschließend wird der Code gelöscht. Weitere Konten werden unter **Benutzer** angelegt; jedes Konto sieht seine eigenen Computer.

In der Desktop-App dieselbe Serveradresse eintragen und anmelden. Unter **Dieser Computer** die App oder den Hintergrunddienst zuordnen. Für Windows-Zugriff vor der Benutzeranmeldung den Systemdienst einrichten. Windows-Anmeldedaten werden nicht gespeichert.

## Zwei Updatewege

**Unraid aktualisiert das vollständige Image:** Im Docker-Tab auf Updates prüfen und das Update des zRemote-Containers ausführen. So werden auch Node.js, die Linux-Basis und der Updater erneuert. Der Downloadfortschritt erscheint im Unraid-Updatefenster.

**Die Serveroberfläche aktualisiert die Anwendung:** Unter **Updates → Eigener Server** lassen sich zusätzliche signierte Serverpakete installieren. Dabei werden Prozent, geladene Datenmenge, Geschwindigkeit und Restzeit angezeigt. Unterbrochene Downloads werden erneut versucht; Fehler bleiben sichtbar. Laufende Fernverbindungen verschieben den Austausch.

Neue Vorlagen verwenden `AUTO_UPDATE=false`; damit übernimmst du neue Images bewusst über Unraid. Mit `true` werden zusätzlich Anwendungsupdates automatisch geladen. Vorhandene Einstellungen bleiben beim Imagewechsel erhalten. Die Serveroberfläche zeigt auch die im Image enthaltene Version.

Eine neuere oder gleich alte Imageversion ersetzt eine ältere gespeicherte Laufzeit. Eine bereits neuere Serverlaufzeit bleibt erhalten. Bei einem fehlgeschlagenen Anwendungsupdate startet wieder der vorherige Stand.

Die Anwendung liest den öffentlichen Release-Feed und prüft Signatur und SHA-256. Unraid lädt öffentliche Images über die Containerregistry. Beides benötigt weder GitHub-Konto noch persönlichen Token; die GitHub-REST-API wird für laufende Updates nicht verwendet.

## Ohne Registry oder mit Compose

Das fertige Imagearchiv lässt sich mit `docker load --input ZumbyteRemote-DockerImage-0.3.0-alpha.5-linux-amd64.tar.gz` importieren. Es enthält das feste Versionstag. Für spätere Updates durch Unraid trotzdem den Kanal `:alpha` als Repository eintragen und einmal aus der Registry laden.

Das Docker-Paket enthält Compose, Beispielkonfiguration und Unraid-Vorlage. In der entpackten Konfiguration Domain, Appdata, UID/GID und Bind-Adresse anpassen. Dann:

```sh
docker compose --env-file .env -f compose.yaml pull
docker compose --env-file .env -f compose.yaml up -d
```

## Sicherung

Für eine Dateisicherung den Container stoppen und den gesamten Appdata-Ordner einschließlich `updates` sichern. Bei Wiederherstellung denselben Ordner und dieselbe UID/GID verwenden. Private Geräteschlüssel bleiben auf den jeweiligen Computern.

Die Dateien für Community Apps sind vorbereitet; die Aufnahme in den Katalog erfordert eine gesonderte Einreichung und Prüfung. [Community Apps](COMMUNITY-APPS.md)
