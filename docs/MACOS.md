# zRemote auf dem Mac

zRemote gibt es für Apple Silicon (`arm64`) und Intel (`x64`). macOS 13 oder neuer wird benötigt.

## Installieren

Das passende PKG aus dem offiziellen Release herunterladen und öffnen. Es installiert `ZumbyteRemote.app` im Programme-Ordner. Alternativ die App aus dem DMG nach **Programme** ziehen. Danach die eigene HTTPS-Serveradresse eintragen und anmelden.

Ab 0.3.0-alpha.3 sind die App und der PKG-Installer mit Developer ID signiert und von Apple notarisiert. Das passende Paket findest du im offiziellen [zRemote-Release](https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release/releases).

## Bildschirm und Steuerung freigeben

Unter **Dieser Computer** den Mac dem Konto zuordnen. Die Schaltflächen **Bildschirmaufnahme** und **Bedienungshilfen** öffnen die passenden Systemeinstellungen. Dort zRemote freigeben. Bei einer früheren Installation kann der Eintrag noch **Zumbyte Remote** heißen. Die App danach über **zRemote → Beenden** vollständig schließen und erneut öffnen; das Schließen-Kreuz lässt sie im Hintergrund weiterlaufen. Anschließend unter **Dieser Computer → Freigaben erneut prüfen** kontrollieren und neu verbinden. macOS kann nach einem Update eine erneute Freigabe verlangen.

Ohne Bildschirmfreigabe kann der Mac kein Bild übertragen; ohne Bedienungshilfen kann er keine Maus- und Tastatureingaben annehmen. Ein zentraler Login ersetzt diese macOS-Freigaben nicht.

## Hintergrunddienst einrichten

In der installierten App unter **Dieser Computer → macOS-Hintergrunddienst einrichten** aktivieren. Der Dienst läuft als LaunchAgent des angemeldeten Benutzers. Seine Datei liegt unter `~/Library/LaunchAgents/de.zumbyte.remote.agent.plist`. Ein kleiner Helfer hält die App im Hintergrund offen und startet sie nach der Benutzeranmeldung erneut.

Die App bleibt beim Schließen des Hauptfensters im Hintergrund erreichbar. Über das Symbol in der Menüleiste öffnest du sie wieder. Unter **Anmeldeobjekte** kannst du den erlaubten Hintergrundbetrieb kontrollieren. Zum Entfernen in der App **Hintergrunddienst deaktivieren** wählen; Gerätezuordnung und Anmeldedaten bleiben erhalten.

Der Dienst arbeitet in der angemeldeten grafischen Benutzersitzung. Zugriff vor der Mac-Anmeldung oder auf die FileVault-Entsperrung ist in dieser Version nicht enthalten.

## Verbinden und aktualisieren

Wenn macOS keinen passenden Auflösungswechsel erlaubt, wird ab Alpha 7 das vollständige Bild automatisch ins Fenster eingepasst. Das Seitenverhältnis bleibt erhalten, auch im Vollbild. Originalgröße · 1:1 bleibt manuell auswählbar. Die Automatik aus- und wieder einschalten, um einen Auflösungswechsel erneut zu versuchen.

Jede Verbindung öffnet ein eigenes Fenster. Ins Bild klicken, um fernzusteuern. **Home/Pos1** gibt Maus und Tastatur lokal frei. Auf Mac-Tastaturen ohne Home entspricht das gewöhnlich **fn + Pfeil links**. Kopieren und Einfügen verwenden die Tastenkombination des Zielsystems, beim Mac also Cmd+C und Cmd+V. Text und einzelne oder mehrere Dateien werden unterstützt, Ordner noch nicht.

Unter **Updates** neue Versionen prüfen. Die App lädt das passende PKG direkt aus dem GitHub-Release und prüft Signatur sowie SHA-256. Vor dem Installieren Fernsitzungen beenden. Das Systeminstallationsprogramm führt das Update aus; ein eingerichteter Hintergrunddienst wird anschließend wiederhergestellt. Bei Abbruch des Installationsdialogs die bisherige App erneut öffnen, damit sie ihren Hintergrunddienst wiederherstellt.

Ab **0.3.0 Alpha 5** zeigt die App Downloadfortschritt, Geschwindigkeit, Restzeit und sichtbare Fehlermeldungen. Falls eine ältere Version beim Update wiederholt abbricht, den passenden PKG-Installer einmal direkt von der Release-Seite herunterladen und öffnen. Einstellungen und gespeicherte Computer bleiben erhalten.
