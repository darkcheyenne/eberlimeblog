---
layout: post
title:  "Erfahrungsbericht: Webanwendungen mit JavaEE"
date:   2013-08-28 00:00:00 +0100
categories: Raspberry
---
# Theoretische Grundlagen
Java Enterprise Edition, oder JavaEE, ist eine Erweiterung zu Java. Generell ist JavaEE auf die Erstellung von Webanwendungen und Webdiensten ausgerichtet. Dabei bietet JavaEE hauptsächlich Funktionen, welche den Aufwand zur Erstellung einer Serversoftware verringern.

Auf der Seite der **Darstellungsschicht** kann das im 2006 eingeführte Java Server Faces(JSF) viele gängige HTML Konstrukte aus Objekten oder Listen generieren. Weiterhin unterstützt Java Server Faces(JSF) den Programmierer mit einem halbautomatischen Datenaustausch zwischen Browser und Server via Ajax.

Auf der Ebene der der **Geschäftslogik** bieten Enterprise Java Beans(EJB) eine Möglichkeit, benötigte externe Klassen erst bei Bedarf automatisch zu instanzieren und diese zwischen Sitzungen von unterschiedlichen Benutzung zu teilen.

Auf der Ebene der **Datenhaltung** bietet das Java Persistence API(JPA) eine Möglichkeit zur automatischen Datenhaltung auf einer Datenbank. Die Daten werden dabei direkt über Java Objekte(Entites) definiert und die Java Persistence API(JPA) kümmert sich dann um die Umsetzung dieser Objekte auf die Datenbank.

Zum Betrieb einer JavaEE Anwendung benötigt man einen JavaEE fähigen Webserver. Die Referenzimplementation eines solchen Webservers ist GlassFish 4.

# Ausgangslage
Ein Freund, welchen wir im weiteren Verlauf Leonardo nennen, hat von einer in der Türkei ansässigen Firma ein sehr gutes Jobangebot erhalten. Aus diesem Grund ist dieser seit etwa einem Jahr dabei die türkische Sprache zu lernen.

Dabei ist aufgefallen, dass es ein Mangel an Lernkarten-Anwendungen (spezifisch Anwendungen mit vorgefertigten Lernkarten) gibt.

Leonardo ist daraufhin an mit der Idee eine Lernkarten Webseite zu erstellen an mich herangetreten.

Da ich mich selbst bereits seit längerem für Webanwendungen interessiere und gerne mit dieser Technologie experimentiert hätte, habe ich mich entschlossen mit Leonardo eine Lernwebseite aufzubauen. Wobei ich die technische Seite und Leonardo die inhaltliche Seite übernimmt.

# Abgrenzung
Ich werde mich im weiteren Verlauf dieses Artikels nur auf meine Erfahrungen mit der Programmiersprache Java Enterprise Edition eingehen. Weitere Themen die als Teil dieses Projekts angefallen sind werde ich je nachdem in anderen Artikeln beschreiben.

# Erfahrungsbericht
## Stunden 0-4 | Einstieg

Ich habe bereits ein wenig Erfahrung mit JavaEE in einem anderen Projekt gemacht, habe es jedoch nie in allen Aspekten selbst umgesetzt.

Aus diesem Grund habe ich ein passendes Tutorial im Internet gesucht. Die eigentliche Dokumentation von Oracle ist als Nachschlagewerk brauchbar, zum neu lernen allerdings völlig ungeeignet.
Was mir relativ gut gefallen hat ist das (kostenpflichtige) Videotraining der Firma video2brain (https://www.video2brain.com/de/videotraining/java-ee-6).

## Stunden 5-10 | Planung
Aufgrund des Aufbaus einer JavaEE Anwendung war gibt es bereits von Grund auf folgende Unterteilung:

* Darstellung (XHTML)
* Geschäftslogik (Java)
Aufbauend auf dieser Grundunterteilung habe ich mich für folgende Unterteilung entschieden:

* Darstellung (XHTML)
* Darstellungslogik (Java, Sitzungsorientiert)
* Dienste (Java, Singelton)
* Datendefinition (Java)
Generell kann ich feststellen, dass die unterteilen von Programmcode in sinnvolle Schichten mit JavaEE gefördert wird.

## Stunden 11-50 | Entwicklung
Das Zusammenspiel zwischen den verschiedenen Schichten funktioniert erstaunlich gut und hilft enorm dabei Ordnung zu halten.
Java Server Faces kann direkt aus Java Objekten HTML generieren.
Dies ist vor allem aus dem Grund, dass alle Daten aus der Datenbank in Klassen geliefert werden enorm hilfreich.
So lässt sich zum Beispiel eine Funktion, die quasi den Inhalt einer Tabelle als Webseite ausgibt in wenigen Zeilen Quelltext realisieren.
Es gibt zu Java Server Faces eine grosse Anzahl verschiedener Bibliotheken, welche sich nahtlos in bestehende Anwendungen integrieren lassen.
So bietet zum Beispiel die Primefaces-Bibliothek sortierbare und durchsuchbare Tabellen, Fortschrittsanzeigen und JavaScript-Popupfenster.

Die vollautomatische Umsetzungen von Informationen aus der Datenbank in Objekte ist extrem mächtig, macht das Entwickeln wesentlich einfacher und trägt enorm zur Robustheit der Anwendung bei.

Ebenfalls sehr hilfreich ist die Integration von mehrsprachigen Textelementen und das automatischen Aushandlung der Sprache mit dem Browser.

Negativ aufgefallen ist, dass der Glasfish-Server während der rund 50 Stunden Entwicklungszeit mehrfach „Schluckauf„ hatte.
Dies hat sich darin geäussert, dass der Glasfisch nur noch eine unsinnige Fehlermeldung ausgegeben hat. Die Lösung ist dann immer ein kompletter Neustart des Servers.

# Fazit
Auf der Ebene der GUI-Entwicklung ist JavaEE im Vergleich zu Java mit AWT oder Swing eine enorme Verbesserung!

JavaEE Webanwendungen laufen ganz einfach und unkompliziert auf jeden Web-Browser und es ist viel einfacher eine robuste Anwendung zu entwickeln.

Ich habe leider keinen Vergleich zwischen JavaEE und ASP.NET. Ich möchte mir allerdings ASP.net irgendwann in Zukunft gerne ansehen.