# Actual Budget

## Beschreibung

Actual Budget ist eine selbst gehostete Anwendung zur Verwaltung
persönlicher Finanzen und Budgets.

Der Dienst wird auf dem Raspberry Pi über Docker Compose betrieben
und über Caddy intern mit HTTPS bereitgestellt.

## Zugriff

- URL: https://budget.homelab
- Reverse Proxy: Caddy
- Interner Container-Port: 5006
- Docker-Netzwerk: proxy-network

Der Dienst ist nicht direkt über einen veröffentlichten Host-Port
erreichbar.

## Voraussetzungen

- Raspberry Pi mit Docker und Docker Compose
- Bestehendes Docker-Netzwerk `proxy-network`
- Caddy als Reverse Proxy
- Pi-hole für die interne DNS-Auflösung

## Verzeichnisstruktur

```text
actual-budget/
├── compose.yaml
├── README.md
└── data/
    └── .gitkeep
```

## Sicherheit

- Zugriff nur über das interne Homelab beziehungsweise VPN.
- Keine direkte Veröffentlichung des Container-Ports.
- HTTPS über Caddy mit interner Zertifizierungsstelle.
- Serverpasswort bei der ersten Einrichtung setzen.
