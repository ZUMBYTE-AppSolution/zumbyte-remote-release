# Zumbyte Remote in Community Apps einreichen

Das öffentliche Repository ist `https://github.com/ZUMBYTE-AppSolution/zumbyte-remote-release`.

| Datei | Zweck |
|---|---|
| `ca_profile.xml` | Beschreibung und Support des Anbieters im Repository-Stamm |
| `templates/zumbyte-remote.xml` | Eine Docker-Vorlage für Zumbyte Remote |
| `LICENSE` | MIT-Lizenz für XML-Vorlagen und Repository-Dokumentation; keine Umlizenzierung der Anwendung |
| `assets/app-icon.png` | App- und Repository-Icon |
| `docs/UNRAID.md` | Einrichtung, HTTPS, Datenverzeichnis und Updates |

Die XML verwendet ein festes GHCR-Versionstag, Port 8787, Appdata unter `/data`, UID 99/GID 100 und einen Container ohne Privilegien oder Docker-Socket. Die eigene HTTPS-Adresse muss beim Installieren eingetragen werden. Die Netzwerkauswahl kann in Unraid auf eine eigene br0-Adresse geändert werden; die bestehende Container-IP wird durch eine neue Vorlage nicht geändert.

Vor der Einreichung muss das Containerpaket öffentlich sein und anonym von GHCR geladen werden können. Ein erfolgreicher Build allein reicht dafür nicht. Bei einer neuen Node.js-/Linux-Basis die Vorlage auf ein neues geprüftes Image-Tag aktualisieren. Die Anwendung im Container kann ihre signierten Updates weiterhin ohne GitHub-API laden.

## Einreichen

1. [Community Apps öffnen](https://ca.unraid.net/submit), anmelden und eine neue Einreichung beginnen.
2. Als Repository `ZUMBYTE-AppSolution/zumbyte-remote-release` und Branch `main` angeben.
3. **Validate** ausführen. Es müssen genau die gewünschte Docker-Anwendung und das Anbieterprofil gefunden werden.
4. **Scan** ausführen und Hinweise zum Image, zu XML-Feldern und Links bearbeiten.
5. Vorschau, Alpha-Kennzeichnung, Support und Darstellung prüfen und anschließend zur Prüfung einreichen.

Die Veröffentlichung in Community Apps erfolgt nach deren Prüfung. Das Vorhandensein der XML-Dateien bedeutet noch keinen Katalogeintrag. Es wird kein Unraid-Plugin veröffentlicht; deshalb ist keine `.plg` oder Plugin-XML erforderlich. Weitere Anwendungen erhalten jeweils eine eigene Container-XML. Die Community-Apps-Anmeldung und Einreichung werden nicht über ein fremdes Konto stellvertretend durchgeführt.

Referenzen: [Einreichung](https://ca.unraid.net/submit/help), [Container-XML](https://ca.unraid.net/submit/help/repository-xml), [Anbieterprofil](https://ca.unraid.net/submit/help/repository-info-xml), [Feldreferenz](https://ca.unraid.net/submit/help/xml-field-reference).
