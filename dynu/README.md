# Dynu Updater

---

## Beschreibung

Dynu wird als Dynamic-DNS-Dienst verwendet.

Da sich die oeffentliche IPv4-Adresse des Internetanschlusses aendern kann, stellt Dynu einen festen Hostname bereit, werlcher automatisch auf die aktuelle oeffentliche IPv4-Adresse zeigt.

Der Dynu-Hostname wird nur fuer den externen Zugriff auf Wireguard-VPN verwendet.

---

## Hostname

Aktueller Dynu-Hostname:
```
homelab-2405.opik.net
```
Der Hostname zeigt auf die aktuelle oeffentliche IPv4-Adresse des Internetanschlusses.

---

## Zweck

Der Dynu-Hostname wird als Endpoint fuer Wireguard verwendet:
```
homelab-2405.opik.net:51820
```
Dadurch muss die oeffentliche IPv4-Adresse nicht direkt in den Wireguard-Client-Konfigurationen hinterlegt werden und man schliesst somit aus das diese, bei einem Wechsel der oeffentlichen IPv4-Adresse nicht aufhoert zu funktionieren.

---

## Docker

Das verwendete Image ist:
```
longkeyy/dynu-updater:1.1
```

---

## Verzeichnisstruktur
```
dynu/
|-- compose.yaml
|-- .env
|-- .gitignore
|__ README.md
```

---

## Konfiguration

Der Dynu-Updater verwendet:

- Dynu Username
- Dynu IP Update Password
- Dynu Hostname

Das IP Update Password wird verwendet, damit das normale Dynu-Account-Passwort nicht auf dem Raspberry Pi hinterlegt werden muss.

Das Passwort wird fuer den verwendeten Updater als SHA-256-Hash gespeichert.


