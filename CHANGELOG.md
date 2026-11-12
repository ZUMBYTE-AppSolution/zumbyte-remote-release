# Changelog

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
