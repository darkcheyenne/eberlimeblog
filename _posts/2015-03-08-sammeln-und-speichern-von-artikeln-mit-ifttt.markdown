---
layout: post
title:  "Sammeln und Speichern von Artikeln mit IFTTT"
date:   2015-03-08 11:55:00 +0100
categories: jekyll update
---
# Einleitung

Ich bin aus beruflichen Gründen jeden Tag ca. 2 Stunden mit dem Zug unterwegs. Der grösste Teil dieser Zeit  verbringe ich bei der Arbeit, jedoch  an Tagen an denen ich länger im Büro bin gönne ich mir etwas entspannung indem ich auf diversen Webseiten Neuigkeiten oder Artikel lese.  Dabei kommt es vor, dass ich mir Artikel zur Referenz oder zur Errinnerung merken und ablegen möchte. Das Problem dabei ist, dass ich gern die Artikel der verschiedenen Seiten zur einfacheren Suche zentralisiert ablegen und speichern möchte.

# Ausgangslage

Ich beziehe Neuigikeiten und Artikel aus einer vielzahl von Kanälen:
 Fever (Privater RSS Server | Klassische News)
  * 9to5Mac * 20Min * Basler Zeitung Front * CCC Event Weblog * Gamasutra News * GameSkinny RSS Feed * Golem.de * heise online News * Kotaku * Humble Mumble * iPhoneblog.de * Macwelt News * netzpolitik.org * The Verge - All Posts * Touch Arcade
 Tumblr (Hauptkanal für Katzenbilder)
  Reddit (Buzz der aktuell das Netz beschäftigt)
   Facebook (Buzz aus dem Freundeskreis)
 Twitter (Buzz aus Personen von denen ich gern höhre)
  Das Ziel ist das Sammeln von allen Informationen in Evernote.
 # Vorarbeit
 Ich habe bereits vor einigen Jahren mit dem Dienst IFTTT (IF This Than That) experimentiert. In diesem Dienst kann man diverse Konten (Evernote, Facebook und c.a 300 weitere) vebinden und dann auf der Basis von Auslösern in dem einen Dienst in einem anderen Dienst etwas auslösen.
 Das Problem dabei ist, dass IFTTT kein Geld kostet und ich somit nicht weiss, was eigendlich Ihr Geschäftsmodell ist.
 Aus diesem Grund habe ich mich im Vorfeld bereits bei diversen alternativen (Zapier, Pipes etc.) ein Konto erstellt und mir die notwendigen Dienste und Auslöser angesehen. Ich habe für mich folgende Auslöser(Input) und Aktionen(Output) identifiziert:


Auslöser: * Fever: Neues Saved Item (Via RSS Feed) * Tumbler: Neues "Merken" eines Posts * Reddit: Neuer "Save" eines Posts * Facebook: Neues "Like" * Twitter: Neues "Speichern" eines Tweets * Instapaper: Neuer Artikel 

Aktion: * Instapaper: Neuer Artikel erstellen * Evernote: Neue Notiz erstellen 

Zu meiner Enttäuschung ist der grösste gemeinsame Nenner aller Funktionen bei IFTTT, die einzige fehlende Funktion ist der "Like" Auslöser bei Facebook.

 Weitere Recherchen über IFTTT lassen mich keine weiteren Anzeichen finden das IFTTT die Benutzerdaten und Verbindungen für schändliche Zwecke missbraucht, deshalb bin ich troz meines Ungehagens bereits IFTTT eine Chance zu geben.
 # Umsetzung

![Bild](/assets/34527-image_002.jpg) 
Die Umsetzung selbst gestaltet sich relativ einfach. Accounts mit IFTTT verbinden und Regeln erstellen. 
 Am Ende habe ich folgende 5 IFTTT-Regeln für mich erstellt:  ![Bild](/assets/ff8a8-image.jpg) ![Bild](/assets/803b8-image_003.jpg)
![Bild](/assets/6e2ca-image_004.jpg) ![Bild](/assets/f68ee-image_005.jpg)
![Bild](/assets/85dee-image_006.jpg)

# Ergebnis (Vorläufig)

Das Ergebnis ist im bei dem oben erwähnten Aufbau nur bedingt befriedigend. Die IFTTT-Regeln von den diversen Dienster zu Instapaper arbeiten erwartungsgemäss. Artikel werden automatisch von Instapaper erfasst und  in einer angenehm lesbaren Form aufbereitet. Die Verbindung von Instapaper zu Evernote ist nicht wie erhofft. Es wird nur der Link zum Artikel übertrangen was für die Langzeitarchivierung nicht geeignet ist.

Ein Update zu diesem Artikel folgt in der Zukunft.