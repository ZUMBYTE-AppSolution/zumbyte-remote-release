# Updates ohne GitHub-API

## Ablauf

1. Öffentlichen Atom-Feed lesen; keine API-Anmeldung und kein GitHub-Token.
2. Höchste passende stabile oder Vorabversion bestimmen.
3. `update.json` und `update.sig` direkt vom Versionstag laden.
4. Beschreibung mit dem fest eingebauten Ed25519-Schlüssel prüfen.
5. Paket laden, Größe und SHA-256 prüfen.
6. Passendes Windows-, Mac- oder Linux-Paket installieren oder die neue Serverlaufzeit vorbereiten.

Der reguläre Prüfzyklus beträgt sechs Stunden. ETags und ein lokaler Prüfstand vermeiden unnötige Abrufe. Downloadfortschritt und Fehlermeldungen bleiben sichtbar. Unterbrochene Downloads lassen sich sicher fortsetzen; ein aktiver Download bricht nicht nach einer festen Gesamtdauer ab. Eine fehlgeschlagene Prüfung oder ein ungültiges Paket lässt die laufende Version bestehen.

## Windows

Unter **Updates** prüfen und installieren. Die App beendet sich dafür; Windows kann Administratorbestätigung verlangen. Der Installer erhält die vorherigen Dateien unter `<Installationsordner>.previous`. Bestehende Dienstschlüssel und Gerätezuordnung bleiben erhalten.

Programme, Hilfsprozesse, Installer und Uninstaller sind mit Microsoft Artifact Signing und Zeitstempel signiert. Die Updatebeschreibung wird zusätzlich mit dem eingebauten Prüfschlüssel kontrolliert. Einen manuell heruntergeladenen ersten Installer über die offizielle Repository-Adresse beziehen.

## macOS

Die App lädt das PKG für Intel oder Apple Silicon und prüft dieselbe Ed25519-Updatebeschreibung sowie SHA-256. Der macOS-Installer übernimmt die Installation in den Programme-Ordner. Ein eingerichteter Benutzer-LaunchAgent wird vorübergehend gestoppt und beim nächsten Appstart wiederhergestellt. Profile und Gerätezuordnung liegen außerhalb der App. App und Installer sind mit Developer ID signiert und bei Apple notarisiert. Siehe [Mac-Anleitung](MACOS.md).

## Linux

Eine DEB-Installation lädt das signiert beschriebene Paket und bittet über die Paketverwaltung um die Installation. Die portable Ausgabe prüft das neue TAR.GZ-Paket und wechselt anschließend auf den neuen Programmordner. Bei einem Fehlstart bleibt die bisherige Ausgabe erhalten. Die Geräteidentität und Einstellungen liegen außerhalb der ausgetauschten Programmdateien. Siehe [Linux-Anleitung](LINUX.md).

## Server und Unraid

Das Image enthält den gemeinsamen Updater mit Downloadfortschritt, Geschwindigkeit und Restzeit für Anwendungsupdates.

In Unraid als Repository **`ghcr.io/zumbyte-appsolution/zumbyte-remote-server:alpha`** verwenden. Danach unter **Docker → Auf Updates prüfen → Update** das vollständige Image aktualisieren. Das erneuert auch Node.js, die Linux-Basis und den Updater. Feste Versionstags wechseln nicht automatisch zur nächsten Version. [Umstieg und Einrichtung](UNRAID.md).

Die Administratoroberfläche bietet zusätzlich signierte Anwendungsupdates. `AUTO_UPDATE=true` installiert diese automatisch; mit `false` werden sie manuell unter **Updates → Eigener Server** gestartet. Neue Unraid-Vorlagen verwenden `false`. Vorhandene Einstellungen bleiben erhalten.

Konten, Geräte und Laufzeiten liegen dauerhaft in Appdata. Bei einem Imagewechsel wird die mitgelieferte Version verwendet, wenn sie gleich alt oder neuer ist. Eine bereits neuere signierte Serverlaufzeit bleibt erhalten. Ein fehlgeschlagenes Anwendungsupdate kehrt zum vorherigen Stand zurück.

Weder Docker-Socket noch privilegierter Modus sind nötig. App und Server verwenden öffentliche Release-Dateien; Unraid verwendet die öffentliche Containerregistry. Laufende Updates benötigen weder GitHub-REST-API noch persönlichen Token.

## ServerDesk-Plugin

Die verfügbaren Plugin-Pakete liegen im offiziellen [Plugin-Katalog](https://github.com/ZUMBYTE-AppSolution/serverdesk-plugins). Installation und Aktualisierung übernimmt eine kompatible ServerDesk-Version. Die selbstständige Remote-App aktualisiert keine ServerDesk-Installation.
