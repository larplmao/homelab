# Caddy

---

## Beschreibung

Caddy wird als Reverse Proxy fuer die internen Dienste des Homelabs verwendet.

Caddy stellt die Dienste ueber interne Domains bereit und uebernimmt dabei die HTTPS-Verschluesselung.

---

## Domains

Aktuell verwendete Domains:

  - `https://portainer.homelab/`
  - `https://uptime.homelab/`
  - `https://pihole.homel`
  - `https:// wireguard.homelab`


Die Domains werden ueber Pi-hole auf die IP-Adresse des Raspberry Pi aufgeloest.

---

## Zweck

Caddy dient als zentraler Einstiegspunkt fuer die Weboberflaechen der internen Dienste.

Anstatt die einzelnen Ports direkt aufzurufen, werden die Dienste ueber HTTPS und die jeweiligen Domains erreicht.

---

## HTTPS

Fuer die internen `.homelab` Domains wird eine eigene Caddy Certificate Authority verwendet.

Die Clients muessen das Caddy Root-Zertifikat als vertrauenswuerdige Stammzertifizierungsstelle installieren.

---

## Docker

Das verwendete Image ist:

- `caddy:latest`

Caddy verwendet das externe Docker-Netzwerk:

- `proxy-network`

Dadurch kann Caddy direkt auf die entsprechenden Docker-Container zugreifen.

---

## Verzeichnisstruktur
```
caddy/
|-- compose.yaml
|-- Caddyfile
|-- .gitignore
|-- data/
|-- config/
|__ README.md
```
---

## Konfiguration

Die Reverse-Proxy-Regeln werden im `Caddyfile` definiert.
