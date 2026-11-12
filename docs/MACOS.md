# Zumbyte Remote auf dem Mac

Ab 0.3.0-alpha.1 gibt es Pakete für Apple Silicon (`arm64`) und Intel (`x64`). macOS 13 oder neuer wird benötigt. Die Mac-Fernsteuerung ist neu und benötigt noch Praxistests auf echten Macs.

## Installieren

Das passende PKG aus dem offiziellen Release herunterladen und öffnen. Es installiert `ZumbyteRemote.app` im Programme-Ordner. Alternativ die App aus dem DMG nach **Programme** ziehen. Danach die eigene HTTPS-Serveradresse eintragen und anmelden.

Die Alpha besitzt noch keine Apple-Developer-ID und keine Apple-Notarisierung. macOS kann deshalb eine Freigabe unter **Systemeinstellungen → Datenschutz & Sicherheit** verlangen. Das Paket nicht aus unbekannten Downloadquellen beziehen. Es werden keine macOS-Sicherheitsfunktionen abgeschaltet.

## Bildschirm und Steuerung freigeben

Unter **Dieser Computer** den Mac dem Konto zuordnen. Die Schaltflächen **Bildschirmaufnahme** und **Bedienungshilfen** öffnen die passenden Systemeinstellungen. Dort Zumbyte Remote freigeben und die App anschließend erneut öffnen. macOS kann nach einem Update eine erneute Freigabe verlangen.

Ohne Bildschirmfreigabe kann der Mac kein Bild übertragen; ohne Bedienungshilfen kann er keine Maus- und Tastatureingaben annehmen. Ein zentraler Login ersetzt diese macOS-Freigaben nicht.

## Hintergrunddienst einrichten

In der installierten App unter **Dieser Computer → macOS-Hintergrunddienst einrichten** aktivieren. Der Dienst läuft als LaunchAgent des angemeldeten Benutzers. Seine Datei liegt unter `~/Library/LaunchAgents/de.zumbyte.remote.agent.plist`. Ein kleiner Helfer hält die App im Hintergrund offen und startet sie nach der Benutzeranmeldung erneut.

Die App bleibt beim Schließen des Hauptfensters im Hintergrund erreichbar. Über das Symbol in der Menüleiste öffnest du sie wieder. Unter **Anmeldeobjekte** kannst du den erlaubten Hintergrundbetrieb kontrollieren. Zum Entfernen in der App **Hintergrunddienst deaktivieren** wählen; Gerätezuordnung und Anmeldedaten bleiben erhalten.

Der Dienst arbeitet in der angemeldeten grafischen Benutzersitzung. Zugriff vor der Mac-Anmeldung oder auf die FileVault-Entsperrung ist in dieser Version nicht enthalten.

## Verbinden und aktualisieren

Jede Verbindung öffnet ein eigenes Fenster. Ins Bild klicken, um fernzusteuern. **Home/Pos1** gibt Maus und Tastatur lokal frei. Auf Mac-Tastaturen ohne Home entspricht das gewöhnlich **fn + Pfeil links**. Kopieren und Einfügen verwenden die Tastenkombination des Zielsystems, beim Mac also Cmd+C und Cmd+V. Text und einzelne oder mehrere Dateien werden unterstützt, Ordner noch nicht.

Unter **Updates** neue Versionen prüfen. Die App lädt das passende PKG direkt aus dem GitHub-Release und prüft Signatur sowie SHA-256. Vor dem Installieren Fernsitzungen beenden. Das Systeminstallationsprogramm führt das Update aus; ein eingerichteter Hintergrunddienst wird anschließend wiederhergestellt. Bei Abbruch des Installationsdialogs die bisherige App erneut öffnen, damit sie ihren Hintergrunddienst wiederherstellt.
