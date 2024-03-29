---
title: Freifunk
---

## Links
- [Freifunk](https://freifunk.net/)
- [Freifunk Forum](https://forum.freifunk.net/)
- [Pico Peering Agreement](http://picopeer.net/)
- Braunschweig
  - [Freifunk Braunschweig](https://freifunk-bs.de/)
  - [Freifunk Firmware
    Braunschweig](http://firmware.freifunk-bs.de/)
  - [Freifunk Braunschweig Karte](https://freifunk-bs.de/map/)
  - [GitLab Stratum 0](https://gitli.stratum0.org/explore/projects)
  - Status des aktuellen Freifunk Routers (nur wenn
    verbunden):
    - <http://node.ffbs>
    - [http://[2001:bf7:382::1]/](http://[2001:bf7:382::1]/)

## Nummer 1 - TP-Link TL-WR841N
- Hardware: TP-Link TL-WR841N
- Hardware Version: 9.2
- Gekauft: gebraucht - April 2019
- Software: Freifunk Braunschweig installiert und eingerichtet
- Node Name: may-01
- Geo: 52° 13,495' N 010° 30,985' E
- Modifikation: in outdoor Gehäuse
- Map Link: <https://w.freifunk-bs.de/map/#!/de/map/14cc20702702>

## Nummer 2 - TP-Link TL-WR841N
- Hardware: TP-Link TL-WR841N
- Hardware Version: 9.1
- Gekauft: gebraucht - April 2019
- Modifikation: keine

## Nummer 5 - TP-Link TL-WR841N
- Hardware: TP-Link TL-WR841N
- Hardware Version: 9.0
- Gekauft: gebraucht - April 2019
- Modifikation: keine

## Nummer 6 - TP-Link TL-WR841N
- Hardware: TP-Link TL-WR841N
- Hardware Version: 11.1
- Gekauft: gebraucht - April 2019
- Modifikation: keine

## Nummer 7 - TP-Link Archer C7 (EU)
- Hardware: TP-Link Archer C7 (EU)
- Hardware Version: 4.0
- Gekauft: gebraucht - April 2019
- Software: Freifunk Braunschweig installiert und eingerichtet
- Node Name: may-parker-07
- Modifikation: keine

## Nummer 8 - AVM FRITZ!Box 4020
- Hardware: AVM FRITZ!Box 4020
- Hardware Version: -
- Hardware Besonderheit: 3 Antennen parellel, keine orthogonal - siehe
  auch hier:
  <https://openwrt.org/toh/avm/fritz.box.4020?s%5C#different_antenna_layouts>
- Gekauft: gebraucht - April 2019
- Software: Freifunk Braunschweig installiert und eingerichtet
- Node Name: may-08
- Konfiguration: kein Mesh-VPN
- Geo: 52° 13,502' N 010° 30,996' E
- Modifikation:
  - Gehäuse wurde geöffnet aber wieder geschlossen
  - hintere Schrauben wurden sehr unsauber ausgebohrt
  - unten wurden "Gitterstäbe" entfernt
- Map Link: <https://w.freifunk-bs.de/map/#!/de/map/5c49793fe8f4>

## Nummer 9 - AVM FRITZ!Box 4020
- Hardware: AVM FRITZ!Box 4020
- Hardware Version: -
- Hardware Besonderheit: 2 Antennen parellel, eine orthogonal - siehe
  auch hier:
  <https://openwrt.org/toh/avm/fritz.box.4020?s%5C#different_antenna_layouts>
- Gekauft: gebraucht - April 2019
- Modifikation:
  - Passiv POE Umbau - siehe Foto unten
  - USB Buchse ausgelötet - siehe Foto unten
  - WPS und WLAN Schalter abgekniffen - siehe Foto unten

{{< figure src="/img/docs/passiv-poe-umbau-fritz-box-4020.jpg" caption="Photo of the hardware modification" >}}

## Nummer 11 - AVM FRITZ!Box 4020
- Hardware: AVM FRITZ!Box 4020
- Hardware Version: -
- Hardware Besonderheit: 3 Antennen parellel, keine orthogonal - siehe
  auch hier:
  <https://openwrt.org/toh/avm/fritz.box.4020?s%5C#different_antenna_layouts>
- Gekauft: gebraucht - Mai 2019
- Node Name: may-11
- Modifikation: einige Rippen oben am Gehäuse waren gebrochen und
  wurden entfernt

## Nummer 13 -  Ubiquiti UniFi AC MESH - UAP-AC-M
- Hardware: Ubiquiti UniFi AC MESH - UAP-AC-M
- Gekauft: gebraucht (wie neu) - September 2022
- Node Name: may-13
- Map link: <https://freifunk-bs.de/map/#!/de/map/68d79a0b15ce>

## Router
Warning: Devices with ≤4MB flash and/or ≤32MB ram will work but they will be very
limited (usually they can't install or run additional packages) because
they have low RAM and flash space. Consider this when choosing a device
to buy, or when deciding to flash OpenWrt on your device because it is
listed as supported. Also see:
<https://openwrt.org/supported_devices/432_warning>

### TP-Link TL-WR841N/ND
- Speicher: 4MB Flash, 32MB RAM :\!:
- Aufgrund des relativ kleinen 4MB Flash-Speichers ist die weitere
  Kompabilität zu zukünftigen Updates offen
- Unterstützung zur Zeit nur bis Version 12 - Version 13 oder höher
  geht noch nicht
- OpenWRT Link: <https://openwrt.org/toh/tp-link/tl-wr841nd>
- Versionen von FF BS unterstützt: 3, 5, 7 bis 12
- Original Firmware Download:
  <https://www.tp-link.com/no/support/download/tl-wr841nd/>

### Archer C7 AC1750
- Speicher
  - Version 1: 8MB Flash, 128MB RAM
  - Version 2 bis 5: 16MB Flash, 128MB RAM @ 720MHz bis 775MHz
- Achtung: Für FFBS gibt es nur die Firmware in Version 2, 4 und 5
- Empfehlungen
  - <https://wiki.freifunk-franken.de/w/Portal:Hardware>
- OpenWRT Seite: <https://openwrt.org/toh/tp-link/archer-c7-1750>
- TP-Link Support:
  <https://www.tp-link.com/de/support/download/archer-c7/>

### AVM FRITZ\!Box 4020
- Speicher: 16MB Flash, 128MB RAM @ 750MHz
- OpenWRT Seite: <https://openwrt.org/toh/avm/fritz.box.4020>

### AVM FRITZ\!Box 4040
- Speicher: 32MB Flash, 256MB RAM
- OpenWRT Seite: <https://openwrt.org/toh/avm/avm_fritz_box_4040>

### TP-Link CPE210
- Achtung: Nur Version 1 und 2 - nicht Version 3
- Speicher: 8MB Flash, 64MB RAM
- Empfehlungen
  - <https://wiki.freifunk-franken.de/w/Portal:Hardware#TP-Link_CPE210>
- OpenWRT Seite: <https://openwrt.org/toh/tp-link/cpe210>

### Unifi
- OpenWRT Link: <https://openwrt.org/toh/ubiquiti/unifiac>
- Unifi Vergleich:
  <https://help.ubnt.com/hc/en-us/articles/360008036574-UniFi-Access-Point-Comparison-Charts>
- Router flashen:
  <http://www.netz39.de/wiki/freifunk:anleitungen:ubiquitigeraete>

#### Unifi AC Lite
- Empfohlen <https://darmstadt.freifunk.net/mitmachen/unterstuetzte-geraete/>

#### UniFi AC Mesh
- Empfohlen <https://darmstadt.freifunk.net/mitmachen/unterstuetzte-geraete/>

### TP-Link TL-WR1043N/ND
- Speicher
  - Version 1: 8MB Flash, 32MB RAM :\!:
  - Version 2 bis 5: 8MB bis 16MB Flash, 64MB RAM
- Empfehlungen
  - <https://www.chemnitz.freifunk.net/static-mitmachen/>
  - <https://ffmuc.net/wiki/p/Router#TP-Link_TL-WR1043N.2FND>
  - <https://www.freifunk-donau-ries.de/2016/05/26/neue-routerbestellung-ist-da/>
  - <https://www.freifunk-uelzen.de/router-empfehlungen/>
  - <https://www.freifunk-bochum.de/mitmachen/der-router/>
- OpenWRT Seite: <https://openwrt.org/toh/tp-link/tl-wr1043nd>
- Maximale Anzahl Clients (Erfahrungswert): \> 45
  -[Quelle](https://ffmuc.net/wiki/p/Router#TP-Link_TL-WR1043N.2FND)
- Softwarefehler beim Booten - sichere Trennung zwischen lokalen
  Netzwerk und externen Netzwerk nicht gegeben
  -[Quelle](https://ffmuc.net/wiki/p/Router#TP-Link_TL-WR1043N.2FND)

### TP-Link TL-WDR4300
- Speicher: 8MB Flash, 128MB RAM
- OpenWRT Link: <https://openwrt.org/toh/tp-link/tl-wdr4300>

### TP-Link TL-WDR3600
- Speicher: 8MB Flash, 128MB RAM
- Probleme mit Version 1.5: <https://dev.archive.openwrt.org/ticket/21593#ticket>
- OpenWRT Link: <https://openwrt.org/toh/tp-link/tl-wdr3600>
- sehr alt - wird nicht mehr hergestellt

## Outdoor Box
- <https://wiki.freifunk.net/Outdoorf%C3%A4higen_Router_basteln>
- <https://wiki.freifunk.net/Outdoor_Box>
- <https://wiki.freifunk.net/DIY_Halterung>
- <https://wiki.darmstadt.freifunk.net/DIY_TL-WR842ND_Outdoor_Box>
- <https://wiki.darmstadt.freifunk.net/DIY_TL-WR841N_Outdoor_Box>
- <http://wiki.leipzig.freifunk.net/Gehaeuse>
- <https://forum.freifunk.net/t/umbau-tl-wr841nd-fuer-outdoor-einsatz/2077>
- <https://www.youtube.com/watch?v=v1fI3JdK8gg>

## TP-Link TL-WR841N & TL-WR841ND Abmessungen
- Platine:
  - Tief: 17 mm
  - Breit: 125 mm
  - Breit (mit unterboden): 132 mm
  - Hoch (ohne Stecker und mit abgetrennten Schaltern): 98 mm
  - Hoch (mit Steckern leicht gequetscht): 130 mm
