# Pi-hole

---

## Beschreibung

Ich nutze Pi-hole als Networkwide DNS-Server mit integriertem AD-Tracker Blocker

---

## Ports

| Port | Protokoll | Beschreibung    |
|------|-----------|-----------------|
| 53   | TCP       | DNS             |
| 53   | UDP       | DNS             |
| 80   | TCP       | Weboberflaeche  |
| 67   | UDP       | DHCP	     |

---

## Verzeichnisstruktur

```
pihole/
|-- compose.yaml
|-- .env
|-- .env.example
|-- README.md
|__ data/
```

---

## Volumes

| Host     | Container     | Beschreibung                      |
|----------|---------------|-----------------------------------|
| "./data" | "/etc/pihole" | Persistente Pi-hole Konfiguration |

---

## .env

| Host     | Container     | Beschreibung                      |
|----------|---------------|-----------------------------------|
| "./data" | "/etc/pihole" | Persistente Pi-hole Konfiguration |

---

## Docker-Netzwerk

Eigenes Bridge-Netzwerk:
- "dns"

---

## Backup

Alle Konfigurationsdateien befinden sich im Ordner`:

```
data/
```

---

## Git-Struktur

In der Repository werden folgende Dateien **NICHT** versioniert:

- ```.env```
- ```data/*```

Ausgenommen:

- ```data/.gitkeep```

---
