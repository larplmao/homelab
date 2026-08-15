# Homarr
---

## Beschreibung

Homarr ist ein Dashboard zur zentralen Verwaltung und Übersicht der Dienste im Homelab.

Es dient als zentrale Startseite für die verschiedenen Services und zeigt zusätzlich Informationen und Statistiken über integrierte Dienste an.

---

## Zweck

Homarr dient als zentrale Übersicht und ermöglicht den schnellen Zugriff auf die verschiedenen Dienste im Homelab.

Die Weboberfläche ist nur über das interne Netzwerk bzw. über WireGuard erreichbar.

---

## Docker

Homarr läuft als Docker-Container.

Image: 
- `ghcr.io/homarr-labs/homarr:latest`
Port: 
- `7575`

---

## Verzeichnisstruktur
```
homarr/
├── compose.yaml
├── .env
└── appdata/
```
---

## Konfiguration

Die persistenten Homarr-Daten werden im Verzeichnis `appdata/` gespeichert.

Der Docker Socket wird eingebunden, damit Homarr Docker-Container erkennen und entsprechende Informationen anzeigen kann.

Die `SECRET_ENCRYPTION_KEY` wird über die `.env` Datei bereitgestellt und nicht in GitHub gespeichert.

## Netzwerk

Homarr ist mit dem externen Docker-Netzwerk `proxy-network` verbunden.

Der Zugriff erfolgt intern über Caddy:

`https://home.homelab`

Caddy übernimmt dabei das interne HTTPS und den Reverse Proxy.
