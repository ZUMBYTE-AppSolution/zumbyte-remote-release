# Updates

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

Programme, Hintergrunddienst und Installer sind digital signiert. Windows zeigt **Andreas Zumbansen** als verifizierten Herausgeber. Einen manuell heruntergeladenen Installer immer aus dem offiziellen Release beziehen.

## macOS

Die App lädt den passenden PKG-Installer für Intel oder Apple Silicon. Zusätzlich zur Updatebeschreibung und SHA-256 werden ab Alpha 5 die Apple-Signatur und die Freigabe des Installers geprüft. App und Downloads sind mit Developer ID signiert und von Apple notarisiert.

Der macOS-Installer übernimmt die Installation in den Programme-Ordner. Ein eingerichteter Benutzer-Hintergrunddienst wird für die Aktualisierung angehalten und beim nächsten Appstart wiederhergestellt. Lässt sich der Installer nicht öffnen, läuft die vorhandene App weiter. Profile und Gerätezuordnung bleiben erhalten. [Mac-Anleitung](MACOS.md).

**Ältere Mac-Version ohne Fortschrittsanzeige:** Wenn das Update wiederholt abbricht, lade den passenden PKG-Installer von der [Release-Seite](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases) und öffne ihn einmal direkt. Eine Deinstallation ist dafür nicht erforderlich.

## Fortschritt und Fehler ab Alpha 5

Neue zRemote-Builds zeigen den Downloadfortschritt mit Geschwindigkeit und geschätzter Restzeit. Danach folgt die Paketprüfung. Unterbrochene Downloads werden automatisch erneut versucht und nach Möglichkeit fortgesetzt. Ein Fehler bleibt mit einer Möglichkeit zum erneuten Versuch sichtbar.

Ein laufender Download wird auch bei langsamer Verbindung nicht nach drei Minuten abgebrochen. Die neue Anzeige ist ebenfalls im aktualisierten Server enthalten, einschließlich Docker und Unraid.

## Server und Unraid

Das aktuelle öffentliche Image enthält **0.3.0 Alpha 5**, einschließlich Downloadfortschritt, Geschwindigkeit und Restzeit für Anwendungsupdates.

In Unraid als Repository **`ghcr.io/zumbyte-appsolution/zumbyte-remote-server:alpha`** verwenden. Danach unter **Docker → Auf Updates prüfen → Update** das vollständige Image aktualisieren. Das erneuert auch Node.js, die Linux-Basis und den Updater. Feste Versionstags wechseln nicht automatisch zur nächsten Version. [Umstieg und Einrichtung](UNRAID.md).

Die Administratoroberfläche bietet zusätzlich signierte Anwendungsupdates. `AUTO_UPDATE=true` installiert diese automatisch; mit `false` werden sie manuell unter **Updates → Eigener Server** gestartet. Neue Unraid-Vorlagen verwenden `false`. Vorhandene Einstellungen bleiben erhalten.

Konten, Geräte und Laufzeiten liegen dauerhaft in Appdata. Bei einem Imagewechsel wird die mitgelieferte Version verwendet, wenn sie gleich alt oder neuer ist. Eine bereits neuere signierte Serverlaufzeit bleibt erhalten. Ein fehlgeschlagenes Anwendungsupdate kehrt zum vorherigen Stand zurück.

Weder Docker-Socket noch privilegierter Modus sind nötig. App und Server verwenden öffentliche Release-Dateien; Unraid verwendet die öffentliche Containerregistry. Laufende Updates benötigen weder GitHub-REST-API noch persönlichen Token.

## ServerDesk-Plugin

Die verfügbaren Plugin-Pakete liegen im offiziellen [Plugin-Katalog](https://github.com/ZUMBYTE-AppSolution/serverdesk-plugins). Installation und Aktualisierung übernimmt eine kompatible ServerDesk-Version. Die selbstständige Remote-App aktualisiert keine ServerDesk-Installation.
