<p align="center"><img src="assets/app-icon.png" width="128" height="128" alt="Zumbyte Remote"></p>
<h1 align="center">zRemote</h1>
<p align="center">Deine Computer über deinen eigenen Server erreichen.</p>
<p align="center"><a href="https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases/tag/v0.3.0-alpha.5">Downloads</a> · <a href="docs/UNRAID.md">Unraid</a> · <a href="docs/MACOS.md">Mac einrichten</a> · <a href="https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/issues">Hilfe und Fehler</a></p>

Melde dich an deinem eigenen Server an und öffne einen Computer aus deiner Geräteliste. Für jedes Gerät wählst du, ob eine Person vor Ort bestätigen muss, deine zentrale Anmeldung genügt oder ein zusätzliches Gerätepasswort nötig ist.

**0.3.0 Alpha 5** behebt den Installationsabbruch auf dem Mac und übernimmt gespeicherte Zugänge älterer Mac-Versionen. Updates zeigen Downloadfortschritt, Geschwindigkeit, Restzeit und sichtbare Fehlermeldungen. Windows-App, Dienst und Installer sind digital signiert; Herausgeber ist **Andreas Zumbansen**. Die Mac-Pakete sind mit Developer ID signiert und von Apple notarisiert. Gespeicherte Computer, Profile und Dienstzuordnungen bleiben bei Updates erhalten.

## Herunterladen

| Für … | Download |
|---|---|
| Windows x64 | [Installer mit Desktopverknüpfung](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases/download/v0.3.0-alpha.5/ZumbyteRemote-Setup-0.3.0-alpha.5-windows-x64.exe) · [Portable ZIP](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases/download/v0.3.0-alpha.5/ZumbyteRemote-Portable-0.3.0-alpha.5-windows-x64.zip) |
| Mac mit Apple Silicon | [PKG installieren](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases/download/v0.3.0-alpha.5/ZumbyteRemote-Setup-0.3.0-alpha.5-macos-arm64.pkg) · [DMG](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases/download/v0.3.0-alpha.5/ZumbyteRemote-0.3.0-alpha.5-macos-arm64.dmg) |
| Mac mit Intel | [PKG installieren](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases/download/v0.3.0-alpha.5/ZumbyteRemote-Setup-0.3.0-alpha.5-macos-x64.pkg) · [DMG](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases/download/v0.3.0-alpha.5/ZumbyteRemote-0.3.0-alpha.5-macos-x64.dmg) |
| Docker / Unraid | Öffentliches Image: `ghcr.io/zumbyte-appsolution/zumbyte-remote-server:alpha` · [Einrichtung](docs/UNRAID.md) |
| Unraid Community Apps | [Vorlage und Anbieterprofil](docs/COMMUNITY-APPS.md) · [Dateipaket](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases/download/v0.3.0-alpha.5/ZumbyteRemote-Unraid-CommunityApps-0.3.0-alpha.5.zip) |
| Server ohne Container | [Node.js-24-Serverpaket](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases/download/v0.3.0-alpha.5/ZumbyteRemote-Server-0.3.0-alpha.5.tar.gz) |
| Imageimport / Containerkonfiguration | [Imagearchiv Linux amd64](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases/download/v0.3.0-alpha.5/ZumbyteRemote-DockerImage-0.3.0-alpha.5-linux-amd64.tar.gz) · [Docker-/Unraid-Paket](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases/download/v0.3.0-alpha.5/ZumbyteRemote-Unraid-Docker-0.3.0-alpha.5.zip) |

[Prüfsummen für Alpha 5](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases/download/v0.3.0-alpha.5/SHA256SUMS.txt) · [Änderungen](CHANGELOG.md)

Windows-Pakete enthalten die benötigten Laufzeiten. Die Mac-Ausgabe benötigt macOS 13 oder neuer; für Bildschirmübertragung und Steuerung sind die macOS-Freigaben für Bildschirmaufnahme und Bedienungshilfen nötig. Die integrierte Updateprüfung verwendet signierte Updatebeschreibungen und SHA-256. Das Docker-Image enthält ebenfalls Alpha 5 und lässt sich über den Kanal `:alpha` direkt in Unraid aktualisieren.

## Die App

![Geräteliste](assets/screenshots/windows-dienst.png)

| Anmeldung | Diesen Computer einrichten |
|---|---|
| ![Anmeldung](assets/screenshots/anmeldung.png) | ![Computer und Hintergrunddienst](assets/screenshots/dieser-computer.png) |

Die Bilder zeigen die laufende App.

## Verbinden

1. Server starten und eine eigene HTTPS-Adresse mit WebSocket-Unterstützung einrichten.
2. Die Adresse im Browser öffnen. Den einmaligen Code aus `/data/setup-token.txt` eingeben und das erste Administratorkonto anlegen.
3. Desktop-App installieren, dieselbe Serveradresse eintragen und anmelden.
4. Unter **Dieser Computer** den Computer deinem Konto zuordnen. Er bekommt einen festen Eintrag in der Geräteliste.
5. Für unbeaufsichtigten Zugriff den Hintergrunddienst einrichten und die gewünschte Zugriffsregel wählen.

Weitere Konten werden unter **Benutzer** angelegt. Jedes Konto sieht seine eigenen Computer.

| Einstellung | Beim Verbinden |
|---|---|
| **Bestätigung am Gerät** | Die Person am Zielcomputer erlaubt den Zugriff. |
| **Mein Konto / kein weiteres Passwort** | Deine zentrale Anmeldung genügt; es erscheint keine zusätzliche Freigabemaske. |
| **Gerätepasswort** | Zusätzlich zur zentralen Anmeldung wird das Gerätepasswort abgefragt. |

## Während der Verbindung

Jede Verbindung öffnet ein eigenes Fenster. Ins Bild klicken, um zu steuern. **Pos1 / Home** gibt Maus und Tastatur lokal frei. Der Monitorplan zeigt die Anordnung der Bildschirme mit Nummern; ein Klick wechselt den Monitor. Mit dem Pfeil geht es zum nächsten Bildschirm.

**Vollbild** verwendet ein eigenes Vollbildfenster mit schwebender einklappbarer Leiste. Dort stehen Monitorwahl, Auflösungsgrenze, Bildqualität, 1:1, Zwischenablage, Dateien und Trennen bereit. Mit **Bildschirm an Fenster anpassen** wird die tatsächliche Auflösung des entfernten Computers auf den nächstpassenden unterstützten Modus gesetzt. Dafür muss auf dem Zielcomputer zRemote 0.3.0 Alpha 3 oder neuer laufen. Die separate Auflösungsgrenze begrenzt nur die Übertragung.

In den aktuellen Desktop-Apps lassen sich **Text und mehrere Dateien in beide Richtungen** kopieren und einfügen. Strg+C/V beziehungsweise Cmd+C/V verwenden oder die Schaltflächen in der Leiste wählen. **Dateien senden** öffnet eine Dateiauswahl. Fortschritt und Fehler werden im Verbindungsfenster angezeigt. Ordner werden noch nicht übertragen. Die Zwischenablage ist für die angemeldete Desktop-Sitzung vorgesehen.

Die native Tastaturübernahme gilt für die fokussierte Desktop-Verbindung. Betriebssystemreservierte Sicherheitsfolgen bleiben eine Ausnahme; **Strg + Alt + Entf** über die eigene Schaltfläche an das Windows-Dienstgerät senden. Im Browser stehen die nativen Datei-/Zwischenablagefunktionen und die Übernahme von Systemtastenkombinationen nicht zur Verfügung.

## Im Hintergrund erreichbar bleiben

**Windows:** Das Schließen des Hauptfensters lässt die App im Infobereich weiterlaufen. Von dort lässt sie sich wieder öffnen. Der optionale Systemdienst startet mit Windows und arbeitet unabhängig vom Hauptfenster. Er hat eine eigene Gerätezuordnung und unterstützt den Anmelde-/Sicherheitsdesktop. Windows-Anmeldedaten werden direkt in Windows eingegeben; Zumbyte Remote speichert kein Windows-Passwort und richtet kein Autologin ein.

**Mac:** Der Benutzer-LaunchAgent hält die App im Hintergrund erreichbar und startet sie nach der Anmeldung. Bildschirmaufnahme und Bedienungshilfen müssen in macOS freigegeben werden. Der Mac-Anmeldebildschirm und FileVault sind in dieser Alpha nicht enthalten. [Mac-Anleitung](docs/MACOS.md).

## Unraid und Community Apps

Das Image kann ohne Anmeldung geladen werden:

```sh
docker pull ghcr.io/zumbyte-appsolution/zumbyte-remote-server:alpha
```

Konten, Geräte und Anwendungsupdates bleiben im Appdata-Ordner. Der Container benötigt weder privilegierten Modus noch Docker-Socket. Die Vorlage erlaubt auch eine eigene br0-Adresse; bestehende IP-Adressen werden nicht geändert. [Unraid-Anleitung](docs/UNRAID.md).

Für Community Apps liegen **[ca_profile.xml](ca_profile.xml)** und **[templates/zumbyte-remote.xml](templates/zumbyte-remote.xml)** bereit. Die Vorlage enthält Icon, Beschreibung, Supportlinks, Port und Konfiguration. Die Aufnahme in den CA-Katalog erfolgt nach eigener Einreichung und Prüfung durch Unraid. [Dateien und Einreichung](docs/COMMUNITY-APPS.md).

## Updates

App und Server lesen den öffentlichen GitHub-Release-Feed und laden die passenden Dateien direkt. Dafür sind weder GitHub-API noch GitHub-Token nötig. Vor der Installation werden Signatur, Größe und SHA-256 geprüft.

Unter **Updates** wird das passende Installationspaket gestartet. Profile und Gerätezuordnung bleiben erhalten. Unraid aktualisiert über den Kanal `:alpha` das gesamte Containerimage. Zusätzliche automatische Serverupdates sind mit `AUTO_UPDATE` einschaltbar. [Update-Anleitung](docs/UPDATES.md).

## ServerDesk

Das [Remote-Plugin für ServerDesk](https://github.com/ZUMBYTE-AppSolution/serverdesk-plugins) ist als eigenes Downloadpaket erhältlich. Für separate Verbindungsfenster, native Eingaben und Vollbild empfehlen wir ServerDesk ab 0.2.0 Beta 26 und das zRemote-Plugin ab 0.3.0 Alpha 5.

Dies bleibt eine Alpha. Native Linux-Desktopsteuerung, Ordnerübertragung, MFA und weitere Praxistests stehen aus. Die Lizenz für Vorlagen und Dokumentation gilt nicht automatisch für die heruntergeladenen Anwendungsdateien.

**Zumbyte – AppSolution · [www.zumbyte.de](https://www.zumbyte.de/)**
