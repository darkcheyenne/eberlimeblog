---
layout: post
title:  "Wilkommen auf eberli.me"
date:   2015-01-03 11:55:00 +0100
categories: Synology
---
# Einleitung
Ich besitzte seit ca. 6 Monaten einen Synology NAS vom Typ DS214. Der DS214 ist ein NAS mit 2 Festplatten der von Synology als NAS für die Privatnutzung oder für kleine KMU eingestuft wird.

Ich habe meinen NAS bis vor einigen Wochen nur für die Speicherung von Daten verwendet und bin aktuell daran mich mit den erweiterten Möglichkeiten des Synology NAS zu beschäftigen.

# Ziele

Ich möchte kurz- oder langfristig folgende Funktionen meines Synology NAS austesten.

* VPN
* E-Mail-Server
* Backup via Amazon Glacier
* Privater Video-Server
* Photo Server mit Konten für Verwandte

# Ausgangslage
## Vorbereitungen
Ich spiele bereits seit längerer Zeit mit dem Gedanken die obene genannten Dinge zu testen, habe aus Umsetzen aus Zeitgründen immer in die Zukunft verschoben, ich habe jedoch über die Monate bereite diverse Vorbereitungen getroffen:

* ***Custom-Domain*** Ich habe mir bei einer Weihnachtsaktion die Domain eberli.me bei Hover.com gekauft. Der Gründ dafür ist, dass ich komplette Kontrolle über den DNS-Record will wenn ich mit MX-Records oder Subdomains experimentieren will. 
* ***Mailbox*** für Custom-Domain Weiterhin verkauft Hover für relativ wenig Geld Mailboxen (20$/Jahr). Der Grund für diese Mailbox ist, dass Personen die mit eine Mail schreiben einen NDR (Non-Delivery-Reply) erhalten wenn mein NAS nicht erreichbar ist. Stattdessen soll es einen Fail-Over zur Mailbox von Hover geben.
* ***Hardware*** Ich habe mir damit diese Versuche stattfinden kann einen Synology DS214 gekauft. Ich hatte früher eine Synology DS407 aus dem Jahr 2007, diese ist jedoch nicht mehr im Update-Zyklus. In der DS214 sind zwei Western Digital WD30EURS Festplatten mit 3 TB pro Einheit.

## Zugriffskonzept

Weiterhin möchte ich über meine Überlegungen zur Sicherheit sprechen. Ich möchte nicht, dass mit Ausnahme der Bilder die ich mit meinen Verwandten teilen möchte irgendwelche Informationen ungeschützt über das Internet fliegen. Aus diesem Grund unterteile ich den Zugriff auf meinen NAS in drei geographische Zonen:

### Zugriff von Überall

* SMTP (Port 25): Damit SMPT-Server mir Mail zustellen können und ich praktisch aus jedem Land Mails erhalten kann sind diese Port offen
* SMTP SSL (Port 465): Gleiches gilt für SMTP mit SSL-Verschlüsselung 
* SMTP TSL (Port 587): Und für SMTP mit TSL-Verschlüsselung 

### Zugriff auf der Schweiz (Via GEO-IP)

* VPN: VPN erfolgt über L2TP/IPSec und wird nur von mir selbst genutzt (Und ich bin 99% meiner Zeit innerhalb der Schweiz)
* Photo Station: Die Verwandtschaft mit der ich Bilder teilen möchte kommt ebenfalls aus der Schweiz

### Zugriff aus dem lokalen Netzwerk (Ink. wenn im VPN eingeloggt)

Alle weitern Dienste werden nur von mir selbst genutzt und brauchen nur durch VPN oder aus meiner eigenen Wohnung herraus erreichbar zu sein. Dazu gehören:

* Datenzugriff: Datenzugriff via CIFS oder WebDAV
* Video Station: Eigentlich nicht zwingend Schützenswert, aber ich sehe keinen Grund warum ich nicht einfach VPN aufmachen kann
* Mail-Zugriff: Zugriff auf die Mails via IMAP
* Konfiguration: Zugriff auf das Konfigurations-WebGUI des Synology NAS

## Weitere Sicherheitsüberlegungen

* Automatische Blockierung: Der Synology NAS bietet eine Funktion zur automatischen, temporären Sperrung von IP-Addresse von denen innerhalb kurzer Zeit viele falsche Passwortanfragen kommen. Diese Funktion wirft hemmt die Brauchbarkeit von Brute-Force-Angriffen stark.
* HTTPS: Ich hätte gern ein SSL-Zertifikat für eberli.me damit auch die Verbindungen auf die Fotos alle in HTTPS (Also Verschlüsselt) stattfinden.


