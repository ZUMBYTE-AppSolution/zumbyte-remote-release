# Changelog

## 0.3.0-alpha.6 · 19. November 2026

- Windows und Mac zeigen in der Seitenleiste die tatsächlich installierte App-Version.
- Die Mac-App trägt den Anzeigenamen zRemote. Vorhandene Einstellungen und Gerätezuordnungen bleiben erhalten.
- Mausbewegungen werden gleichmäßiger übertragen. Beim Klicken wird die letzte Zeigerposition zuerst gesendet.
- Die Bildverarbeitung im Verbindungsfenster benötigt weniger Rechenzeit.
- Beim Windows-Hintergrunddienst blockiert die Bildschirmaufnahme keine Eingaben mehr.
- Die höchste Bildqualität unterstützt bei direkten Desktop-Verbindungen bis zu 60 Bilder pro Sekunde. Die tatsächlich erreichbare Bildrate hängt von den Geräten und der Verbindung ab.
- Die App prüft, ob die Maus- und Tastatursteuerung wirklich bereit ist. Fehlende Freigaben oder ein Startfehler werden angezeigt.

Windows-Pakete sind digital signiert. Die Pakete für Apple Silicon und Intel sind mit Developer ID signiert und von Apple notarisiert. Das Docker-Image und die Community-Apps-Dateien bleiben bei Alpha 5; der Kanal `:alpha` bleibt unverändert.

## 0.3.0-alpha.5 · 19. November 2026

- Das Docker-Image für Unraid enthält Alpha 5 und lässt sich über den Kanal `:alpha` direkt im Docker-Tab aktualisieren.
- Aktualisierte Community-Apps-Vorlage mit erhaltenen Appdata-Einstellungen und optionalen zusätzlichen Serverupdates.
- Die Serveroberfläche zeigt Downloadgeschwindigkeit, Restzeit und die im Container enthaltene Version.

- Der Mac-Installer schließt die Installation wieder vollständig ab und öffnet anschließend die App.
- Gespeicherte Zugänge aus älteren Mac-Versionen werden nach der Umbenennung zu zRemote übernommen.
- Ein zuvor eingerichteter Mac-Hintergrunddienst wird nach dem Update wieder gestartet.
- Downloadfortschritt, Geschwindigkeit, Restzeit, automatische Wiederholungen und sichtbare Fehlermeldungen sind enthalten.

## 0.3.0-alpha.4 · 19. November 2026

Zurückgezogen wegen eines Fehlers beim Abschluss der Mac-Installation. Bitte Alpha 5 verwenden.

- Updates zeigen Downloadfortschritt, Geschwindigkeit, Restzeit und die anschließende Paketprüfung.
- Langsame Downloads werden nicht mehr nach drei Minuten abgebrochen.
- Nach einer Unterbrechung wird automatisch erneut versucht; vorhandene Daten werden nach Möglichkeit weiterverwendet.
- Fehlermeldungen bleiben sichtbar und bieten einen erneuten Versuch an.
- Der Mac-Installer wird vor dem Öffnen auf Apple-Signatur und Freigabe geprüft. Schlägt das Öffnen fehl, bleibt die App erreichbar.
- Die neue Updateanzeige ist auch im Server enthalten, einschließlich Docker und Unraid.

## 0.3.0-alpha.3 · 18. November 2026

- Die Bildschirmauflösung des entfernten Windows-Computers passt sich auf Wunsch an das Verbindungsfenster und an Vollbild an. Gewählt wird die nächstpassende unterstützte Auflösung; beim Trennen wird die vorherige Einstellung wiederhergestellt.
- Bei einem Verbindungsabbruch oder einem fehlgeschlagenen Aufbau wird die Verbindung automatisch erneut versucht. Ein Countdown zeigt die Zeit bis zum nächsten Versuch.
- Die angepinnte Steuerleiste schließt oben oder unten bündig mit dem Bildschirmrand ab.
- Die neuen Bedienelemente stehen auch im zRemote-Plugin für ServerDesk bereit.
- Die Mac-App und die Installer für Apple Silicon und Intel sind mit Developer ID signiert und von Apple notarisiert.

## 0.3.0-alpha.2 · 17. November 2026

- Windows-App, Hintergrunddienst, Installer und Deinstallation sind digital signiert. Verifizierter Herausgeber: Andreas Zumbansen.
- Installer mit Desktopverknüpfung und portable Windows-Ausgabe.
- Gerätezuordnungen und geschützte Profile bleiben bei Updates erhalten.
- Weiterhin automatische Updateprüfung ohne GitHub-Konto oder GitHub-API.

Diese Ausgabe enthält Windows-Pakete und das passende Serverpaket. Mac-Pakete und das fertige Docker-Image bleiben bei Alpha 1.

## 0.3.0-alpha.1 · 12. November 2026

- Mac-Pakete für Apple Silicon und Intel, native Maus-/Tastatursteuerung und ein Benutzer-Hintergrunddienst.
- Windows-App im Infobereich; Schließen des Hauptfensters lässt sie im Hintergrund weiterlaufen.
- Native Vollbildfunktion mit schwebender einklappbarer Steuerleiste und Pos1/Home als lokale Freigabetaste.
- Grafische Monitoranordnung mit Nummern, anklickbarem Wechsel und Auflösungsgrenzen für die Übertragung.
- Text und mehrere Dateien in beide Richtungen kopieren und einfügen; Fortschritt und Prüfsummen enthalten.
- Kontozugriff ohne Gerätepasswort öffnet keine zusätzliche Freigabemaske. Bestätigung bleibt separat wählbar.
- Windows-Dienst für den Anmelde-/Sicherheitsdesktop; Dateioperationen mit den Rechten des angemeldeten Benutzers.
- ServerDesk-Provider um Datei-/Zwischenablagedienste und fokussierte native Eingaben erweitert.
- Öffentliches GHCR-Image und vollständige Community-Apps-Dateien für Unraid vorbereitet.
- Release-Titel tragen Appname und Versionsnummer. Screenshots der Test-Eingabefenster wurden entfernt und werden nicht mehr veröffentlicht.

Mac-Fernsteuerung und echte Boot-/Anmeldeszenarien benötigen weitere Praxistests. Ordnerübertragung, native Linux-Desktopsteuerung und herstellerseitig signierte Installationspakete sind noch nicht enthalten.


## Ergänzungen in 0.2.0-alpha.1

- Neues App- und Installericon mit Monitor, Verbindungspfeilen und türkisem Glow.
- ServerDesk-Plugin mit Anmeldung, Geräteverwaltung und Fernansicht vorbereitet. Die Nutzung benötigt eine kompatible ServerDesk-Version.
- Signierter Plugin-Katalog mit einzelnen Versionen und direkten Downloadpaketen ohne GitHub-API.

## 0.2.0-alpha.1 – 2026-11-10

- Windows-Maus- und Tastatursteuerung mit begrenztem Eingabeprotokoll und Freigabe gehaltener Tasten beim Trennen.
- Eigener Windows-Systemdienst mit automatischem Start, Wiederverbindung und erhaltenen Geräteschlüsseln.
- Separater Sitzungshelfer für aktive Konsole und Windows-Sicherheitsdesktop; kein gespeichertes Windows-Kennwort nötig.
- P-256-Geräteauthentifizierung zusätzlich zu bestehenden Ed25519-App-Geräten.
- Bild- und Eingaberelay für den Dienst über den selbst betriebenen Server.
- Windows-Installer mit Desktop-/Startmenüverknüpfung, Deinstallation und Dienstübernahme bei Updates.
- API-freie Releaseprüfung, Updatekanäle, Ed25519-signierte Beschreibung und SHA-256-Prüfung.
- Verwalteter Serverstart mit dauerhaften Anwendungslaufzeiten und Rückfall bei Fehlstart, auch in Docker/Unraid.
- Eigene Downloadseite mit Anleitungen und App-Screenshots.

Ein echter Neustart mit Windows-Anmeldung, Mac-/Linux-Fernsteuerung und Verbindungen über getrennte Internetnetze benötigen weitere Praxistests. Der Stand bleibt eine Alpha.

## 0.1.0-alpha.1 – 2026-11-10

Erste lokale Grundlage: zentraler Login, Benutzerkonten, Geräteliste, Einmalkopplung, feste Schlüssel, Zugriffsregeln und WebRTC-Bildschirmansicht. Als lokale Pakete erstellt; noch kein GitHub-Release.
