---
layout: post
title:  "Experiment: Installation von Glassfish mit MySQL-DB auf einem Raspberry Pi 2"
date:   2015-07-26 11:55:00 +0100
categories: raspberry
---
# Vorbereitung

## Die Motivation

Im Zusammenhang mit einem weiteren Projekt möchte ich gern prüfen, ob und wie gut ein Glassfish Server mit MySQL auf einem neuen Raspberry Pi 2 laufen kann. (Notiz: Gewisse Schritte bis des Raspberry selbstständig läuft sind Mac spezifisch)

## Der Plan

Der Plan ist eine für Raspberry Pi angepasste Variante von Debian Wheezy zu verwenden. Bisher habe ich nur Ubuntu für meine Linux-Installationen verwendet, jedoch kommt Debian bereits mit einem installieren Java 7 von dem ich mir eine Erleichterung der Installation verspreche.  Bei Glasfish werde ich die neueste Version des JavaEE-Web-Profiles verwendet. Das Web-Profile reicht für fast alle Anwendungsfälle und ist weniger Arbeitsspeicher intensiv.  Die Datenhaltung soll auf einem MySQL Server Community Edition geschehen. MySQL sollte einfach per Paketmanager nachinstallierbar sein.

## Das Shopping

Die Testinstallation besteht aus den unten aufgeführten Geräten (5 Volt Micro USB Netzteil nicht enthalten):
 * Raspberry Pi Typ 2 Entwicklermainboard Preis: 48 CHF * Gehäuse MC-RP002-CLR zu Raspberry Pi B+ Preis: 13.85 CHF * SAMSUNG Speicherkarte micro SDHC 32GB EVO Anmerkung: Diese SD-Karte ist zu GROSS für das Gehäuse!!! Ich musste beim Gehäuse ein Teil abbrechen damit die SD-Karte platz hat. Preis: 24.90 CHF
 * Logitech USB-Tastatur (Linux zertifiziert) Anmerkung: Anschaffung nachdem mein Wireless-Keyboard nicht erkannt wurde. Preis: 14.90 CHF
 Der Anschaffungspreis beläuft sich damit auf 101.65 CHF.
 # Umsetzung

## Passwortverwaltung

Bei der Installation werden/sollen an verschiedenen Stellen Passwörter benötigt. Insbesondere wichtig sind die Passwörter für den Linux Benutzeraccount, den MySQL-Sever und den Glasfish-Sever.
 Zu Verwaltung dieser Passwörter verwende ich den Passwort-Manager 1Passwort:
 ![Screenshot](/assets/96af1-bildschirmfoto2015-03-14um10.png) 
Jedes Passwort ist generiert und hat 20+ Stellen (Keine genaue Angaben aus Sicherheitsgründen :)).

## Flashen der SD-Karte mit RASPBIAN

Anmerkung; Der erste Versuch dieser war RASBIAN per DD direkt auf die Flash-Karte zu bringen. Leider bricht der Startvorgang beim Laden der USB-Geräte dann ab und bleibt stehen. Das ist einbekanntes Phänomen. Aus diesem Grund habe ich die Installation via NOOBS wie folgt via NOOBS vollzogen.

Ich verweise dazu auf die (sehr gute) offizielle Anleitung auf RASPBERRY.ORG: NOOBS SETUP

Nach der Installation von NOOBS kann man die SD-Karte in Raspberry Pi einsetzten und erhält beim ersten Start die Option ein Betriebsystem seiner Wahl herunterzuladen.

Meine Wahl ist aus den oben genannten Gründen natürlich RASBIAN.

## Update der Installation

Normalerweise sind die Images aus dem Internet nicht am aktuellsten, deshalb lohnt es sich nach dem ersten Start ein Update durchzuführen:

    sudo apt-get update && sudo apt-get upgrade

## Konfiguration der Installation

Ausführen von:

    sudo raspi-config
    
Und setzten von folgenden Optionen:

* Expandieren der Partition auf die maximale Grösse
* Setzten von Sprache und Region
* CPU-Speed auf „High" setzten (Optional)

Erweiterte Optionen:
* Netzwerkname des Pi setzten
* „Memory Split" auf 16mb setzten (Mehr Memory für den Server, weniger für die Grafikkarte)
* SSH aktivieren

## Raspberry Pi Firmware-Update

Die Firmware des Raspberry Pi übersetzt bei der Steuerung der Hardware die Befehle des Betriebssystems im Hardware spezifische Anordnungen. Sollte ein Gerät nicht funktionieren kann das an der fehlenden Unterstützung seitens der Firmware liegen und ein Update wird nötig. Dabei ist es egal ob Raspbian, OpeneElec oder eine andere Distribution verwendet wird.

Das offizielle Repository der Raspberry Firmware auf GitHub frei verfügbar.

Mit folgendem Befehl kann auf der Hardware der aktuelle Stand der Firmware abgefragt werden:

    sudo uname -a

Je nach dem wie alt die Firmware im Vergleich zum aktuellen Stand ist lohnt sich ein Firmware upgrade.

Für das Firmwareupdate gibt es von Hexxeh ein Updateskript das uns die aktuellste Firmware herunterlädt und installiert. Dazu wird Git benötigt.

***Schritt 1:*** Installation von Git:

    sudo apt-get install git

***Schritt 2:*** Herunterladen des Scripts von dem Repository von Hexxeh:

    sudo wget https://raw.github.com/Hexxeh/rpi-update/master/rpi-update -O /usr/bin/rpi-update && sudo chmod +x /usr/bin/rpi-update
***Schritt 3:*** Ausführen des Scripts:

    sudo rpi-update
    
***Schritt 4:*** Neustart des Systems:

    sudo reboot
    
## Installation von MySQL

Der nächste Schritt ist den MySQL-Server gegen aussen aufzumachen. Ich möchte aus dem privaten Netzwerk von meiner Entwicklungsinstallation direkt auf MySQL zugreifen können. 
Dazu muss als erstes die Datei my.cnf angepasst werden:

    vi /etc/mysql/my.cnf

Dort muss folgende Zeile auskommentiert werden (Heiss ein # vor die Zeile). Dieser Eintrag sorgt dafür, dass nur Verbindungen vom eigenen Server angenommen werden.

    bind-address = 127.0.0.1

Der nächste Schritt ist die Berechtigung des root-Benutzers für den Netzwerkzugriff (Ja, keine Best-Practice). Der erste Schritt dazu ist das Login im Server via MySQL-Client:

    mysql --user=root

Dann das Berechtigen des Benutzers (Anmerkung: Den Text passwort durch das richtige Passwort ersetzten!):

    GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'password' WITH GRANT OPTION;
    
Und einen Neustart des MySQL-Servers nach dem Ausstieg aus dem Client:

    sudo /etc/init.d/mysql restart

Damit ist die Installation des MySQL-Servers abgeschlossen und es sollte der Zugriff via Client von anderes Computers möglich sein:

![Screenshot](/assets/6dee4-bildschirmfoto2015-03-14um11.png)

## Installation von Glasfish 4 Web-Profile

Download der aktuellen Version von Glasfish (Web-Profile)

    wget http://dlc.sun.com.edgesuite.net/glassfish/4.1/release/glassfish-4.1-web.zip

Entpacken des herruntergeladenen Archivs

    unzip glassfish-4.1*zip

Anpassen der Berechtigungen damit die Dateien des Servers ausführbar sind

    chmod -R 777 glassfish4

Start des Glasfish-Servers nach dem Entpacken

    glassfish4/bin/asadmin start-domain

Initialer start der Glasfish Domain

    glassfish4/bin/asadmin start-domain

Initiale Passwortänderung

    glassfish4/bin/asadmin change-admin-password

Aktivierung des Remote-Zugriffs auf den Administrationsport des Glasfish Servers

    glassfish4/bin/asadmin enable-secure-admin

Neustart der Glasfish Domain damit die Änderung aktiv werden

    glassfish4/bin/asadmin stop-domain
    glassfish4/bin/asadmin start-domain
  
## Ergebnis

Das Ergebnis dieses Experiments ist, dass es möglich ist auf einem Raspberry-Pi2 einen Glasfish 4 Server und eine MySQL Datenbank zu bereiben.

Die Performance ist bestenfalls OK und das starten und beenden des Glasfish Servers dauert sehr lange. Da es sich dabei aber um einen 50 CHF Computer handelt der auf einem 5V Netzteil läuft halte ich dies für einen Erfolg.

Bei Gelegenheit gibt es noch einene Follow-Up-Post mit detailierten Performancemessungen.
    
