# Updates ohne GitHub-API

## Ablauf

1. Öffentlichen Atom-Feed lesen; keine API-Anmeldung und kein GitHub-Token.
2. Höchste passende stabile oder Vorabversion bestimmen.
3. `update.json` und `update.sig` direkt vom Versionstag laden.
4. Beschreibung mit dem fest eingebauten Ed25519-Schlüssel prüfen.
5. Paket laden, Größe und SHA-256 prüfen.
6. Passenden Windows-/Mac-Installer starten oder neue Serverlaufzeit vorbereiten.

Der reguläre Prüfzyklus beträgt sechs Stunden. ETags und ein lokaler Prüfstand vermeiden unnötige Abrufe. Eine fehlgeschlagene Prüfung oder ein ungültiges Paket lässt die laufende Version bestehen.

## Windows

Unter **Updates → Desktop-App** prüfen und installieren. Die App beendet sich dafür; Windows kann Administratorbestätigung verlangen. Der Installer erhält die vorherigen Dateien unter `<Installationsordner>.previous`. Bestehende Dienstschlüssel und Gerätezuordnung bleiben erhalten.

Die Pakete sind derzeit nicht mit einem Authenticode-Zertifikat signiert. Die eingebaute Updatefunktion verwendet einen eigenen kryptografischen Prüfschlüssel. Einen manuell heruntergeladenen ersten Installer über die offizielle Repository-Adresse beziehen.

## macOS

Die App lädt das PKG für Intel oder Apple Silicon und prüft dieselbe Ed25519-Updatebeschreibung sowie SHA-256. Der macOS-Installer übernimmt die Installation in den Programme-Ordner. Ein eingerichteter Benutzer-LaunchAgent wird vorübergehend gestoppt und beim nächsten Appstart wiederhergestellt. Profile und Gerätezuordnung liegen außerhalb der App. Die Pakete sind noch nicht mit einer Apple-Developer-ID signiert oder notarisiert; die Update-Signatur ersetzt diese Apple-Signatur nicht. Siehe [Mac-Anleitung](MACOS.md).

## Server und Unraid

Start über `apps/launcher/server.mjs`; der Container verwendet denselben Launcher. `AUTO_UPDATE=true` aktiviert automatische Anwendungsupdates. Bei `false` werden Updates über die Administratoroberfläche installiert. `/data/updates` muss dauerhaft beschreibbar sein.

Neue Laufzeiten liegen getrennt von Datenbank und Konten unter `/data/updates/runtimes`. Der Launcher prüft ihren Start und kehrt bei einem Fehlstart zur bisherigen Laufzeit zurück. Der aktive Pfad bleibt über Containerneustarts erhalten. Das Containerdateisystem braucht keine Schreibfreigabe, der Docker-Socket wird nicht benötigt.

Das betrifft die Anwendung im Container. Für Änderungen der Node.js-/Linux-Basis ein neues Container-Image verwenden und denselben Appdata-Ordner erhalten.

## ServerDesk-Plugin

Die verfügbaren Plugin-Pakete liegen im offiziellen [Plugin-Katalog](https://github.com/ZUMBYTE-AppSolution/serverdesk-plugins). Installation und Aktualisierung übernimmt eine kompatible ServerDesk-Version. Die selbstständige Remote-App aktualisiert keine ServerDesk-Installation.
