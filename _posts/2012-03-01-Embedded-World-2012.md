---
layout: post
category : lessons
tags : [embeddedworld, realtime, tutorial]
---
{% include JB/setup %}

# Tutorial mit David Kalinsky Tag 3

Heute am letzten Tag der Embedded World 2012 habe ich die 3. Class von Dr. David Kalinsky besucht. Das Thema heute war "Fault Tolerant System Design". 

## Fault Tolerant VS Safty
Zu Beginn der Veranstalltung wurde der Unterschied zwischen einem fehlertoleranten System und einem für
sicherheitskritischen Anwendungen unterschieden und auf Überschneidungen hingewiesen. 

## High Avalibility
Fehlertolerante Systeme werden über ihre Verfügbarkeit in verschiedene Klassen eingeteilt. 

## Fault Tree Entwicklung
Bevor mit dem Systemdesign begonnen wird sollte erst eine Fehleranlayse erstellt werden. 
Dazu schlug David folgendes Vorgehen vor: 
* Eine Stunde Brainstorming mit möglichst vielen Personen aus unterschiedlichen Professions
* Alle möglichen auftrettenden Fehler werden auf ein Withebord geschrieben. 
* Anschließend markiert jeder die 10 wichtigsten Punkte. Je mehr Markierungen, 
  desto kritischer scheint der Fehler zu sein.  
* Einteilung der Fehler in entsprechende Kategorieen. Dabei entsteht ein Fehlerbaum mit 
  mehreren Leveln. Je weiter die Verzweigung desto spezifischer ist das Problem. 
* Verbindung der Baumelemente mit und oder oder Verbindungen.
* Zuteilung einer Wahrscheinlichkeit wie häufig der Fehler auftretten kann für jeden 
  einzelnen Fehler. Die Wahrscheinlichkeiten für die höheren Knoten können aus den 
  niedrigeren Knoten berechnet werden.
