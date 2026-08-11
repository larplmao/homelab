# WireGuard

## Beschreibung

Ich verwende WIreguard als VPN in meinem Homelab, um von ausserhalb sicher auf mein internes Netzwerk und die darin betriebenen Dienste zuzugreifen.

Fuer die Verwaltung wird wg-easy mit einer WEB-GUI verwendet.

---

## Netzwerk

### Heimnetz

- Netzwerk: 		``` 192.168.1.0/24```
- Gateway:  		``` 192.168.1.1   ```
- Raspberry Pi:		``` 192.168.1.20  ```

### Wireguard

- VPN-Netzwerk:		``` 10.8.0.0/24 ```
- Wireguard Port:	``` 51820/UDP   ```
- WEG-GUI: 		``` 51821/TCP	```

Die VPN-Clients erhalten eine IP aus dem Wireguard-Netzwerk, zb: ``` 10.8.0.2 ```

---
 
## Verzeichnisstruktur
```
wireguard/
|-- compose.yaml
|-- README.md
|-- .gitignore
|__ data/
```
---

## Docker Compose

Wireguard wird ueber Docker Compose betrieben.

Das verwendete Image ist:
```ghcr.io/wg-easy/wg-easy:15```

## Konfiguration

Die grundlegende Konfiguration wird ueber die WEB-GUI von wg-easy vorgenommen.

Aktuelle Einstellungen: 

- Oeffentliche IPv4: aktuelle von ISP zugeteilte IPv4 Adresse
- Wireguard-Port: ``` 51820/UDP    ```
- VPN-Netzwerk:   ``` 10.8.0.0/24  ```
- Pi-hole DNS: 	  ```192.168.1.20  ```
- IPv6: deaktiviert

---

## Web-GUI

Die Weboberflaeche ist innerhalb des lokalen Netzwerks erreichbar und laeuft ueber den Port 51821.

---

## Portweiterleitung

Damit Wireguard ausserhalb meines Netzwerks erreichbar ist, wird auf dem Router folgende Portweiterleitung eingerichtet:

- Protokoll: 	 ``` UDP 	 ```
- Externer Port: ``` 51820	 ```
- Interner Port: ``` 51820	 ```
- Ziel-IP:	 ``` 192.168.1.20```

---

## Sicherheit

- Nur UDP-Port 51820 wird aus dem Internet weitergeleite.t
- Die wg-easy WEB-GUI ist nicht oeffentlich erreichbar.
- IPv6 ist deaktiviert.
- Wireguard verwendet individueelle schluessel fuer jeden Client.
- Private Keys werden nicht in Git gespeichert.
- .env und sensible Daten werden ueber .gitignore ausgeschlossen.
