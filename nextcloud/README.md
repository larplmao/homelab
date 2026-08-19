# Nextcloud
---

## Beschreibung

Nextcloud ist eine private Cloud-Lösung zur Speicherung und Verwaltung von Dateien.

Sie ermöglicht mehreren Benutzern den Zugriff auf gemeinsame und persönliche Dateien sowie weitere Funktionen wie Kalender, Kontakte und Notizen.

---

## Dienste

- Dateispeicher
- Benutzerverwaltung
- Dateifreigaben
- Kalender
- Kontakte
- Notizen

---

## Zweck

Nextcloud dient als private Cloud im Homelab.

Die Daten werden auf der angeschlossenen 2-TB-Festplatte gespeichert.

Der Zugriff erfolgt nur über das interne Netzwerk bzw. über WireGuard.

---

## Docker

Nextcloud läuft als Docker-Container.

Image: `nextcloud`
Port: `80`

Für die Datenbank wird ein separater Docker-Container verwendet.

---

## Verzeichnisstruktur

```
nextcloud/
├── compose.yaml
├── .env
├── .gitignore
├── app/
└── db/
```
---

## Speicher

Die Nextcloud-Daten werden auf der externen 2-TB-Festplatte gespeichert.

`/mnt/cloud-data`

Dadurch bleiben die Benutzerdaten unabhängig vom Speicher des Raspberry Pi.

---

## Konfiguration

Die Konfiguration und Zugangsdaten werden über Docker Compose und die .env Datei verwaltet.

Sensible Daten wie Passwörter und Secrets werden nicht in GitHub gespeichert.

---

## Netzwerk

Nextcloud ist mit dem externen Docker-Netzwerk `proxy-network` verbunden.

Der Zugriff erfolgt intern über Caddy:

`https://cloud.homelab/`

Caddy übernimmt dabei das interne HTTPS und den Reverse Proxy.
