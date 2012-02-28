---
layout: post
category : lessons
tags : [intro, beginner, realtime, tutorial]
---
{% include JB/setup %}

# Was ist ein Real Time Operation System?

Bevor man sich mit Echtzeitsystemen beschäftigen kann muss
sich erst einmal mit der Echtzeit beschäftigen. 

## Die Echtzeit
Als Beispiel stelle man sich einen klassischen Übertragungsblock vor.
Legt man auf den Systemeingang eine Anregung, so kann man am Ausgang 
eine Reaktion beobachten. 
Erfolgt diese Reaktion sofort, d.h. ohne eine Zeitverzögerung, so spricht man
von einer Reaktion in Echtzeit. Da jedes technische oder auch nicht technische
System eine gewisse, evtl. sehr kleine, Reaktionszeit besitzen, definiert man
den Echzeitbegriff häufig auch wie folgt: 

Erfolgt eine Reaktion auf eine Systemanregung innerhalb eines beliebig klein 
definierten Zeitraums so spricht man von Echtzeitverhalten. Dabei muss für die
jeweilige Anwendung die Zeitanforderungen defniert werden für die das 
System quasi ein Echtzeitverhalten aufweist. 

Dies ist auch der erste kritische Punkt bei der Systemauslegung. Werden die 
Zeitanforderungen zu scharf gewählt, wird evtl. eine hohe Paralellität im 
RTOS gefordert, was komplexere Schedulingalgorithmen zur Folge hat. 

Setzt man im Gegenzug dazu die Zeitanforderungen zu weit herab, so werden 
Deadlines nicht mehr eingehalten und es werden Task nicht mehr korrekt beendet. 

## Real Time Operation System RTOS
Ein RTOS ist ein in der Regel spezielles Betriebssystem das auf die 
definierten Zeitanforderungen zugeschnitten ist. Vor allem ist es 
deterministisch. D. h. das Verahlten des OS auf ein Signal, Interrupt, Event, 
... ist bestimmbar und innerhalb der geforderten Schranken. 

Im Gegensatz dazu ist das Zeitverhalten von general-computing OS stark 
nicht-deterministisch. Es ist nicht möglich das Zeitverhalten der einzelnen
Tasks genau zu bestimmen. Die in diese OS eingesetzen Scheduler Algorithmen
bemühen sich einen fairen und preformante Einteilung der Rechenzeit zu 
gewährleisten. Dabei werden häufig statistische Größen für die Vergabe der Rechenzeit verwendet. So wird häufig Versucht die mittlere Rechenzeit der Tasks zu minimieren. 


