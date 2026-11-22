zRemote für Linux
=================

Installation

Für Fedora und GamerZ OS gibt es ein natives RPM-Paket für x86_64. Im
AppStore das Repository „ZUMBYTE-AppSolution/zumbyte-remote-release“ und
Alpha 10 wählen, dann die korrigierte Datei mit „linux-x86_64-r3.rpm“ installieren.
Bei Bedarf zuerst die GitHub-Quelle im AppStore aktualisieren.
Abhängigkeiten und Menüeintrag richtet die Paketverwaltung ein.
Alternativ im Downloadordner:

    sudo dnf install ./ZumbyteRemote-Setup-0.3.0-alpha.10-linux-x86_64-r3.rpm

Revision 3 ergänzt die direkte Bildschirmaufnahme des Systemdienstes auf
GamerZ OS und kompatiblen Wayland-Desktops. Die Versionsanzeige der App
bleibt „0.3.0-alpha.10“; die Paketverwaltung erkennt die neuere Revision.
Bitte die neue Datei einmal über den AppStore oder die Paketverwaltung
installieren. Der App-Updater bietet Revisionen derselben App-Version
nicht als neue Version an. Andere Alpha-10-Linux-Pakete enthalten diese
Korrektur noch nicht.

Bei einer RPM-Installation verwendet auch der zRemote-Updater wieder ein
RPM-Paket und die System-Paketverwaltung. Benutzerprofile, Geräte-ID und
gespeicherte Freigaben bleiben dabei erhalten. Eine laufende portable oder
.run-Ausgabe bitte vor dem Wechsel vollständig über „App beenden“ schließen.

Wähle die Ausgabe passend zu deinem Computer:

• x64: normale PCs mit Intel- oder AMD-Prozessor.
• ARM64: 64-Bit-ARM-Geräte, beispielsweise Raspberry Pi mit einem
  64-Bit-Desktop-System. Eine 32-Bit-Installation wird nicht unterstützt.

Der grafische .run-Installer ist für aktuelle Linux-Desktops mit glibc 2.35
oder neuer vorgesehen: zum Beispiel Ubuntu 22.04+, Debian 12+, Fedora,
openSUSE und Arch Linux. Auf einem Raspberry Pi eignet sich Raspberry Pi OS
Bookworm 64-bit oder neuer mit Desktop. GTK 3, NSS, ALSA, X11-Bibliotheken,
libsecret und OpenSSL müssen über die Paketverwaltung verfügbar sein.
Ein Anmeldeschlüsselbund wie GNOME Schlüsselbund oder KWallet schützt die
Gerätezuordnung. Alpine/musl, 32-Bit-Systeme und reine Konsolensysteme ohne
Desktop werden nicht unterstützt. Die unterschiedlichen Desktop- und
Grafiktreiber können die verfügbaren Fernsteuerungsfunktionen beeinflussen.

Lade den .run-Installer herunter, erlaube in seinen Dateieigenschaften das
Ausführen und starte ihn. Alternativ im Downloadordner, für x64:

    chmod +x ./ZumbyteRemote-Setup-0.3.0-alpha.10-linux-x64.run
    ./ZumbyteRemote-Setup-0.3.0-alpha.10-linux-x64.run

Für ARM64 die Datei mit „linux-arm64.run“ verwenden. Bitte ohne sudo starten.
Der Assistent installiert zRemote für dein Benutzerkonto und legt einen
Menüeintrag an. Desktopverknüpfung und Start nach der Linux-Anmeldung sind
wählbar. Standardordner: ~/.local/share/zremote. Zum Entfernen im Menüeintrag
die Aktion „zRemote deinstallieren“ wählen oder „uninstall“ im Programmordner
starten. Geräte-ID und persönliche Einstellungen bleiben erhalten.

Debian, Ubuntu und Raspberry Pi OS können alternativ das passende DEB-Paket
mit ihrer Paketverwaltung installieren. Eine bereits vorhandene DEB-Ausgabe
bitte über die Paketverwaltung entfernen, bevor du zum .run-Installer
wechselst. Beide Ausgaben verwenden dieselben geschützten Benutzerdaten.

Die portable TAR.GZ-Ausgabe lässt sich in einen beschreibbaren Ordner entpacken.
Öffne darin „zRemote“ und behalte den Ordner auch für künftige Updates.

Verbinden

Gib am steuernden Computer die ID und das Einmal- oder Dauerpasswort des
anderen Computers ein. Ein Konto ist dafür nicht erforderlich. Der entfernte
Benutzer wählt, welche Funktionen freigegeben werden. Mit Pos1 gibst du Maus
und Tastatur am steuernden Computer wieder frei.

Der Systemdienst verwendet auf GamerZ OS und kompatiblen Hyprland-/wlroots-
Desktops den direkten Aufnahmezugang. Die Programmfreigabe wird beim
Einrichten des Dienstes vorbereitet. Eine ausdrücklich verweigerte
Bildschirmaufnahme bleibt gesperrt. Bei „Mein Account ohne Passwort“ auf
dem eigenen Server ist kein Annahmedialog erforderlich. Während der
Verbindung erscheint das kleine, minimierbare Freigabefenster wie unter
Windows und macOS. Dort kannst du Rechte ändern oder die Verbindung trennen.

Auf anderen Wayland-Desktops ist die lokale Bildschirmfreigabe nötig; ein
vollständig unbeaufsichtigter Desktopzugriff ist dort nicht zugesichert.
Eine bestätigte Aufnahme wird für weitere Verbindungen wiederverwendet.
Abbruch oder verweigerte Freigabe lösen bei automatischen Wiederverbindungen
keine weiteren Auswahldialoge aus. Je nach Desktop ist
eine zweite Freigabe für Maus und Tastatur nötig. Wähle dann in beiden
Systemdialogen denselben Bildschirm. Hyprland und kompatible wlroots-
Desktops können ihren eigenen Eingabezugang verwenden. Die Auflösung und
Systemtastenkürzel verwaltet unter Wayland der Desktop. Das Verbindungsfenster
passt das Bild proportional ein. Bei mehreren angeschlossenen Bildschirmen
steht unter Wayland in dieser Ausgabe nur die Ansicht zur Verfügung, damit
Eingaben nicht auf dem falschen Bildschirm landen. Für die vollständige
Steuerung mehrerer Monitore bitte eine X11-Sitzung verwenden. Die Wayland-
Unterstützung ist noch experimentell. zRemote prüft die verfügbaren
Systemfreigaben; fehlende oder abgelehnte Eingaberechte werden als Fehler
angezeigt. Ein eigenes zRemote-Gerätepasswort ersetzt keine Betriebssystem-
Freigabe. Die Grafikauflösung bleibt unter Wayland unverändert.

Zugriff vor der Anmeldung

Installiere die RPM-Revision 3 systemweit und wähle in zRemote unter
„Dieser Computer“ beziehungsweise in den Geräteeinstellungen
„Linux-Systemdienst einrichten“. Bestätige die Linux-Administratorabfrage.
Der Dienst startet danach mit dem Computer. Geräte-ID, Passwort und die
Zuordnung zu deinem eigenen Server werden übernommen.

Vor der Anmeldung braucht die Verbindung ein gültiges zRemote-Passwort,
eine dauerhafte Freigabe oder die eingerichtete Kontofreigabe deines eigenen
Servers. Eine Bestätigung durch einen angemeldeten Benutzer ist dort
naturgemäß nicht möglich. Dein Linux-Anmeldekennwort wird weder gespeichert
noch automatisch eingegeben.

Bei einer Textanmeldung wird die echte Anmeldekonsole übertragen. Stellt
eine grafische Wayland-Anmeldung keine Fernsteuerungsfreigabe bereit,
öffnet der Dienst erst nach freigegebenem Zugriff eine freie Textanmeldung.
Nach dem Trennen kehrt er zur ursprünglichen Anzeige zurück, sofern an der
Textkonsole keine Anmeldung erfolgt ist. Eine vorhandene Benutzersitzung
wird nicht beendet. Nach der grafischen Anmeldung verbindet sich der Client
erneut; gegebenenfalls muss die lokale Bildschirmfreigabe bestätigt werden.

Der Linux-Systemdienst unterstützt derzeit Bild und Eingaben. Chat, Dateien,
Zwischenablage und Ton sind in diesem Dienst noch nicht verfügbar. Die
normale App bietet weiterhin die übrigen Verbindungsfunktionen. Für den
Systemdienst werden systemd, logind, Xvfb, freie virtuelle Konsolen und ein
Kernel mit uinput benötigt. Auf anderen Init-Systemen bleibt der Start
nach der Benutzeranmeldung verfügbar. Eine reine Serverinstallation ohne
grafische Laufzeit und unveränderliche Systeminstallationen sind mit dem
RPM nicht abgedeckt.

Hintergrund und Updates

Unter Einstellungen kannst du den Hintergrundstart für deine Linux-Anmeldung
einrichten. Das Schließen des Hauptfensters lässt zRemote im Infobereich
weiterlaufen. Ohne Systemdienst beendet „App beenden“ die Freigabe. Ein
eingerichteter Systemdienst bleibt unabhängig von der App aktiv und lässt
sich über die Linux-Diensteverwaltung stoppen.

Updates zeigen ihren Downloadfortschritt an und prüfen die Herkunft und
Prüfsumme. Bei einer DEB- oder RPM-Installation fragt die Paketverwaltung nach deiner
Bestätigung. Die .run-Installation und portable Ausgaben aktualisieren sich
in ihrem eigenen Ordner. Geräte-ID und Einstellungen bleiben erhalten.
Es werden öffentliche Release-Dateien und der GitHub-Atom-Feed verwendet;
ein GitHub-Konto oder Token wird nicht benötigt.

Verbindungen laufen direkt zwischen den beteiligten Computern. Die Zumbyte-
Vermittlung überträgt Verbindungsangebote. Nur bei der öffentlichen ID-
Vermittlung endet eine Sitzung nach 90 Minuten. Verbindungen über einen
eigenen Server sind ohne dieses Zeitlimit vorgesehen; dafür müssen auch
Server und steuernde App die Korrektur enthalten. Ältere Ausgaben können
die Verbindung weiterhin nach 90 Minuten beenden.
