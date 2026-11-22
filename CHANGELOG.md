# Änderungen

## 0.3.0 Alpha 10 · 20. November 2026

### Linux-RPM Revision 2 · ergänzt am 22. November

- Bildschirmfreigabe funktioniert auf GamerZ OS mit Hyprland auch bei Verwendung von XWayland.
- Maus und Tastatur nutzen den verfügbaren Wayland-Eingabezugang. Abgelehnte Systemfreigaben bleiben gesperrt.
- Unter Wayland bleibt die Bildschirmauflösung unverändert; das Bild wird proportional eingepasst.
- Neuer Linux-Systemdienst für Zugriff vor der Anmeldung, mit Bild und Eingaben. Bei Bedarf wird nach freigegebenem Zugriff eine freie Textanmeldung verwendet.
- Paketupdates erhalten Geräte-ID, Passwörter, Serverzuordnung und Dienstschlüssel.
- Der Linux-Client setzt für Verbindungen über den eigenen Server kein 90-Minuten-Zeitlimit mehr. Ältere Server und Gegenstellen benötigen die entsprechende Korrektur ebenfalls.

Die neue Datei endet auf „linux-x86_64-r2.rpm“. Einmal über AppStore oder Paketverwaltung installieren; Revisionen derselben App-Version erscheinen nicht als neue Version im App-Updater. Andere Alpha-10-Linux-Pakete bleiben unverändert.

### RPM für Fedora und GamerZ OS · ergänzt am 21. November

- Natives RPM-Paket für x86_64, direkt über den GamerZ-AppStore installierbar.
- Abhängigkeiten und Menüeintrag werden von der Paketverwaltung eingerichtet.
- Updates verwenden weiterhin RPM und zeigen den Downloadfortschritt an. Geräte-ID und Einstellungen bleiben erhalten.
- Der geschützte Gerätespeicher funktioniert auch in der Hyprland-Sitzung von GamerZ OS.

### Linux-Installer · ergänzt am 21. November

- Grafische Installer für x64 und ARM64, einschließlich Raspberry Pi mit 64-Bit-Desktop-System.
- Installation im eigenen Benutzerkonto, Menüeintrag und wählbare Desktopverknüpfung.
- Hintergrundstart nach der Linux-Anmeldung ist wählbar.
- Updates und Deinstallation erhalten Geräte-ID und persönliche Einstellungen.
- Updates funktionieren auch auf Distributionen mit neueren Systembibliotheken.

Der .run-Installer ist auch für Fedora, openSUSE und Arch vorgesehen. DEB-Pakete und portable Ausgaben bleiben als Alternative verfügbar. ARM64 ist neu; ein Test auf einem echten Raspberry Pi steht noch aus.

Die Geräte-ID ist nach dem Beenden oder einem abgebrochenen Start sofort wieder verfügbar. Eine zurückgebliebene Sperre eines bereits beendeten Prozesses verhindert das Öffnen von zRemote nicht mehr.

- Geräte-ID, Passwörter und gespeicherte Freigaben bleiben erhalten.
- Ein noch laufender Zugriff auf den Gerätespeicher wird weiterhin geschützt.
- Die Korrektur gilt für Windows, macOS, Linux und die Hilfsprogramme des ServerDesk-Plugins.

Bitte beide zRemote-Apps und das ServerDesk-Plugin auf Alpha 10 aktualisieren. ServerDesk Beta 28 kann weiterverwendet werden.

## 0.3.0 Alpha 9 · 20. November 2026

### Verbinden mit ID und Passwort

zRemote vergibt jetzt eine feste neunstellige ID. Damit lassen sich Computer ohne Registrierung und ohne eigenen Server verbinden. Das Einmalpasswort wird nach Verwendung erneuert; ein Dauerpasswort lässt sich unter „Dieser Computer“ speichern.

Ein Zumbyte-Konto ergänzt einen Verbindungsnamen, Freunde und Favoriten. Die ID bleibt auch ohne Konto nutzbar. Portable und installierte App verwenden beim selben Benutzer dieselbe Gerätezuordnung.

### Du bestimmst die Freigaben

Der Annahmedialog lässt Bild, Maus, Tastatur, Zwischenablage, Dateien, Chat und verfügbaren Ton einzeln freigeben. Im Präsentationsmodus bewegt die Gegenstelle nur den Mauszeiger. Dauerhaft erlaubte Zugriffe können mit eigenen Rechten gespeichert und unter „Kontakte“ wieder geändert werden.

Auf dem ferngesteuerten Computer bleibt ein kleines, minimierbares Fenster zum Ändern der Freigaben und Trennen der Verbindung. Chatnachrichten, Links und Dateien laufen direkt zwischen den Computern. Nach 90 Minuten endet eine Sitzung.

### Jetzt auch als Linux-App

Für Linux x64 gibt es einen DEB-Installer und ein portables TAR.GZ-Paket. Unter X11 sind Bildschirmübertragung, Maus, Tastatur sowie Text- und Dateizwischenablage enthalten. Hintergrundstart nach der Benutzeranmeldung und der gemeinsame Updater sind eingebaut.

Wayland ist noch experimentell und verlangt die Freigabe im Systemdialog. Bei mehreren angeschlossenen Bildschirmen steht dort zunächst nur die Ansicht zur Verfügung. Zugriff vor der Linux-Anmeldung ist in dieser Ausgabe nicht enthalten.

### Außerdem

- Einstellungen für Bild, Qualität und Eingaben bleiben je Gegenstelle gespeichert und lassen sich zurücksetzen.
- Bei Verbindungsabbruch zeigt ein Countdown den nächsten Versuch. Schließen des Fensters beendet weitere Versuche.
- Der Windows-Hintergrunddienst verwendet dieselbe öffentliche ID. Bestehende Dienste für einen eigenen Server lassen sich über „Hintergrunddienst einrichten“ ergänzen.
- Mac-Verbindungen passen das vollständige Bild ein, wenn die Bildschirmauflösung nicht sicher geändert werden kann.
- Updates zeigen Downloadfortschritt und bleibende Fehlermeldungen. Die Suche benötigt keinen GitHub-Token.

Die öffentliche Vermittlung überträgt Verbindungsangebote und keine Sitzungsinhalte. Verbindungen können an Router- oder Firewallbeschränkungen scheitern. Der eigene Server und der Unraid-Container bleiben als zusätzliche Betriebsart verfügbar.

Windows-Dienstverbindungen übertragen in dieser Ausgabe keinen Ton und kein Mikrofon. Ordnerübertragung und ein virtueller Mac-Zusatzbildschirm sind nicht enthalten.


## 0.3.0-alpha.8 · 19. November 2026

- Direkt in der Verbindung chatten: eigene und empfangene Nachrichten haben unterschiedliche Sprechblasen, Links sind anklickbar und zugestellte Nachrichten werden gekennzeichnet.
- Dateien im Chat senden, den Fortschritt verfolgen und empfangene Dateien gezielt speichern. Chat-Anhänge verändern die Zwischenablage nicht automatisch.
- Bildqualität, Bildgröße, Monitor, Ton, Mauszeiger und die Position der Steuerleiste für jeden Computer separat speichern und auf Standard zurücksetzen.
- Am Mac werden Deckel- und Sperrstatus getrennt geprüft. Bei geöffnetem Deckel, aktiver Sitzung oder abgelehntem Auflösungswechsel bleibt die Auflösung erhalten; das Bild wird unverzerrt eingepasst.
- Sitzungen enden nach 90 Minuten. Danach startet keine automatische Wiederverbindung.
- Der Windows-Systemdienst zeigt während der Freigabe ein einklappbares Fenster mit Chat und Trennen-Schaltfläche. Die Gegenstelle kann dieses Fenster nicht fernbedienen.

Für den Chat beide Geräte und den Remote-Server aktualisieren. In ServerDesk werden das neue zRemote-Plugin und ServerDesk Beta 27 benötigt.

## 0.3.0-alpha.7 · 19. November 2026

- Bei abgelehntem oder nicht unterstütztem Auflösungswechsel wird das vollständige Remote-Bild automatisch ins Fenster eingepasst, ohne es zu verzerren.
- Die Anpassung gilt auch für Vollbild und das ServerDesk-Plugin. Die Originalauflösung des Bildes bleibt erhalten.
- Nach einem abgelehnten Wechsel werden für diesen Monitor keine weiteren automatischen Auflösungswechsel angefordert. Aus- und Einschalten der Automatik erlaubt einen neuen Versuch.
- Originalgröße · 1:1 bleibt als manuelle Ansicht verfügbar.

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
