zRemote für Linux
=================

Installation

Lade das DEB-Paket für deinen Computer herunter und öffne es mit der
Paketverwaltung. Danach findest du zRemote im Anwendungsmenü. Unterstützt
werden Ubuntu 22.04 oder neuer und vergleichbare Debian-Systeme.

Für andere Distributionen gibt es das portable TAR.GZ-Paket. Entpacke es in
einen beschreibbaren Ordner und öffne darin „zRemote“. Der Ordner muss bei
einem Update erhalten bleiben. Für den geschützten Gerätespeicher muss der
Anmeldeschlüsselbund des Desktops verfügbar sein.

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
Prüfsumme. Bei einer DEB-Installation fragt die Paketverwaltung nach deiner
Bestätigung. Portable Ausgaben aktualisieren sich in ihrem eigenen Ordner.
Geräte-ID und Einstellungen bleiben erhalten.

Verbindungen laufen direkt zwischen den beteiligten Computern. Die Zumbyte-
Vermittlung überträgt Verbindungsangebote. Nach 90 Minuten endet eine Sitzung.
