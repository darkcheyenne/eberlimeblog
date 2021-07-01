---
layout: post
title:  "Erfahrungsbericht: Zimbra Collaboration Suite auf einer Amazon EC2 Micro Instance"
date:   2013-12-10 11:55:00 +0100
categories: Cloud
---
# Ausgangslage
Installation von Zimbra Collaboration Server Open Source Edition 8.0.5 GA auf einer Amazon EC2 Micro Instance mit Ubuntu x64

* 613 MiB Arbeitsspeicher

* Bis zu EC2 Recheneinheiten (für kurze periodische Bursts)

* Nur EBS-Speicherung

* 64-Bit-Plattform

* API-Name: t1.micro

* Disk: 8GB Elastic Storage Volume

# Vorgehen
## Update von Ubuntu
sudo apt-get update sudo apt-get upgrade

## Installation der Pre-Requisites
sudo apt-get install libgmp3c2 libperl5.14 pax sysstat sqlite3

## Anpassen des Hostnamen und der Hosts-Datei
	sudo vi /etc/hostname 
	sudo vi /etc/hosts 127.0.0.1 localhost.localdomain localhost 172.31.14.114 #DNS-Name# #Hostname# 
	sudo init 6

## Installation der Software
	wget http://files2.zimbra.com/downloads/8.0.5_GA/zcs-8.0.5_GA_5839.UBUNTU12_64.20130910124038.tgz 
	tar xvfz zcs-8.0.5_GA_5839.UBUNTU12_64.20130910124038.tgz 
	cd zcs-8.0.5_GA_5839.UBUNTU12_64.20130910124038 
	sudo ./install.sh
	
## Ergebnis
100% CPU-Auslastung über einen Zeitraum von 24 Stunden:

Nicht alle Dienste des Zimbra-Serveres können starten.

Auf der Basis der Dokumentation ist anzunehmen, dass 613MB Arbeitsspeicher nicht für den Betreib von Zimbra 8 ausreicht.

Abbrucht des Versuchs. Löschen der EC2-Instanz.

