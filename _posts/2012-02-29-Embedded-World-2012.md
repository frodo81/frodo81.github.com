---
layout: post
category : lessons
tags : [embeddedworld, realtime, tutorial]
---
{% include JB/setup %}

# Tutorial mit David Kalinsky Tag 2

Da ich gestern so begeistert von der Einführung von David Kalinsky war, habe ich
heute seine Class "Software Design for Multicore Systems -- 2012 Edition"
besucht. Gerade sitze ich im Zug nach Hause und ziehe kurz mein Fazit vom heutigen Tag. 
Mal sehn wie weit ich komme ... noch 30 min

## Mutlicore VS verteiltes System
Multicore und verteilte Systeme sind grundsätzlich sehr ähnlich, aber nicht gleich! 
Viele Konzepte und Grundlagen für verteilte System sind schon 30 Jahre alt und 
können erstaunlicherweise übernommen werden. 

Aber es gibt einige grundlegende Unterschiede: 

* Der Systemtakt liegt bei Multicore Prozessoren um den
Faktor 100 kleiner als bei verteilten Systemen. Ein Tick bei einem Multicore 
liegt ca. bei 100nsec-1µsec; bei einem Verteilten System bei 10µsec-1msec.
* Die Bandbreite innerhalb eines Multicore-Prozessors ist deutlich höher 
  (1Gbit/s VS 100 Gbit/s)
* Multicore Prozessoren besitzen eine zuverlässige physikalischen Schicht. 
  Verteilte Systeme können hingegen der physikalischen Schicht nicht "trauen" 
  und müssen zusätzlichen Sicherungsmechanismen implementiern. So werden 
  Prüfsummen, Redundance, Arbittierungsverfahren, ... verwendet die 
  zusätzlich Bandbreite benötigen. 
* In verteilten Systemen ist die Anzahl der Prozessoren nicht konstant, beim
  Multicore dagegen schon. Das größte verteilte System der Welt ist das Internet. 
  An diesem Beispiel kann man sich schön die heterogene und varibale Struktur 
  veranschaulichen. 
* Die Topologie/Architektur in einem verteilten System ist sehr variabel. 
  Anhand eines Mobilfunknetzes kann man sich das ganz gut veranschaulichen. 
  Es ändern sich ständig die Anzahl der Teilnehmer und die verwendeten Geräte.
  Bei einem Multicore dagegen ist diese an die vorhandene Hardware gebunden
  und damit fest. 
* Software in den einzelnen Teilsystemen ist bei verteilten Systemen 
  inconsistent. Es gibt verschiedene Rechner mit unterschiedlichen 
  Softwareständen, OS, ... 
  Beim Multicore ist die Software auf den Prozeßoren konsitent. 

... 15 min 

## AMP VS SMP
AMP steht für Asymmetric Multi-Processing und SMP steht für Symmetric Multi-Processing. 
Diese beiden Begriffe haben sich heute durch den ganzen Tag gezogen. Als erstes muss
man sich klar machen, dass die Begriffe von unterschiedlichen Personon anders betrachtet
werden. So sieht ein Hardware Designer, ein OS-Programmieren und ein Softwareentwickler 
den Begriff jeweils anders. 

* <b>Hardware Designer</b>: Ein SMP-Core ist für dies Gruppe ein Multicore Prozessor bei dem die 
einzelnen Cores völlig identisch sind. Identisch bedeutet, das jeder Prozessor denselben
Hardwareaufbau hat, also die gleichen Hardwarekomponenten besitzt. D.h. in einem 
n-Mulit-Core gibt es also genau n gleiche Prozessoren. Dagegen ist
ein AMP ein Multicore System das aus verschiedenen Prozessoren besteht. Z.B. eine 
general-perpose CPU und ein oder mehrere DSPs, wie z.B. der Infinieon TriCore, 
Mikroautobox oder der Multicore Chip in der Playstation.

* <b>Softwareentwickler</b>: Diese Gruppe denkt in Tasks. Kann ein Task auf einer beliebigen
CPU laufen ist es für den Softwareentwickler ein SMP System, auch wenn das darunter
liegende System verschiedene Cores besitzt. Analoges gilt für die ASP. D.h. bei einem
SMP kann der Task einmal auf dem Core 1 laufen und das nächste mal auf Core 2. 
Bei einem AMP läuft der Task immer auf einem festen Core. 

* <b>Betriebsystemprogrammierer</b> haben wieder eine andere Sichtweise. Ein SMP bedeutes 
  für den OS-Entwickler ein System, welches das Scheduling für mehrere Cores übernimmt. 
  Ein AMP OS meint, dass jeder Core für sich selbst ein Scheduling durchführt. 

... 1 min

## Amdahl's Law

Amdahl's Law besagt, dass mit steigender Anzahl der Rechenkerne die gesamte zur Verfügung 
stehende Rechenleistung nichtlinear skalliert. 
... morgen mehr ...

