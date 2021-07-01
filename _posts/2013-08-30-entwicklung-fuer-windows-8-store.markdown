---
layout: post
title:  "Erfahrungsbericht: App Entwicklung für Windows 8 Store"
date:   2013-08-30 11:55:00 +0100
categories: Windows
---
# Theoretische Grundlagen
Windows Store Apps sind eine mit Windows 8 hinzugekommene Entwicklungsmöglichkeiten für die .NET Programmiersprachen.

Windows Store Apps können nur auf Windows 8 und Windows 8 RT Geräten ausgeführt werden, haben das typische Vollbild Layout von Smartphone- und Tablet-Apps und werden ausschliesslich über den Windows 8 Store vertrieben.

# Ausgangslage
Microsoft hat in der Schweiz einen Wettbewerb ausgeschrieben, bei welchem man für das Entwickeln von zwei Windows Store Apps ein Windows 8 RT Tablet gewinnen konnte.

Ich habe an diesem Wettbewerb teilgenommen und habe auch ein Tablett erhalten. Eine der beiden Anwendungen habe ich über die Monate weiterentwickelt und möchte in diesem Zusammenhang meine Erfahrungen mit der Entwicklung von Windows 8 Store Apps teilen.

# Erfahrungsbericht

## Entwicklungsumgebung

Die Entwicklungsumgebung Visual Studio ist nach meiner Erfahrung eines der komfortabelsten und stabilsten IDEs auf dem Markt. Visual Studio ist stabil, bietet oft brauchbare Hilfestellungen und hat einen sehr guten Debugger.

Wenn man für Windows 8 Store etwas entwickelt, dann ist man zwingend auf Visual Studio angewiesen. Es gibt keine alternativen zwischen denen man wählen könnte.

## Kosten
Die (Jährlichen-)Kosten für ein Entwickler Abonnement bei Microsoft sind 49$ oder 69 CHF. Eine solches (aktives) Konto ist erforderlich um Apps auf dem Windows 8 Store zu veröffendlichen. Auf dem Store befindliche Apps werden bem Auslaufen des Entwickler Abonnements nach 10 Tagen aus dem Store entfernt.

Einzelentwickler können die kostenlose Express Editon von Visual Studio verwenden. Viele der teambasierten Funktion von Visual Studio sind den kostenpflichend Versionen von Visual Studio vorbehalten.

## App-Store-Infrastruktur
Das Windows 8 Store Dashboard, die Managementkonsole zur Verwaltung eigener Windows 8 Store Apps, ist Funktional.

Es lassen sich neue Apps registrieren und registrierte Apps updaten(Ein Update jeglicher Art ist immer mit einer Neu-Zertifizierung verbunden).

Es gibt Statistiken zu diversen technischen Aspekten, Verkaufs- und Nutzungszahlen.

Jedoch dauert es oft Wochen bis diese Statistiken aktualisiert werden und die Statistiken sind nicht sehr Umfangreich.
Ein viel grösses Problem ist, dass die von Benutzern hinterlassenen Bewertungen nach Land angezeigt werden. Ein Entwckler muss 50+ Länder durchgehen um alle Bewertungen zu seiner App lesen zu können.
Weiter wäre es nett auch auf solche Bewertungen eingegehn zu können. Z.b Wenn man aufgrund einer Bewertung ein Feature hinzugefügt hat.

## GUI-Design
Das GUI-Design geschieht in XAML, einer XML basierten Sprache. Der grafische Designer ist sehr langsam, aber ansonsten geht das Design via Designer oder Text gut von der Hand.

Animationen (FadeIn/FadeOut/Bewegung) von Elementen können relativ einfach realisiert werden.

Ein GUI so zu designen, dass es mit Auflösungsänderungen, welche die Position der Elemente verändern sollten, ist schwierig. Dies liegt vor allem daran, dass sich der Inhalt von Listen schlecht anpassen lässt.

## Performance
Im Vergleich zu dem bestehenden Framework WPF ist die Performance der neuen XMAL Oberfläche sehr sehr gut! Listen mit 500+ Einträgen, inklusive eines 64x64 Icons pro Eintrag, werden in unter einer Sekunde aufgebaut.

# Fazit
Die App-Entwicklung für den Windows 8 Store hinterlässt generell einen guten Eindruck. Die Funktionen und die verwendeten Technologieen wirken solide.

Es gibt allerdings zwei Dinge, die stören:

1. Der Umfang der Statistiken auf dem Windows 8 Store ist eher mässig.
1. Viele der Microsoft-Anwendungen verwendete GUI-Elemente, die nicht als Vorlagen in Visual Studio vorhanden sind.Microsoft verschenk viel Potential die Anwendungslandschaft zu vereinheitlichen und die Entwickung von Windows 8 Store Apps zu fördern.
