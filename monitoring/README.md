# Monitoring

--

## Beschreibung

Das Monitoring-System dient zur Überwachung des Raspberry Pi und der
darauf laufenden Docker-Container.

Prometheus sammelt die Metriken, während Grafana diese übersichtlich
visualisiert.

--

## Dienste

- Prometheus
- Grafana
- Node Exporter
- cAdvisor

--

## Zweck

Das Monitoring dient zur Überwachung des Homelab-Systems.

Dabei werden sowohl Systemressourcen des Raspberry Pi als auch
Ressourcen und Zustände der Docker-Container überwacht.

--

## Docker

Das Monitoring läuft vollständig über Docker.

Alle Dienste befinden sich im externen Docker-Netzwerk:

-  `proxy-network`

--

## Verzeichnisstruktur

monitoring/
├── compose.yaml
├── prometheus/
│   ├── prometheus.yml
│   └── data/
└── grafana/

--

## Prometheus

Prometheus sammelt die Metriken der verschiedenen Monitoring-Quellen.

Die Abfrage erfolgt standardmässig alle 15 Sekunden.

Überwachte Targets:
`
- `prometheus:9090`
- `node-exporter:9100`
- `cadvisor:8080`

--

## Node Exporter

Node Exporter stellt Systemmetriken des Raspberry Pi bereit.

Überwacht werden unter anderem:

- CPU-Auslastung
- RAM-Auslastung
- Swap
- Speicherplatz
- Netzwerk
- Disk I/O

--

## cAdvisor

cAdvisor stellt Metriken über die Docker-Container bereit.

Überwacht werden unter anderem:

- CPU-Auslastung pro Container
- RAM-Auslastung pro Container
- Netzwerktraffic
- Disk I/O
- Container-Uptime
- Container-Status

## Grafana

Grafana dient zur Visualisierung der von Prometheus gesammelten
Metriken.

Zugriff:

- `https://grafana.homelab`

Verwendete Dashboards:

- Node Exporter Full
- Docker / cAdvisor Monitoring

--

## Netzwerk

Prometheus und Grafana kommunizieren intern über das Docker-Netzwerk:

- `proxy-network`

Grafana wird über Caddy erreichbar gemacht:

- `https://grafana.homelab`

Prometheus selbst wird nicht über Caddy veröffentlicht.

--

## Homarr

Grafana ist als App in Homarr eingebunden.

Dadurch kann das Monitoring direkt vom Homarr-Dashboard aus geöffnet
werden.

--

## Konfiguration

Die Prometheus-Konfiguration befindet sich unter:

- `prometheus/prometheus.yml`

Die Grafana-Daten und Einstellungen werden dauerhaft unter `grafana/` gespeichert:

Sensible Zugangsdaten werden nicht in GitHub gespeichert.
