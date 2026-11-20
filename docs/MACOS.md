# zRemote auf dem Mac

zRemote gibt es für Apple Silicon (`arm64`) und Intel (`x64`). macOS 13 oder neuer wird benötigt.

## Installieren

Das passende PKG aus dem offiziellen Release herunterladen und öffnen. Es installiert `ZumbyteRemote.app` im Programme-Ordner. Alternativ die App aus dem DMG nach **Programme** ziehen. Unter **Verbinden** erscheinen die feste neunstellige ID und das Einmalpasswort. Ein Konto und ein eigener Server sind für eine Verbindung nicht erforderlich. Die Serveradresse wird nur beim ausdrücklich gewählten Betrieb mit einem eigenen Server benötigt.

Ab 0.3.0-alpha.3 sind die App und der PKG-Installer mit Developer ID signiert und von Apple notarisiert. Das passende Paket findest du im offiziellen [zRemote-Release](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases).

## Bildschirm und Steuerung freigeben

Unter **Dieser Computer → Freigaben erneut prüfen** die macOS-Freigaben prüfen. In den Systemeinstellungen unter **Datenschutz & Sicherheit** Bildschirmaufnahme und Bedienungshilfen für zRemote aktivieren. Bei einer älteren Installation kann dort noch **Zumbyte Remote** stehen. Die App anschließend vollständig beenden und erneut öffnen; das Schließen des Fensters lässt sie im Hintergrund laufen. macOS kann nach einem Update eine erneute Freigabe verlangen.

Ohne Bildschirmfreigabe kann der Mac kein Bild übertragen; ohne Bedienungshilfen kann er keine Maus- und Tastatureingaben annehmen. Ein zentraler Login ersetzt diese macOS-Freigaben nicht.

## Hintergrunddienst einrichten

In der installierten App unter **Dieser Computer → Hintergrunddienst einrichten** aktivieren. Der Dienst läuft als LaunchAgent des angemeldeten Benutzers. Seine Datei liegt unter `~/Library/LaunchAgents/de.zumbyte.remote.agent.plist`. Ein kleiner Helfer hält die App im Hintergrund offen und startet sie nach der Benutzeranmeldung erneut.

Die App bleibt beim Schließen des Hauptfensters im Hintergrund erreichbar. Über das Symbol in der Menüleiste öffnest du sie wieder. Unter **Anmeldeobjekte** kannst du den erlaubten Hintergrundbetrieb kontrollieren.

Der Dienst arbeitet in der angemeldeten grafischen Benutzersitzung. Zugriff vor der Mac-Anmeldung oder auf die FileVault-Entsperrung ist in dieser Version nicht enthalten.

## Verbinden und aktualisieren

Am steuernden Computer die ID oder den Verbindungsnamen und das Passwort des Macs eingeben. Die Anfrage am Mac annehmen und die Funktionen einzeln freigeben. Ein Dauerpasswort und die Bestätigung vor Ort lassen sich unter **Dieser Computer** einstellen. Dauerhaft erlaubte Gegenstellen sind unter **Kontakte** änderbar. Ein Konto ist für ID und Passwort optional; es ergänzt Verbindungsnamen, Freunde und Favoriten.

Jede Verbindung öffnet ein eigenes Fenster. Ins Bild klicken, um fernzusteuern. **Home/Pos1** gibt Maus und Tastatur lokal frei. Auf Mac-Tastaturen ohne Home entspricht das gewöhnlich **fn + Pfeil links**. Kopieren und Einfügen verwenden die Tastenkombination des Zielsystems, beim Mac also Cmd+C und Cmd+V. Text und einzelne oder mehrere Dateien werden unterstützt, Ordner noch nicht. Die Freigaben gelten auch für den direkten Chat und Dateiversand. Auf dem Mac bleibt ein kleines Fenster zum Ändern der Rechte und Trennen der Verbindung erreichbar.

Bei geöffnetem MacBook oder aktiver, entsperrter Sitzung passt zRemote das Bild proportional ins Fenster ein. Ein tatsächlicher Auflösungswechsel wird nur angeboten, wenn der Mac gesperrt ist, kein geöffneter Laptopbildschirm entgegensteht und macOS einen aktiven Bildschirm mit passenden Modi bereitstellt. Die Anordnung der Bildschirme bleibt erhalten. Ist ein Wechsel nicht möglich, bleibt das vollständige Bild eingepasst. Ein virtueller Zusatzbildschirm ist nicht enthalten.

Die Vermittlung überträgt nur Verbindungsangebote. Bild, Eingaben, Ton und Dateien laufen direkt zwischen den Computern. Eine Sitzung endet nach 90 Minuten. Bei einem vorzeitigen Abbruch zeigt das Verbindungsfenster den Countdown bis zum nächsten Versuch; Schließen des Fensters beendet diese Versuche.

Unter **Updates** neue Versionen prüfen. Die App lädt das passende PKG direkt aus dem GitHub-Release und prüft Signatur sowie SHA-256. Vor dem Installieren Fernsitzungen beenden. Das Systeminstallationsprogramm führt das Update aus; ein eingerichteter Hintergrunddienst wird anschließend wiederhergestellt. Bei Abbruch des Installationsdialogs die bisherige App erneut öffnen, damit sie ihren Hintergrunddienst wiederherstellt.
