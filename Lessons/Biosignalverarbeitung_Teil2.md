### Praktikumsunterlagen
## **Biosignalverarbeitung - Teil 2**
### WS 2024

Bachelorstudiengang
### Medizin-, Gesundheits- und Sporttechnologie

Autoren:
#### *Yannic Heyer / Niklas Brown* *Adaptiert von: Gerda Strutzenberger, PhD / Lukas Neururer*

Letztes Update: 30. September 2024

# **Inhaltsverzeichnis**

**1** **Praktikum** **2**

1.1 Organisatorisches . . . . . . . . . . . . . . . . . . . . . . . . . . . 2

1.2 Teil 2 - Elektrokardiografie (EKG) . . . . . . . . . . . . . . . . . . 5

**Literaturverzeichnis** **IV**

**Abbildungsverzeichnis** **V**

**Tabellenverzeichnis** **VI**

1

# **Kapitel 1** **Praktikum**

In diesem Praktikum werden Sie lernen, mit frei verf¨ugbarer Hardware Biosignale am Menschen aufzunehmen und die Daten ¨uber Programmierung zu filtern,
verarbeiten und analysieren. Dabei werden Sie Biosignale vom Muskel-, Nervenund Herz-Kreislauf-System kennenlernen und f¨ur sich erforschen.
### **1.1 Organisatorisches**

1. **Bewertung**
Die Bewertung dieses Moduls erfolgt ¨uber die Abgabe von Laborberichten
und der Abgabe eines Abschlussprojektes. Das Praktikum wird in 3-4er
Gruppen durchgef¨uhrt und bewertet.

2. **Gruppenbildung**
Die Gruppenbildung ist Ihnen innerhalb der bereits aufgeteilten Gruppen
A & B frei ¨uberlassen. Die Aufteilung wird im Rahmen der ersten Vorlesung durchgef¨uhrt und gilt fortlaufend f¨ur das Semester. Nachtr¨agliche
¨Anderungen von Gruppen werden nur unter besonderen Umst¨anden und in
Absprache mit dem Lehrenden vorgenommen.

3. **Aufteilung der Ubungen** **[¨]**

(a) **Teil 1 - Aufbau der Hardware und erste Aufnahmen + Schrei-**
**ben eines Praktikumsberichtes**

In dieser Sektion wird das Hardware Setup aufgebaut. Es werden
erste Messungen vorgenommen sowie Daten gefiltert und analysiert.
Zum Schluss wird gemeinsam das Schreiben von Praktikumsberichten
besprochen und einige Beispiele aufgezeigt. **Abgabe von Python**
**Programmen + freiwillige Abgabe vom Praktikumsbericht /**

2

1. Praktikum 3

**Feedback formale Kriterien**

**Bitte machen Sie sich mit den Grundlagen der Arduino IDE**
**[unter folgendem Link bekannt. Fokussieren Sie sich auf die](https://docs.arduino.cc/learn/starting-guide/getting-started-arduino##arduino-software-tools-1)**
**Sektionen beginnend mit ”Arduino API“. Downloaden Sie**
**f¨ur dieses Praktikum die Version 1.8.19, welche als Legacy**
**Version gef¨uhrt wird (Siehe Abbildung 1.1).**

Abbildung 1.1: Arduino IDE 1.8.19

(b) **Teil 2 - Elektrokardiografie (EKG)**
Diese Sektion beinhaltet die Messung und Analyse der elektrischen
Aktivit¨at des Herzens durch ein 1-Kanal-EKG. Dabei sollen Eigenschaften wie die Herzfrequenz, die Herzfrequenzvariabilit¨at und der
Energieverbrauch untersucht werden. **Abschluss mit Laborbericht**

(c) **Teil 3 - Elektromyografie (EMG)**
Das EMG Praktikum umfasst die Messung und Analyse der vom Skelettmuskel erzeugten elektrischen Aktivit¨at. Dabei gilt es, die relative
Muskelaktivierung, das Frequenzspektrum des aktiven Muskels und
die Erm¨udung zu bestimmen. **Abschluss mit Laborbericht**

4. **Hardware**

Jeder Projektgruppe wird zu Beginn des Praktikums ein Hardware-Kit
ausgeh¨andigt, welches mit Vorsicht zu behandeln und nach Projektende
**vollst¨andig** zur¨uckzugeben ist. Dieses Kit umfasst die in Tabelle 1.1 dargestellten Komponenten.

1. Praktikum 4

Tabelle 1.1: Hardwarekomponenten mit Mengenangaben pro
Kit.

Komponente Menge

Mikrocontroller (SparkFun) 1
Analog-Digital-Konverter 1
Data Logger 1
microSD-Karte 1

Beschleunigungssensor 1
EMG/EKG Sensor 1
zus¨atzliche Elektroden tbd

9 V Batterieanschluss 1

9 V Batterie 1

Micro-USB-Kabel 1

Qwiic Kabel 3
Jumper Kabel 4

1. Praktikum 5
### **1.2 Teil 2 - Elektrokardiografie (EKG)**

**ACHTUNG: Sollte ein Studierender bereits EKG Elektroden verwen-**

**det und damit Hautreizungen verursacht haben, soll diese Person im**
**Rahmen dieses Praktikums keine Messungen mit Elektroden durchf¨uhren.**
**Sprechen Sie dies gegebenenfalls mit der Praktikumsleitung ab.**

**Ziele**

1. Aufbau und Testen der Hardware und Software f¨ur EKG-Messungen

2. Berechnen der Herzfrequenz und Herzfrequenzvariabilit¨at

3. Sch¨atzen des Energieverbrauchs bei Aktivit¨at mithilfe der Herzfre
quenz

**Ben¨otigte Komponenten**

1. Mikrocontroller mit USB-Kabel

2. EMG /EKG Sensor mit Elektroden

3. 3 Jumper Kabel

**Ben¨otigte Komponenten f¨ur mobiles System**

1. 9 V Batterie und Batterie Verbindung

2. Data Logger mit microSD Karte

3. Verbindungskabel (Qwiic)

**Ben¨otigte Software**

1. Python (Jupiter Notebook / VS Code)

2. Arduino IDE

1. Praktikum 6
### **Aufgabe 1: Wie nehme ich EKG Rohdaten auf?**

In dieser Aufgabe lernen Sie, das EKG-Messsystem aufzubauen und damit Rohdaten aufzunehmen. Außerdem werden die Rahmenbedingungen f¨ur kommende
Messungen mit dem EKG-System besprochen.

1. **Hardware Setup**
Folgende Schritte sind durchzuf¨uhren, um den EKG-Sensor an den Mikrocontroller anzuschließen:

(a) Verbinden Sie das mitgelieferte 4er-Kabel (schwarz/rot/weiß/gelb) mit
dem blauen EKG-Sensor

(b) Nutzen Sie die drei Jumper Kabel, um diese in die andere Seite des
4er-Kabels zu stecken.

*schwarz* = *GND*

*rot* = *V CC*

*gelb* = *V OUT*

(c) Die rote Verbindung versorgt den Sensor mit Strom und muss mit dem
3.3 V Eingangs des Mikrocontrollers verbunden werden.

(d) Die gelbe Verbindung dient als Ausgang des Sensors und gibt das gemessene Potential als analogen Wert weiter. Daf¨ur muss es mit dem
analogen Input am Mikrocontroller verbunden sein. Schließen Sie demnach das gelbe Kabel an den analogen Eingang *A0* an.

(e) Das schwarze Kabel ist die Erdung bzw. Referenz. Verbinden Sie das
schwarze Kabel mit einem der *GND* Pins am Mikrocontroller.

(f) **Stellen Sie sicher, dass alle Kabel korrekt angeschlossen sind,**
**bevor Sie mit Teil 2 fortfahren.**

2. **Anbringen der Elektroden**
Um ein gutes EKG-Signal gew¨ahrleisten zu k¨onnen, sollen die Elektroden
auf m¨oglichst haarfreie und saubere Stellen geklebt werden. Reinigen Sie
daf¨ur die zu beklebenden Stellen mit Wasser oder Seife und lassen Sie diese

anschließend vollst¨andig trocknen. Danach k¨onnen Sie die Elektroden an
folgende Stellen kleben:

    Elektrode 1 (weiß) an das Manubrium

1. Praktikum 7

    - Elektrode 2 (rot) an den **[linken V6 Ableitpunkt](https://en.wikipedia.org/wiki/Electrocardiography#/media/File:Precordial_leads_in_ECG.png)** . Als Hilfestellung wird folgender **[Link](https://en.wikipedia.org/wiki/Electrocardiography#/media/File:Precordial_leads_in_ECG.png)** bereitgestellt, in dem das Ermitteln des V6
erl¨autert wird.

    Elektrode 3 (schwarz) ist die Referenzelektrode. Dies sollte m¨oglichst
wenig bewegt werden, um St¨orsignale zu vermeiden. Daher wird eine
Platzierung auf der Halswirbels¨aule (C7) oder ¨außeren Sprunggelenk
(lateral Malleolus) empfohlen.

Stecken Sie anschließend die Kabel auf die Druckkn¨opfe der Elektroden
(Farben beachten!!!) und befestigen Sie die Kabel mit Hilfe von haut-neutralem
Klebeband etwa 2-3 cm entfernt von der Elektrode. Dadurch k¨onnen Arte
fakte durch Kabelbewegungen reduziert werden.

3. **Erfassung der Rohdaten**
F¨ur die Erfassung von Rohdaten werden analoge Messwerte eingelesen. Dies
geschieht ¨uber den von Ihnen ausgew¨ahlten Pin (A0). Die Arduino IDE
stell daf¨ur ein Beispiel Code bereit, welchen Sie ¨uber *Datei →* *Beispiele*
*→* *01.Basics →* *AnalogReadSerial* aufrufen k¨onnen. Stellen Sie sicher, dass
Ihr verwendeter analoger Pin dem Pin im Arduino Code gleicht und laden
Sie den Code auf den Mikrocontroller. Offnen Sie den seriellen Plotter und [¨]
passen Sie die Baud Rate an, um die Rohdaten zu erhalten. Nach kurzer
Zeit sollte ein Ihnen bekanntes Bild entstehen (elektrische Aktivit¨at des
Herzens). Falls Sie kein solches Bild wie in Abbildung 1.2 erkennen, ¨uberpr¨ufen Sie erneut Ihr Hardware Setup und die Befestigung der Elektroden
und Kabel.

Abbildung 1.2: EKG Rohdaten.

Trennen Sie Ihren Laptop vom Ladeger¨at und somit vom Stromnetz. Off- [¨]
nen Sie Ihren seriellen Plotter und achten Sie auf Ihre Daten. Schließen Sie

nun ihr Ladeger¨at wieder an und schauen Sie sich erneut die Daten an.
Was k¨onnen Sie f¨ur Unterschiede zwischen diesen Szenarien feststellen und
durch was k¨onnen diese verursacht werden? **(Aufgabe 2 der Abgabe)**

1. Praktikum 8

Stecken Sie das Ladeger¨at wieder ein und greifen Sie mit beiden H¨anden
an das Metallgeh¨ause ihres Laptops. Was k¨onnen Sie in den Rohdaten f¨ur
Ver¨anderungen beobachten und wieso kommt es dazu?

Der Beispiel-Code der Arduino IDE gibt die Rohdaten ohne Zeitstempel
aus. Zur Berechnung der Herzfrequenz sollte die Zeit jedoch hinzugef¨ugt
werden. Gehen Sie daf¨ur in die *void loop()* und ersetzen Sie die Zeile
*Serial.println(sensorValue);* mit folgendem Code.

S e r i a l . print ( sensorValue ) ; *// EKG Rohdaten*
S e r i a l . print ( ’ / t ’ ) ; *// Leerzeichen*
S e r i a l . print ( m i l l i s ( ) ) ; *// Zeit* *in* *Millisekunden*
S e r i a l . println ( ) ; *// neue* *Zeile*

Um eine h¨ohere Sample Rate zu erhalten, ¨andern Sie die *Serial.begin(9600);*
zu *Serial.begin(500000);* . Dadurch wird die Geschwindigkeit der Daten¨ubertragung zwischen Computer und Mikrocontroller erh¨oht. Sie m¨ussen f¨ur eine
weitere Darstellung der Daten im seriellen Plotter die Baud Rate im seriellen Plotter oder Monitor ¨andern.

Speichern Sie die neue Datei auf ihrem Laptop und laden Sie den Code auf
den Mikrocontroller. Sie k¨onnen nun Rohdaten f¨ur die folgenden Experimente aufnehmen und die Daten aus dem seriellen Monitor in eine separate
Textdatei hineinkopieren, um ihre Messwerte zu speichern.

4. **Experiment in Ruhe**
In diesem Experiment werden Sie ein 10-min¨utiges Ruhe-EKG aufnehmen.
Nutzen Sie den Ihnen auf Sakai zur Verf¨ugung gestellten Code **Lab2Code1**,
bei dem mit einer Frequenz von 500 Hz und einer Baud Rate von 500000
aufgenommen wird. **Achtung: Der serielle Monitor kann nur 10 Mi-**
**nuten (300.000 Zeilen) Daten bei 500 Hz aufnehmen. Dr¨ucken Sie**
**bei Beginn den Button** ***Ausgabe l¨oschen*** **, um Fehler zu vermei-**
**den (Siehe Abbildung 1.3)** . Wenn Sie dennoch einen l¨angeren Zeitraum
aufnehmen m¨ochten oder eine Frequenz von 1000 Hz w¨ahlen, k¨onnen Sie
das OpenLog verwenden. Dies k¨onnte vor allem f¨ur Ihr Abschlussprojekt

interessant sein.

(a) Bauen Sie die gesamte Hardware auf und laden Sie den Code auf Ihren
Mikrocontroller

(b) Suchen Sie einen geeigneten Ort, an dem der Proband oder die Probandin eine liegende Position f¨ur 10 Minuten einnehmen kann

1. Praktikum 9

(c) Positionieren Sie den Laptop an diesem Ort und schließen Sie alle
Sensoren an

(d) Gehen Sie sicher, dass Ihr Laptop nicht w¨ahrend den 10 Minuten in
den Ruhemodus wechselt oder sich ausschaltet

(e) Stellen Sie einen Timer auf 10 Minuten. In dieser Zeit soll sich der/die
ProbandIn nicht mehr bewegen. Die Referenzelektrode sollte m¨oglicherweise auf den lateral Malleolus geklebt werden, da durch den Kontakt zwischen Wirbel und Boden Artefakte entstehen k¨onnen

(f) Wenn der Timer durchgelaufen ist, k¨onnen Sie den Mikrocontroller
vom Laptop trennen und ihre Daten aus dem seriellen Monitor in eine
Text-Datei hineinkopieren

Abbildung 1.3: L¨oschen der Daten im seriellen Monitor.

5. **Experiment in Bewegung**
F¨ur Teil 5 dieser Versuchsserie soll die Referenzelektrode wieder am C7 im

Nacken des Probanden angebracht werden. Stellen Sie außerdem sicher, dass
die Verkabelung gut am K¨orper angebracht ist. Dies soll Bewegungsartefakte vermeiden und hilft bei der sp¨ateren Weiterverarbeitung der Daten. F¨ur
die Messung in Bewegung soll das Fahrradergometer und das auf der Tacx
montierte Mountainbike verwendet werden. Es werden zwei Experimente
durchgef¨uhrt:

(a) **Experiment 1 - Ramp and Rest (10 min)**

i. 2 Minuten auf dem Ergometer sitzen - nicht treten - Puls soll
ruhen

ii. 3 Minuten bei konstanter Leistung treten - mittlere bis schwere
Anstrengung - Proband soll sich nach den 3 Minuten ersch¨opft
f¨uhlen

iii. Stoppen zu treten - 5 Minuten ruhen und Puls erholen lassen

1. Praktikum 10

(b) **Experiment 2 - Conconi Test (15 min)**
F¨ur den Conconi Test schließen Sie bitte Ihr mobiles Setup an, da dieser etwa 14 Minuten dauert. Gehen Sie sicher, dass Ihre SD-Karte
funktioniert und starten Sie die Messung. Die einzustellenden Leistungsstufen und die jeweilige Dauer sind unter folgendem **[Link](https://de.wikipedia.org/wiki/Conconi-Test#:~:text=Der%20Conconi%2DTest%20ist%20eine,an%20der%20anaeroben%20Schwelle%20festzustellen.)** zu
finden.
**WICHTIG: Wenn Sie sich k¨orperlich nicht wohlf¨uhlen, k¨onnen**
**Sie den Test jederzeit abbrechen. Denken Sie außerdem dar-**
**an, genug Fl¨ussigkeit zu sich zu nehmen, um Auswirkungen**
**durch Dehydration zu vermeiden.**

1. Praktikum 11
### **Aufgabe 2: Analyse der Rohdaten**

In diesem Teil des Praktikums werden Sie lernen bzw. vertiefen, wie sich die Herzfrequenz, Herzfrequenzvariabilit¨at und der Energieverbrauch durch die Analyse
der Rohdaten berechnen lassen.

1. **Detektion der R-Zacke und Berechnung der Herzfrequenz**
Die Berechnung der Herzfrequenz kann durch den Abstand zweier aufeinander folgender R-Zacken des QRS-Komplexes vorgenommen werden. Eine
¨ubliche Methode in Python ist die Verwendung der *scipy.signal* Bibliothek
mit der **[find peaks Funktion](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.find_peaks.html)** . Diese funktioniert sehr gut in Kombination
mit einem zus¨atzlichem Threshold, jedoch nur bei sehr sauberen Rohdaten. Auch wenn Sie alle zuvor beschriebenen Schritte befolgt haben, werden sie dennoch Rauschen und verschiedene Arten von Artefakten in Ihren

Daten wiederfinden. Dadurch funktioniert eine einfache Kombination aus
*find peaks* und einem Threshold nicht mehr. F¨ur eine bessere Verarbeitung
der Daten wird ihnen der Code **Lab2Functions** zur Verf¨ugung gestellt.
Dieser ist kommentiert und sollte f¨ur Sie einfach verst¨andlich sein.

Bevor Sie jedoch direkt zum Verwenden dieses Programmes springen, sollten Sie sich zuerst die Rohdaten ansehen und ob diese ein hochfrequentes
Rauschen (ca.50 Hz) beinhalten. Sollte dies der Fall sein, gl¨atten Sie zuerst
die Daten, indem Sie folgenden Code anwenden:

**import** scipy . s i g n a l
b, a = scipy . s i g n a l . butter (4,Wn, ’ low ’, analog=False )
e c g f i l t e r e d = scipy . s i g n a l . f i l t f i l t (b, a, ecg )

Wenn wir uns nun ¨uber die digitalen Filterm¨oglichkeiten der des Butterworth Filters informieren, werden wir auf diese **[Website](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.butter.html)** gelangen. Dort
wird f¨ur unsere kritische Frequenz folgende angegeben: *”For digital filters,*
*if fs is not specified, Wn units are normalized from 0 to 1, where 1 is the*
*Nyquist frequency (Wn is thus in half cycles / sample and defined as 2*cri-*
*tical frequencies / fs).“*
Wenn wir eine Abtastrate von 1000 Hz w¨ahlen, liegt die Nyquist-Frequenz
bei 500 Hz. In diesem Fall ist *Wn = 1*, das Filtern w¨are somit bei 500 Hz.
Bei einem *Wn = 0.5* w¨are die cutoff-Frequenz 250 Hz. Da wir das Rauschen
ab etwa 50 Hz unterdr¨ucken m¨ochten, w¨are somit eine cutoff-Frequenz ab
40 Hz sinnvoll. Daf¨ur m¨ussen wir *Wn = 0.08-0.1* w¨ahlen. Versuchen Sie

verschiedene Werte f¨ur *Wn* und nehmen Sie jenes *Wn* bei dem so viel
hochfrequentes Rauschen gefiltert wird, aber so viele Informationen der eigentlichen EKG-Welle erhalten bleiben. Dokumentieren Sie ihre Auswahl
und plotten Sie original gegen gefiltert in einem Graphen.

Um nun aus dem gefilterten Signal eine die R-Zacken zu identifizieren,

1. Praktikum 12

m¨ussen folgende drei Schritte befolgt werden:

(a) **Hochpunkte der Ableitung des EKG-Signals identifizieren**
Hierf¨ur werden Sie die Ihnen zur Verf¨ugung gestellte Datei
**Lab2Functions.py** verwenden, welche Sie auf Sakai finden k¨onnen.
Daf¨ur m¨ussen Sie die Bibliothek in ihren Code einbinden, indem sie
*import Lab2Functions as ekg* einbinden. Die Funktion ben¨otigt das
EKG-Signal und die Zeit als Input. Es berechnet anschließend die Ableitung des Signals. Danach wird die *find peaks* Funktion verwendet,
um die Hochpunkte und somit die Stellen der st¨arksten Steigung zu
identifizieren. Diese treten beim QRS-Komplex beim Ansteigen zur RZacke auf. Die Funktion gibt die Ableitung und die Indizes der Hochpunkte zur¨uck und k¨onnte folgendermaßen aussehen:

d ECG, peaks d ecg = ekg . decg peaks (ECG, time )

(b) **Entfernen der ”falschen“ Hochpunkte**
In diesem Schritt werden Sie die Funktion *d ecg peaks()* verwenden,
um automatisiert die Peaks der R-Zacken zu finden. Dies geschieht
¨uber einen Threshold Wert und einen minimalen Abstand, den die
Hochpunkte zueinander haben m¨ussen. Als Input m¨ussen die Outputs
der vorherigen Funktion eingesetzt werden, die Zeit sowie der Threshold f¨ur H¨ohe und Distanz zwischen den Hochpunkten (H¨ohe = 0.4,
Distanz = 0.5). Die Funktion sollte nun alle ”echten “ Hochpunkte
ausgeben. Kontrollieren Sie ihre Ergebnisse, indem Sie sich die Plots
anschauen und nehmen Sie entsprechende Feinjustierungen vor, wenn
die gegebene Parameter nicht zum gewollten Ziel f¨uhren. Die Funktion
k¨onnte folgendermaßen aussehen:

Rwave peaks d ecg = ekg . d ecg peaks (d ECG,
peaks d ecg, time, 0.4, 0.5)

(c) **Maximaler Signalwert zwischen zwei abgeleiteten Hochpunk-**
**ten finden**
Die Hochpunkte aus den vergangenen Berechnungen spiegeln nur die
h¨ochsten Steigungen wider, aber nicht die eigentlichen Signal-Maxima.
Daf¨ur soll die Funktion *Rwave peaks()* verwendet werden. Die Funktion betrachtet zwei Maxima der abgeleiteten Daten und sucht dazwischen nach einem Maximum. Dieses sollte kurz nach dem ersten
Ableitungs-Maximum auftreten (in den ersten 20 % zwischen den beiden Maxima). Als Input m¨ussen das EKG-Signal, d ECG, die gefunden
Hochpunkte aus der *d ecg peaks()* Funktion und die Zeit. Als Output

1. Praktikum 13

werden die Zeitpunkte der R-Zacke zur¨uckgegeben. Die angewendete
Funktion k¨onnte folgendermaßen aussehen:

Rwave t = ekg . Rwave peaks (ECG, d ECG,
Rwave peaks d ecg, time )

**Sie sollten nun die Zeitpunkte der R-Zacken erhalten haben!**

2. **Berechnung der Herzfrequenz und Herzfrequenzvariabilit¨at (HRV)**
Berechnen Sie nun die Herzfrequenz ¨uber den Abstand der erhaltenen RZacken. In den Daten werden Sie eventuell Ausreißer haben, welche durch
Messfehler oder den vorherigen Algorithmus verursacht werden. Um diese
einzelnen Ausreißer zu gl¨atten, wird mittels folgendem Code ein weiterer
Butterworth Filter angewendet:

b2, a2 = sp . s i g n a l . butter (4, Wn,
btype=’ lowpass ’ ) *#find a good value* *for Wn*
e x e r c i s e h r f i l t = sp . s i g n a l . f i l t f i l t (b2,
a2, e x e r c i s e h r )

Sie k¨onnen nun die HRV berechnen, indem Sie die ungefilterten Daten verwenden und die numpy Funktion *std()* nutzen.

3. **Sch¨atzung des Energieverbrauches**
Um den Energieverbrauch bei leichten bis schweren Aktivit¨aten sch¨atzen
zu k¨onnen, geben Hiilloskorpie et al. verschiedene Gleichungen an, welche
sie unter dem Paper *“Use of heart rate to predict energy expenditure from*
*low to high activity levels”* ver¨offentlichten [1]. Lesen Sie das auf Sakai zur
Verf¨ugung gestellte Paper und wenden Sie mindestens eine der Formeln an,
um einen Graphen des vorhergesagten Energieverbrauchs ¨uber die Zeit zu
erhalten. Danach k¨onnen Sie die genaue Anzahl der Kalorien berechnen,
welche nach der Formel f¨ur diese Aktivit¨at verbraucht wurden (Ergebnis in
kcal).

1. Praktikum 14
### **Abgabe: Teil 2**

F¨ur Teil 2 des Praktikums werden Sie einen Laborbericht einreichen m¨ussen, in
dem Sie die nachfolgenden Fragen beantworten und ihren Code zur Signalverarbeitung von Biosignalen abgeben. Der Bericht soll in LATEX geschrieben werden.
Die daf¨ur ben¨otigte Vorlage k¨onnen Sie auf Sakai finden.

1. Erstellen Sie ein Diagramm, in dem das kabellose Messsystem dargestellt
wird. Beschriften Sie dabei jede Komponente und beschreiben Sie diese kurz
(Stichpunkte). **(2 Punkte)**

2. Beschreiben Sie was im seriellen Plotter zu erkennen ist, wenn Sie Ihre
Messdaten aufnehmen und der Laptop dabei nicht am Stromnetz angeschlossen ist. Was passiert, wenn Sie mit beiden H¨anden an das Metallgeh¨ause des Laptops greifen und der Laptop am Stromnetz angeschlossen
ist? **(kurze Erkl¨arung, 1 Punkte)**

3. F¨uhren Sie *Aufgabe 1 Teil 4: Experiment in Ruhe* f¨ur jeden Teilnehmer Ihrer Gruppe aus und plotten Sie etwas 5 Sekunden der gefilterten Daten.
Markieren Sie f¨ur einen Teilnehmer die P-Welle, den QRS-Komplex und
die T-Welle im Plot. Beschreiben Sie das physiologische Ph¨anomen, welches f¨ur die jeweiligen elektrischen Signale des EKGs verantwortlich ist. **(1**
**Darstellung mit allen Teilnehmern + Markierung der Wellen f¨ur**
**eine Person, 1 Paragraph, 3 Punkte)**

4. Geben Sie den Code an, welcher f¨ur die Aufnahme der Rohdaten des EKGSignals verantwortlich ist. **(1 Punkt)**

5. Plotten Sie etwa 5 Sekunden des EKG-Signals vom *Experiment in Ruhe*
von einem der Teilnehmer (gefiltert). Nutzen Sie die Ergebnisse der PeakSuche-Funktion, um die R-Zacken im Plot zu labeln. **(1 Darstellung, 1**
**Punkt)**

6. Verwenden Sie Python, um die mittlere Herzfrequenz und HRV (mit der
Standardabweichung) f¨ur jeden der drei Teilnehmer zu bestimmen. Vergleichen Sie die Ergebnisse in einer Tabelle (eine Zeile pro Teilnehmer). Denken
Sie daran, alle Datens¨atze zu den jeweiligen Teilnehmern mit abzugeben.
Die Berechnung soll im Code *MainCode2* stattfinden. **(1 Tabelle, wenige**
**S¨atze, 2 Punkte)**

7. Tragen Sie in dem auf Sakai verf¨ugbaren Dokument *HeartRateData* die
mittlere Herzfrequenz und Herzfrequenzvariabilit¨at f¨ur alle Teilnehmer ein.
Sobald alle Gruppen ihre Messungen und Ergebnisse eingetragen haben,
werden Sie durch den Praktikumsleiter informiert und k¨onnen mit den fol
genden Schritten fortfahren:

1. Praktikum 15

(a) Downloaden Sie das Dokument im Tabellenformat und verwenden Sie
Python, um zwei Histogramme zu erstellen. Eines soll die Verteilung
der mittleren Herzfrequenz der Klasse zeigen, das andere die Herzfrequenzvariabilit¨at. Der Plot soll als Beschriftung Ihren Gruppennamen
enthalten. Die Daten im jeweiligen Plot sollen nach Geschlecht farblich markiert werden. Dies erlaubt einen Vergleich der Herzfrequenz
zwischen den Geschlechtern. Was k¨onnen Sie beobachten? Falls Sie
keine Unterschiede erkennen - was kann die Ursache daf¨ur sein? **(2**
**Darstellungen, 3-5 S¨atze, 3 Punkte)**

(b) Interpretieren Sie Ihre pers¨onlichen Daten in Bezug auf die Gesamtverteilung in der Klasse. **(1 Punkt)**

(c) Vergleichen Sie die Verteilung der mittleren Herzfrequenz der Klasse mit dem, was die Literatur vorgibt. Sind Ihre Aufnahmen wirklich

**”** **[ruhende Herzfrequenzen“]** [? Warum oder warum nicht?] **[ (2 Punk-]**
**te)**

8. Lassen Sie einen Ihrer Gruppenteilnehmer das Experiment in Bewegung
machen, welches in Aufgabe 1 Teil 5 beschrieben ist. Stellen Sie die gefilterte
Herzfrequenz ¨uber die gesamte Zeit dar. **(1 Darstellung, 1 Punkt)**

9. Fokussieren Sie sich nun auf 5.a).i) des Experiments, also dem Ruhen auf
dem Ergometer (2 min).

(a) Plotten Sie die gefilterte Herzfrequenz gegen die Zeit w¨ahrend den
ersten 3 Minuten. Markieren Sie im Plot, wann das Treten und somit
die Steigerung der Leistung beginnt. **(1 Darstellung, 1 Punkt)**

(b) Beschreiben Sie die Dynamik des Anstiegs der Herzfrequenz. Warm
sind Start der Ubung und Anstieg der Herzfrequenz nicht zum selben [¨]
Zeitpunkt? **(1 Punkt)**

(c) Beschreiben Sie, was unter dem Begriff *Cardiac Output* verstanden
wird (2-4 S¨atze). Warum bewirkt eine pl¨otzliche Aktivierung der Muskulatur keine direkte Anderung des Cardiac Outputs? [¨] **(1 Punkt)**

10. Betrachten Sie nun den Zeitabschnitt, in dem der Proband mit der Aktivit¨at
stoppt und die folgenden drei Minuten nach dem Stoppen, w¨ahrend der
Proband seinen Puls erholen l¨asst.

(a) Plotten Sie die gefilterte Herzfrequenz gegen die Zeit (4 Minuten) und
markieren Sie den Plot an der Stelle, bei dem die Aktivit¨at aufgeh¨ort
hat. **(1 Darstellung, 1 Punkt)**

(b) Kommt die Herzfrequenz zum urspr¨ungliche Ruhepuls zur¨uck? Wenn
ja, wie lange hat dies gedauert und warum dauert dieser Prozess so
lange? **(1 Punkt)**

1. Praktikum 16

(c) Denken Sie, dass die Zeit bis zur Erholung der Herzfrequenz bei Athleten k¨urzer ist, als bei untrainierten Personen? Warum? **(1 Punkt)**

11. Lesen Sie das Paper, welches unter Sakai-Ressourcen-Praktikum2-Paper zu
finden ist[1], und erkl¨aren Sie, wie die Autoren die Verbindung zwischen
Herzfrequenz und Energieverbrauch entwickelt haben. Was ist der Unterschied zwischen den drei beschriebene Gleichungen? Welche der Gleichungen w¨urden Sie f¨ur die Berechnung Ihres Energieverbrauchs in diesem Experiment verwenden? Begr¨unden Sie Ihre Auswahl. **(2 Paragraphen, 3**
**Punkte)**

12. Berechnen Sie den metabolischen Energieverbrauch ¨uber die Zeit mit der
Gleichung, welche Sie ausgew¨ahlt haben. Ergibt die relative Anderung des [¨]
metabolischen Energieverbrauchs Sinn f¨ur das, was Sie f¨ur das Experiment
erwarten? Begr¨unden Sie Ihre Aussage. **(1 Darstellung, wenige S¨atze,**
**2 Punkte)**

13. Berechnen Sie den gesamten Energieverbrauch f¨ur das Experiment. Dr¨ucken
Sie das Ergebnis in Einheiten von Joule, Kalorien, Rittersport Tafeln, Bier
und als Anteil des Kalorienbedarfs f¨ur Ihre Person. Formeln zu Berechnung
Ihres t¨aglichen Kalorienbedarfs finden Sie im Internet. Implementieren Sie
Ihre Berechnungen in Python und geben Sie die Ergebnisse im Bericht an.
**(2 Punkte)**

14. Ihr abgegebener Code funktioniert und erzeugt die richtigen Plots, welche
f¨ur diesen Bericht gefordert waren. **(1 Punkt)**

15. Erl¨autern Sie, wie die Herzfrequenzvariabilit¨at Aufschluss ¨uber die Steuerung der Herzfrequenz durch das autonome Nervensystem gibt und warum
dies wichtig ist. Wie k¨onnten sich HRV und HR bei einem Spitzensportler
und einer chronisch kranken Person unterscheiden? Verwenden Sie in Ihrer
Antwort Beispiele und verweisen Sie auf die Literatur. **(1 langer Para-**
**graph (unter einer Seite), 6 Punkte)**

**Gesamte Punkte: 37**

**Abgabe auf Sakai:**
Die Abgabe erfolgt ¨uber das Sakai Portal. Verwenden Sie dabei diese Schreibweise
(Lab1 Group *Groupnumber* ) f¨ur die Gruppeneinreichung und speichern Sie die
folgenden Dateien in dieser *.zip* -Datei:

  - Laborbericht als PDF als *Bericht 2 Gruppe Gruppennummer*

  - Main Skript der Python Auswertung als *MainCode2*

1. Praktikum 17

  - Alle Datens¨atze um *MainCode2* ausf¨uhren zu k¨onnen (z.B. Lab1Frage4)

  - Selbstgeschrieben Python Bibliotheken, welche f¨ur *MainCode2* ben¨otigt
werden

  - **Bitte alles in eine** ***.zip*** **-Datei speichern!!!**

# **Literaturverzeichnis**

[1] H. Hiilloskorpi, M. Pasanen, M. Fogelholm, R. M. Laukkanen, and
A. M¨antt¨ari, “Use of heart rate to predict energy expenditure from low to
high activity levels,” **International journal of sports medicine**, vol. 24,
no. 05, pp. 332–336, 2003.

IV

# **Abbildungsverzeichnis**

1.1 Arduino IDE 1.8.19 . . . . . . . . . . . . . . . . . . . . . . . . . . 3

1.2 EKG Rohdaten . . . . . . . . . . . . . . . . . . . . . . . . . . . . 7

1.3 Seriellen Monitor Daten l¨oschen . . . . . . . . . . . . . . . . . . . 9

V

# **Tabellenverzeichnis**

1.1 Praktikum Hardware Komponenten . . . . . . . . . . . . . . . . . 4

VI

