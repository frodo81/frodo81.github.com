---
layout: post
category : lessons
tags : [embeddedworld, realtime, tutorial]
---
{% include JB/setup %}

# Tutorial mit David Kalinsky

Diese Woche findet zum 10 mal die Embedded World statt. Natürlich bin ich wieder
mit dabei. Ich besuche den Kurs "Introduction to Real Time Operation Systems" 
von David Kalinsky. 

Hier poste ich eine kleine Zusammenfassung des Kursinhaltes: 
Zu Beginn haben wir über die Aufgaben eines RTOS gesprochen. Die wichtigsten 
Aufgaben sind: 

* Die absolut wichtigste Aufgabe ist das Taskmanagement. Wenn man dieses nicht 
   benötigt, dann braucht man auch kein OS!
* Dynamische Speicherreservierung, malloc, free und so Zeug
* Ein- und Ausgabeschnittstellten (I/O-Interfaces)
* Intertaskkomunikation, Synchronisation
* Timer, der den Grundtakt für die Tasks angibt

## Task Schedulers
Der wichtigste Part innerhalb des Taskmanagement ist der Task Scheduler. 
Die Aufgabe des Schedulers ist die Berechnung des nächsten auszuführenden
Tasks. D.h. Welchem Task wird als nächstes Prozessorzeit zugewiesen. 

Dabei gibt es eine Reihe unterschiedlicher Algorithmen nach denen die Tasks 
Rechenzeit zugewiesen bekommen: 

* Endless Loop
* Basic Cyclic Executive
* Time-Driven Cyclic Executive
* Multi-rate Cyclic Executive
* Multi-rate Executive for Periodic Tasks
* Multi-rate Executive with Interrupts
* Priority-based Preemptive Scheduling
* Deadline Scheduling Strategies (EDF, LL, MUF)

## Informationen über Tasks
Bevor man mit dem Design des eigentlichen RTOS anfangen kann, muss man die
Aufgaben des Systems in möglichst kleine Einzelaufgaben zerlegen. Diese 
einzelnen möglichst kleinen Aufgaben (engl. chunks) werden dann Tasks genannt.

Ein Task hat dabei einige Eigenschaften. So besitzt jeder Task eine eindeutige
ID, Priorität, Type, Stack, Laufzeit, Deadline, Debuginformationen, ... 

Es gibt verschiedene Kategorien:

* Software-triggerd Tasks
* Background Task(s)
* Interrupt-handling Tasks
* Periodic Tasks
* Phantom Tasks

Jeder Task besitzt verschiedene Zustände während er ausgeführt wird. 
Dies kann mit einem Zustandsautomaten (Stateflow) abgebildet werden. 
Es gibt verschieden Möglichkeiten die Zustände eins Tasks 
einzuteilen. Die einfachste Art besteht aus 3 Zuständen: 

* Ready: Der Task ist für bereit ausgeführt zu werden. Er hat alle notwendigen
	 Resourcen für die Ausführung für sich reserviert.
* Running: Der Task erhält den Prozessor und wird darauf ausgeführt. 
* Blocked: Es fehlen die benötigten Resourcen oder der Task wird von einem höher
	   priorisierten Task verdrängt. 

## Task Kommuniktaion / Synchronisation
In einem System werden die Aufgaben in möglichst kleine Tasks aufgeteilt die 
gut durch einen Programmierer abgearbeitet werden können. Durch diese Konstruktion des RTOS, muss jeder Task mit anderen Tasks kommunizieren können um da er ja 
nur eine bestimmte Aufgabe des Gesamtsystems lösen kann. Diese Ergebnis muss er an andere Tasks weitergeben. 

In einem Real Time Operation System gibt es grundlegend Elemente um eine 
sog. Intertaskkomunikation zu ermöglichen. D.h. einen Informationsaustausch
zwischen zwei oder mehreren Tasks innerhalb eines Systems.

Wir haben dabei die folgenden Verfahren besprochen: 

* "Indirect" Message Passing
* "Direct" Message Passing
* Semaphoren
* Resource Monitor Tasks
* Mutex

### Indirect Message Passing
Bei diesem Verfahren wird die Kommunikation über eine Message an einen anderen Task gesendet. Dabei erstellt der Sender eine Nachricht und sendet diese an einen Buffer, z.B. einen FIFO (FirstIn-FirstOut). Das RTOS erstellt bei der Systeminitialisierung eine entsprechende Warteschlange für alle Nachrichten und sorgt dafür das bei gleichzeitigem Senden von mehreren Task keine Fehler entstehen. 

Äquivalentes geschied beim Empfänger Task. Der Scheduler aktiviert den entsprechenden Task wenn eine Nachricht für diesen vorliegt. Dieser liest wieder aus dem Buffer und erhält somit die benötigten Informationen. 

Ein großer Nachteil dieses Verfahrens ist es das die Nachrichten je nach System mindestens zwei mal Kopiert werden müssen. Dies scheint bei kleinen Nachrichten noch akzeptabel ist jedoch bei großen Nachrichten, wie z.B. bei Ethernet Packeten, sehr Speicheraufwändig und gerade in RTOS unerwünscht. 

### Direct Message Passing
Um dieses Problem zu beseitigen übergibt man dem Buffer nicht den Dateninhalt, 
sondern nur einen Zeiger. Dies sorgt dafür das nur der Zeiger mehrmals kopiert wird. Diese Art der Intertaskkomunikation nennt man auch direktes Nachrichenweiterreichen (engl. Direct Message Passing). 

### Semaphoren
Ein weiteres Verfahren sind sog. Semaphoren. Durch diese wird eine gemeinsame
Resource gesperrt. Es wird aber keine Nachricht ausgetauscht. Ein Semaphore 
kann z.B. eingesetzt werden wenn mehrere Tasks auf eine gemeinsame Resource
zugreifen wollen. So z.B. auf den CAN-Controller oder einen gemeinsamen Speicherbereich für den Datenaustausch. 

## Echtzeit
D. Kalinsky hat die Echzeit ähnlich wie ich definiert im Post 
[Real Time Operation System](http://frodo81.github.com/lessons/2012/02/27/Real-Time-Operation-Systems/). 

<pre>
"Hard" Real Time == correct result MUST BE provided at REQUIRED time deadlines
</pre>
<pre>
"Soft" Real Time == correct result SHOULD BE provided at DESIRED time deadlines
</pre>

Der Echzeitbegriff wird noch einmal in Hard und Soft unterteilt. Dies lässt sich
am einfachsten anhand eines kleinen Beispiels erklären: 

Das System für das Auslösen eines Airbags ist ein Hard Real Time System, den
das nicht einhalten einer Deadline für sofort zum Versagen. 

Ein Soft Real Time System hat keine harte Grenze, die darüber Entscheidet ob das
System versagt hat oder korrekt Funktioniert. Nachdem die Deadline
überschritten ist, wird z.B. die Systempreformance degradiert. Tritt nur 
sporadisch ein Überschreiten der Deadline auf, so wird das häufig gar nicht
wahrgenommen. 

Ein Beispiel für ein Soft Real Time System ist ein Satteliten Receiver. Werden 
die Deadlines für die Decodierung der einzelnen Bildblöcke verpasst, so 
entstehen im Fernsehbild Störungen (Bildartefakte). Werden nur wenige Blöcke 
nicht oder falsch decodiert, so wird es den Consumer nicht weiter stören. 
Mit zunehmender Anzahl an Störungen werden diese immer stärke auffallen und das 
System wird bei zu vielen Bildfehlern als unbrauchbar angesehen. 

## Memory Allocation und Memory Protection
Im letzten Kapitel des Tutorials wurde über die Speichereinteilung und 
Verwaltung in einem RTOS gesprochen. 

Es gibt zwei unterschiedliche Speicherkonzepte: 
* Memory Allocation
* Memory Protection

Wird der Speicher alloziert, so wird im Laufe der Anwendung der Speicher 
fragmentiert. Diese Problem nennt man Memory Fragmentation. In non-RTOS 
Systemen gibt es eine Reihe unterschiedlicher Verfahren für die 
Defragmentierung. Diese Verfahren sind nicht deterministisch und somit nicht
für ein Echzeitsystem geeignet. 

In RTOS werde sog. Pools benutzt. Dabei Teilt man den Speicher in feste 
vorgegebene Größen ein. Es gibt eine Tabelle/Liste in der die nächsten freien
Blöcke der jeweiligen Größe stehen. Somit kann schnell der nächste freie Buffer
gefüllt werden. 

Bei dem letztgenanten Verfahren mit Pools, kann auch eine Fragmentation
auftretten. Man unterscheidet die Fragmentationen in external und internal. Bei
dem Pool Verfahren kann nur die internal Fragmentation auftretten. Diese ist 
für RTOS Anwendungen nicht kritisch. 


