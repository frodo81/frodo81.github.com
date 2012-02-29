---
layout: post
category : lessons
tags : [embeddedworld, realtime, tutorial]
---
{% include JB/setup %}

# Tutorial mit David Kalinsky Tag 2

Da ich gestern so begeistert von der Einführung von David Kalinsky war, habe ich
heute auch noch seine Class "Software Design for Multicore Systems -- 2012 Edition"
besucht. Ich sitzte greade im Zug und zieht mal kurz mein Fazit vom heutigen Tag. 
Mal sehn wie weit ich kommen... noch 30 min

## Mutlicore VS verteiltes System
Multicore und verteilte System sind sehr ähnlich, aber nicht gleich. Viele 
Konzepte und Grundlagen für verteilte System sind schon 30 Jahre alt und 
können übernommen werden. 

Aber es gibt einige grundlegende Unterschiede: 

* Kommunikationsgeschwindigkeit ist bei Multicore Prozessoren ca. um den
Faktor 100 höher (100nsec-1µs). 
* Bandbreite innerhalb eines Prozessors ist deutlich höher (1Gbit/s VS 100 Gbit/s)
* Multicore Prozessoren besitzen eine zuverlässige physikalischen Schicht. Verteilte
Systeme hingegen können der physikalischen Schicht nicht "trauen" und müssen 
zusätzliche Overhead (Sicherungsmechanismen) implementieren. 
* In verteilten Systemen ist die Anzahl der Prozessoren nicht konstant, beim
 Multicore dagegen schon. 
* Gleiches gilt für die Topologie. Fest im Multicore und variable im verteilten
System
* Software in dem System ist bei verteilten Systemen inconsistent. Es gibt 
verschiedene Rechner mit unterschiedlichen Softwareständen, OS, ...
Beim Multicore ist die Software auf den Prozeßoren konsitent. 

... 15 min 

## AMP VS SMP
AMP steht für Asymmetric Multi-Processing und SMP steht für Symmetric Mulit-Processing. 
Diese beiden Begriffe haben sich heute durch den ganzen Tag gezogen. Als erstes muss
man sich klar machen, dass die Begriffe von unterschiedlichen Personon anders betrachtet
werden. So sieht ein Hardware Designer, ein OS-Programmieren und ein Softwareentwickler 
den Begriff jeweils anders. 

* Hardware Designer: Ein SMP ist für dies Gruppe ein Multicore Prozessor bei dem die 
einzelnen Cors völlig identisch sind. Es gibt also n gleiche Prozessoren. Dagegen ist
ein AMP ein Multicore System das aus verschiedenen Prozessoren besteht. Z.B. eine 
general-perpose CPU und einen DSP. 

* Softwareentwickler: Diese Gruppe denkt in Tasks. Kan ein Task auf einer beliebigen
CPU laufen ist es für den Softwareentwickler ein SMP System, auch wenn das darunter
liegende System verschiedene Cores besitzt. Analoges gilt für die ASP. Bei einem
SMP kann der Task einmal auf dem Core 1 laufen und das nächste mal auf Core 2. 
Bei einem AMP läuft der Task immer auf einem festen Core. 

* Betriebsystemprogrammierer haben wieder eine andere Ansicht. Ein SMP OS bedeutet ein 
System, welches das Scheduling für mehrere Cores übernimmt. Ein AMP OS meint, dass 
jeder Core für sich selbst ein Scheduling durchführt. 

... 1 min

## Amdahl's Law

... morgen mehr ...

