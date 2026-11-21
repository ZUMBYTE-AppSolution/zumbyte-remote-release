zRemote für Linux
=================

Installation

Für Fedora und GamerZ OS gibt es ein natives RPM-Paket für x86_64. Im
AppStore das Repository „ZUMBYTE-AppSolution/zumbyte-remote-release“ und
Alpha 10 wählen, dann die Datei mit „linux-x86_64.rpm“ installieren.
Bei Bedarf zuerst die GitHub-Quelle im AppStore aktualisieren.
Abhängigkeiten und Menüeintrag richtet die Paketverwaltung ein.
Alternativ im Downloadordner:

    sudo dnf install ./ZumbyteRemote-Setup-0.3.0-alpha.10-linux-x86_64.rpm

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

Wayland fragt zusätzlich nach der Freigabe von Bildschirm, Maus und Tastatur.
Wähle in den beiden Systemdialogen denselben Bildschirm. Die Auflösung und
Systemtastenkürzel verwaltet unter Wayland der Desktop. Das Verbindungsfenster
passt das Bild proportional ein. Bei mehreren angeschlossenen Bildschirmen
steht unter Wayland in dieser Ausgabe nur die Ansicht zur Verfügung, damit
Eingaben nicht auf dem falschen Bildschirm landen. Für die vollständige
Steuerung mehrerer Monitore bitte eine X11-Sitzung verwenden. Die Wayland-
Unterstützung ist noch experimentell. Ein Zugriff vor der Linux-Anmeldung wird
in dieser Ausgabe nicht unterstützt.

Hintergrund und Updates

Unter Einstellungen kannst du den Hintergrundstart für deine Linux-Anmeldung
einrichten. Das Schließen des Hauptfensters lässt zRemote im Infobereich
weiterlaufen. Über „App beenden“ beendest du die Freigabe.

Updates zeigen ihren Downloadfortschritt an und prüfen die Herkunft und
Prüfsumme. Bei einer DEB- oder RPM-Installation fragt die Paketverwaltung nach deiner
Bestätigung. Die .run-Installation und portable Ausgaben aktualisieren sich
in ihrem eigenen Ordner. Geräte-ID und Einstellungen bleiben erhalten.
Es werden öffentliche Release-Dateien und der GitHub-Atom-Feed verwendet;
ein GitHub-Konto oder Token wird nicht benötigt.

Verbindungen laufen direkt zwischen den beteiligten Computern. Die Zumbyte-
Vermittlung überträgt Verbindungsangebote. Nach 90 Minuten endet eine Sitzung.
