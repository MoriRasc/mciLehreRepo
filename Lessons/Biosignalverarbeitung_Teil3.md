### Praktikumsunterlagen
## **Biosignalverarbeitung - Teil 3**
### WS 2024

Bachelorstudiengang
### Medizin-, Gesundheits- und Sporttechnologie

Autoren:
#### *Yannic Heyer / Niklas Brown* *Adaptiert von: Gerda Strutzenberger, PhD / Lukas Neururer*

Letztes Update: 30. September 2024

# **Inhaltsverzeichnis**

**1** **Praktikum** **2**

1.1 Organisatorisches . . . . . . . . . . . . . . . . . . . . . . . . . . . 2

1.2 Teil 3 - Elektromyografie (EMG) . . . . . . . . . . . . . . . . . . 5

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
### **1.2 Teil 3 - Elektromyografie (EMG)**

**ACHTUNG: Sollte ein Studierender bereits EKG Elektroden verwen-**

**det und damit Hautreizungen verursacht haben, soll diese Person im**
**Rahmen dieses Praktikums keine Messungen mit Elektroden durchf¨uhren.**
**Sprechen Sie dies gegebenenfalls mit der Praktikumsleitung ab.**

**Ziele**

1. Aufbau und Testen der Hardware und Software f¨ur EMG-Messungen

2. Bewertung der Muskelaktivit¨at in Abh¨angigkeit von der Belastung

3. Bewertung, wie die Verschiebung von schnell zuckenden zu langsam
zuckenden motorischen Einheiten mit der Muskelerm¨udung korreliert

**Ben¨otigte Komponenten**

1. Mikrocontroller mit USB-Kabel

2. 12 Bit ADC Konverter mit Qwiic Kabel

3. EMG /EKG Sensor mit Elektroden

4. 3 Jumper Kabel

**Ben¨otigte Software**

1. Python (Jupiter Notebook / VS Code)

2. Arduino IDE

**Zus¨atzliche Literatur**

[1. EMG-Fibel [1]](https://www.velamed.com/wp-content/uploads/EMG-FIBEL-V1.1.pdf)

[2. The European Recommendations for Surface Electromyography (SE-](http://www.seniam.org/)
[NIAM) [2]](http://www.seniam.org/)
### **Aufgabe 1: Wie nehme ich EMG Rohdaten auf?**

In dieser Aufgabe lernen Sie, das EMG-Messsystem aufzubauen und damit Rohdaten aufzunehmen. Außerdem werden die Rahmenbedingungen f¨ur kommende
Messungen mit dem EKG-System besprochen.

1. **Verbindung zwischen Sensor und Mikrocontroller**
Die Verbindung der Hardware gleicht dem Setup aus *Teil 2 - Elektrokar-*
*diografie*, welches Sie f¨ur den Aufbau heranziehen k¨onnen.

1. Praktikum 6

2. **Platzierung der Elektroden und Verbindungen**
In diesem Praktikum wird die Muskelaktivit¨at des Bizeps Brachii untersucht. Die beiden Messelektroden sollten einen Abstand von 2 cm von Elek
trodenmitte zu Elektrodenmitte aufweisen und entlang des Muskels auf
dem Muskelbauch platziert sein. Die Referenzelektrode sollte wie bei der
Elektrokardiografie an einem sehr kn¨ochernen K¨orperteil mit wenig Muskelaktivit¨at angebracht werden.

    Weiße Elektrode auf der Mitte des Muskels (Muskelbauch)

    Rote Elektrode in Richtung der Sehne

    Schwarze Elektrode am Handgelenk, da der Abstand zum Messort gering gehalten werden soll

Beim Festkleben der Kabel auf der Haut soll dieses etwas lockerer festgeklebt werden, da somit mehr Spielraum bei der Muskelkontraktion und der
dadurch entstehenden Bewegung entsteht. Dadurch k¨onnen Bewegungsartefakte durch Kabelbewegungen reduziert werden. Bitte verwenden Sie die
**[SENIAM](http://www.seniam.org/)** Website, um dort ¨uber die Punkte *Recommendations →* *Sen-*
*sor Locations* auf die Informationsseite f¨ur den Bizeps Brachii zu gelangen.
Dort finden Sie die Vorschl¨age f¨ur eine optimale Platzierung auf dem Bizeps
Brachii. Allgemeine Informationen f¨ur einen praxisnahen Einstieg in EMG
Messungen k¨onnen Sie in der **[EMG Fibel](http://www.velamed.com/wp-content/uploads/EMG-FIBEL-V1.1.pdf)** von Peter Konrad nachlesen [1].

3. **Datenakquise mit dem EKG-Setup**
Dieser Teil wird durchgef¨uhrt, um die Funktionalit¨at des Setups zu pr¨ufen.
Daf¨ur wird der gleiche Code wie im Praktikumsteil des EKGs verwendet,
um mit dem Code *AnalogReadSerial* und dem seriellen Plotter Daten aufzunehmen. Testen Sie, ob Ihre Muskelaktivit¨at gemessen und dargestellt
werden kann, indem Sie den Bizeps immer wieder anspannen und danach
entspannen. Sie sollten beim Anspannen eine Ver¨anderung der Amplitude
und Frequenz erkennen. Falls das y-Achsen Setting den Graphen unlesbar
macht, entfernen Sie das *Serial.println(sensorValue);* und ersetzen Sie es
mit folgendem Code:

S e r i a l . print ( sensorValue ) ;
S e r i a l . print ( ”,250,400 ” ) ;
S e r i a l . println ( ) ;

Die Werte 250 und 400 stehen f¨ur den y-Achsenabschnitt und ¨andern sich
nicht mehr im seriellen Plotter. Falls Ihre Muskelaktivit¨at eine niedrigere
oder h¨ohere Amplitude aufweist, k¨onnen Sie die Werte h¨andisch anpassen.

1. Praktikum 7

4. **Bessere Aufl¨osung mit einem ADC**
Wenn Sie auf ihren Plotter sehen, k¨onnen Sie diskretisierte Werte erkennen.
Diese Diskretisierung findet durch den Analog-Digital-Konverter (ADC)
statt und ist in der Genauigkeit auch durch diesen begrenzt. Der auf dem
Mikrocontroller verbaute ADC ist nicht besonders genau, weshalb wir einen
12 Bit ADC ¨uber die Qwiic Kabel anschließen werden, um so die Genauigkeit der Messwerte zu erh¨ohen. Die folgenden Schritte beschreiben, wie Sie
den ADC in ihrem Messsystem integrieren:

(a) Verbinden Sie das vierfache Kabel (schwarz/rot/weiß/gelb) mit dem
EMG-Sensor

(b) Anstelle der direkten Verbindung der Jumper-Kabel, werden diese nun
in den ADC ¨uber Schraubklemmen befestigt. Rot ist mit VCC, schwarz
mit GND und gelb mit A0 zu verbinden und mit einem Schraubenzieher festzuziehen.

(c) Den ADC ¨uber ein Qwiic Kabel mit dem Mikrocontroller verbinden

(d) Installieren Sie nun folgende Bibliothek in der Arduino IDE: *SparkFun*
*ADS1015 Arduino Library*

(e) Offnen Sie nun ¨uber [¨] *Datei →* *Beispiele →* *SparkFun ADS1015 Arduino*
*Library →* *Example1 ReadBasic* den Code und laden Sie diesen auf den
Mikrocontroller. **Andern Sie den analogen Kanal im Code auf** **[¨]**
**A0 - dort wird bisher A3 verwendet** .

(f) Offnen Sie den seriellen Plotter und sehen Sie sich die neuen Messdaten [¨]

an.

Anstelle der bisherigen 80 Diskretisierungen werden nun bis zu 300 Schritte
vorgenommen. Sie haben somit eine deutlich feinere Aufl¨osung erreicht und
k¨onnen damit fortfahren. F¨ur das folgende Experiment wird Ihnen der Code
**Lab3Code1** auf Sakai bereitgestellt. Dieser Code erm¨oglicht eine Aufnahme der Rohsignale bei einer Abtastrate von 1000 Hz, wof¨ur die Baud-Rate
auf 500.000 eingestellt ist, um einen schnellen und sicheren Datentransfer
zu gew¨ahrleisten.

5. **Experimente**

(a) **Experiment 1 - Maximum Voluntary Contraction (MVC)**
Die MVC ist ein Parameter, welcher im Krafttraining verwendet wird
und der f¨uhr das Gewicht steht, welches der oder die SportlerIn einfach maximal bew¨altigen kann [3]. Die MVC Messung wird sich f¨ur
jede Person und auch unterschiedliche Anbringung der Elektroden unterscheiden. Bei der Messung soll der Muskel zu 100 % angespannt

1. Praktikum 8

werden. Die Messung f¨ur die MVC muss wiederholt werden, sobald
die Elektroden neu angebracht wurden.

In diesem Experiment werden sie eine isometrische Kraft¨ubung f¨ur die
Messung der MVC verwenden. Bei einer **[isometrische Muskelkon-](https://de.wikipedia.org/wiki/Isometrische_Kontraktion)**
**[traktion](https://de.wikipedia.org/wiki/Isometrische_Kontraktion)** ¨andert sich die L¨ange des Muskels nicht, sondern nur die
Spannung im Muskel [4].
**Schlagen Sie nach, welche isometrischen Maximalkraft Ubun-** **[¨]**
**gen f¨ur Sie durchf¨uhrbar sind. Halten Sie diese schriftlich und**
**auch auf Bildern fest, um diese anschließend in Ihren Prak-**
**tikumsbericht einzubinden.**

F¨ur alle Experimente sollten Sie mindestens 1-2 Sekunden vor und
nach der geplanten Muskelkontraktion eine Pause einlegen und den
Muskel nicht anspannen. Dadurch k¨onnen Sie bei der Analyse Ihrer
Daten besser die Zeitpunkte der Kontraktion identifizieren. Gehen Sie
nun folgendermaßen vor:

i. Nutzen Sie den **Lab3Code1** w¨ahrend Sie mit dem Computer verbunden sind. Passen Sie die Baud Rate im seriellen Monitor auf

500.000 an. Starten Sie den Mikrocontroller.

ii. Greifen Sie z.B. den Tisch mit Ihrer Hand, w¨ahrend der Oberarm
vertikal und der Unterarm um 90° gebeugt ist. Versuchen Sie den
Tisch hochzuheben, ohne dabei den Winkel von 90° zu ver¨andern
(Lassen Sie Ihre Kommilitonen auf dem Tisch sitzen, falls der
Tisch sich dabei bewegen sollte). F¨uhren Sie dieses Heben f¨ur etwa
5 Sekunden aus, wobei Sie mit maximaler Kraft heben m¨ochten.
Versuchen Sie dabei die Kabel so wenig wie m¨oglich zu bewegen.

iii. Trennen Sie den Mikrocontroller vom Laptop.

iv. Machen Sie eine Pause von mindestens 60 Sekunden und wieder
holen Sie den Versuch weitere zwei Male, um drei Datens¨atze f¨ur
die MVC zu erhalten. Kopieren Sie nach jedem Lauf die Daten aus
dem seriellen Monitor in eine Text-Datei und benennen Sie diese
ordentlich (MVC 1,...). **Nehmen Sie nicht alle drei Messun-**
**gen in einem Durchgang auf, da es zu Komplikationen**
**mit dem seriellen Monitor kommen kann. Sie k¨onnen als**

**Sicherheit eine vierte Messung aufnehmen.**

(b) **Experiment 2 - Relative Muskelaktivit¨at**
In diesem Experiment werden Sie ¨ahnlich zum Experiment 1 vorgehen, jedoch mit drei verschiedenen Gewichten, welche bei etwa 25 %,
50 % und 75 % liegen des MVC liegen sollten. Suchen Sie sich also drei
unterschiedliche Gewichte und dokumentieren Sie diese. Nutzen Sie

1. Praktikum 9

folgende Vorgehensweise:

i. Halten Sie das Gewicht in derselben Position wie in Experiment
1 (90° Winkel)

ii. Schalten Sie den Mikrocontroller an mit dem **Lab3Code1** und

halten Sie das leichteste Gewicht f¨ur 10 Sekunden

iii. Trennen Sie den Mikrocontroller und Laptop, speichern Sie die
Daten aus dem seriellen Monitor. Machen Sie eine Pause von mind.

40 Sekunden **und wiederholen Sie die Messung mit dem**
**mittleren und schweren Gewicht**

(c) **Experiment 3 - Erm¨udung** In diesem Experiment werden Sie eine
Erm¨udung des Muskels messen, indem Sie ein ¨ahnliches Setup wie in
Experiment 1 verwenden. Gehen Sie folgendermaßen vor:

i. Gehen Sie zur¨uck zum Tisch, welchen Sie zum heben verwendet
haben

ii. Nutzen Sie **Lab3Code1** und starten Sie die Messung. Messen Sie
die maximale Kontraktion (so stark wie m¨oglich!) ¨uber volle 10-15
Sekunden

iii. Trennen Sie den Mikrocontroller und Laptop, speichern Sie die
Daten aus dem seriellen Monitor. Machen Sie eine Pause von mind.

60 Sekunden **und wiederholen Sie die Messung zweimal,**
**sodass Sie drei Datens¨atze der Erm¨udung erhalten.**
### **Aufgabe 2: Analyse der Rohdaten**

In diesem Kapitel werden Sie das Verarbeiten von EMG Daten erlernen, die MVC
und die Muskelaktivit¨at berechnen und eine Frequenzanalyse durchf¨uhren. Ziehen
Sie daf¨ur den Python Code der letzten Vorlesung heran.

1. **Vorverarbeiten der EMG Daten**

Die Verarbeitung von EMG Rohdaten ist etwas komplizierter als beim EKG.
Dies liegt an den viele St¨orquellen und Artefakten, die sich mit dem Signal ¨uberlagern. Als Erstes wird das Offset von der Nulllinie sichtbar, welches entfernt werden muss. Bewegungen der Kabel w¨ahrend den Messungen
k¨onnen außerdem tiefe St¨orfrequenzen verursachen, elektrisches Rauschen
hingegen verursacht hochfrequent Uberlagerungen. Um das Signal der Mus- [¨]
keln zu erhalten, m¨ussen wir also die Rohdaten Tief- und Hochpassfiltern.
Das EMG Signal tendiert zu einer Schwingung um den Nullpunkt. Diese
Schwingung gilt es zu eliminieren, indem die Absolutwerte zur Berechnung
herangezogen werden. Abschließend werden die Daten nochmals Tiefpass

1. Praktikum 10

gefiltert, um eine Einh¨ullende der absoluten Werte zu bilden. Die Verarbeitung wird nachfolgend in vier Schritte aufgeteilt.

(a) Offset eliminieren

(b) EMG Signal filtern (20 bis 450 Hz Butterworth)

(c) Gleichrichten des Signals

(d) Einh¨ullende bilden

F¨ur die folgenden Schritte werden Sie die Python Bibliotheken *matplot-*
*lib.pyplot*, *numpy*, *scipy.signal* und die Ihnen auf Sakai zur Verf¨ugung gestellte Bibliothek *Lab3Functions* ben¨otigen. Ihnen werden gewisse Teile des
Codes zur Verf¨ugung gestellt, um die Struktur des Codes vorzugeben und
eine gleiche Benennung der Variablen zu gew¨ahrleisten. Der Code, den Sie
f¨ur dieses Praktikum schreiben werden, ist ein großer Bestandteil der Bewertung. Ihre neun Datens¨atze (3xMVC, 3xGewichte, 3xErm¨udung) sollten in einem Ordner mit ihrem Code gespeichert werden. Benennen Sie die
Datens¨atze MVC1, MVC2, MVC3, Weight1, Weight2, Weight3, Fatique1,
Fatique2 und Fatique3. Danach k¨onnen Sie die funktion *import.data()* des
Ihnen zur Verf¨ugung gestellten Codes verwenden, um die Datens¨atze in drei
Variablen zu komprimieren. Dies k¨onnte folgendermaßen aussehen, wobei
auf den richten Separator zu achten ist:

weights, mvc, f ati gue = l f 3 . import data ( ’ *\* t ’ )

Erf¨ullen Sie nun die vier angegebenen Schritte. In Abbildungen 1.2, 1.3, 1.4
und 1.5 werden die vier Schritte an Beispieldaten gezeigt und sollen Ihnen
als Kontrolle dienen.

Abbildung 1.2: Offset-Korrektur der EMG-Daten.

1. Praktikum 11

Abbildung 1.3: Filtern der EMG-Daten.

Abbildung 1.4: Gleichrichten der EMG-Daten.

1. Praktikum 12

Abbildung 1.5: Einh¨ullende der EMG-Daten. Verwenden Sie eine
Tiefpass Grenzfrequenz von 3 Hz, um eine Einh¨ullende zu erzeugen.
Testen Sie auch andere Grenzfrequenzen bzw. setzen Sie eigene Algorithmen um.

2. **Berechnung der MVC und der relativen Muskelaktivit¨at**
Um die MVC zu berechnen, sollen die drei Durchl¨aufe gemittelt werden. Um
die Muskelaktivierung zu betrachten, m¨ussen wir jedoch erst die neutralen
Daten (keine Anspannung) von den aktivierten (volle Anspannung) trennen.
Schauen Sie sich daf¨ur die Plots der MVC an und finden Sie die Zeitpunkte,
wo die Aktivierungen beginnen und enden. W¨ahlen Sie zur Sicherheit ein
paar Zeitpunkte nach Aktivierung und vor Ende der Aktivierung. Gehen
Sie sicher, dass in der Zeit der Muskel maximal aktiviert war (Amplitude).
Diese Zeitpunkte k¨onnten zum Beispiel wie in Abbildung 1.6 aussehen.

Da dieser Prozess sehr zeitintensiv ist, wird Ihnen ein Code bereitgestellt,
der die Auswahl der Zeitpunkte vereinfacht. Nehmen Sie daf¨ur den Code
**Lab3Functions** und die dort implementierte *get bursts* Funktion. Diese
nimmt drei Input Argumente, welche die gefilterten Daten der drei Experimente sind. Sie werden gebeten, in den Plot hineinzuzoomen, um ein
Zeitintervall auszuw¨ahlen. Daf¨ur m¨ussen Sie die *Enter* -Taste dr¨ucken. Dies

erlaubt Ihnen, einen Start und Endpunkt festzulegen. F¨uhren Sie dies f¨ur
alle drei Bursts und f¨ur die drei verschiedenen Experimente aus. Die Anwendung der Funktion k¨onnte folgendermaßen aussehen:

mvc s, mvc e, weights s, weights e, f a t i g u e s, f a t i g u e e = l 3 f . g e t b u r s t s (
mvc emg filtered, w e i g h t s e m g f i l t e r e d, f a t i g u e e m g f i l t e r e d )

Mit den Start und Endpunkten der drei Burst-Signalen des MVC kann
nun die gemittelte Aktivierung der Muskeln berechnet werden. Nehmen Sie
daf¨ur die Einh¨ullende der drei Bursts und berechnen Sie mit der numpy
*mean()* Funktion den Mittelwert. Mitteln Sie auch ¨uber Ihre drei Versuche,
danach erhalten Sie Ihren pers¨onlichen MVC, welche ab diesem Zeitpunkt
das Maximum darstellt. Demnach werden alle weiteren Berechnungen in %

1. Praktikum 13

Abbildung 1.6: Grafische Darstellung der Aktivierungsdauer von
drei MVC Datens¨atzen.

1. Praktikum 14

von MVC angegeben.

Um die Muskelaktivit¨at f¨ur Experiment 2 und 3 (Gewicht & Erm¨udung) zu
bestimmten, berechnen Sie auch hier den Mittelwert der einzelnen Bursts
(nicht ¨uber alle drei Messungen) und setzen Sie das Ergebnis in Relation
zum MVC. Dies k¨onnte ausformuliert so klingen: ”In Experiment 2 ergibt
sich bei einem Gewicht von 50 % des MVC eine gemessene Muskelaktivierung von XYZ % der maximalen willk¨urlichen Kontraktion. “

3. **Berechnung der Spektralen Leistungsdichte**
F¨ur die Analyse von EMG-Signalen wird oft die spektrale Leistungsdichte
bzw. eine Frequenzanalyse herangezogen. Dies wird nochmals unter folgen[dem Link beschrieben und erkl¨art (Englisch). Die Frequenzanalyse beruht](https://www.intechopen.com/chapters/40123)
[auf der Fast Fourier Transformation, welche Sie unter folgendem Link als](https://www.youtube.com/watch?v=spUNpyF58BY)
YouTube Video zur Wiederholung ansehen k¨onnen. Mit dieser Anleitung
werden Sie eine Spektralanalyse an Ihren EMG-Daten durchf¨uhren k¨onnen.
Daf¨ur m¨ussen Sie Ihre gefilterten Daten (Offset eliminiert und gefiltert) verwendet und folgende Schritte durchf¨uhren:

(a) Isolieren Sie jeweils 0.5 Sekunden zu Beginn, in der Mitte und am Ende einer Aktivierung (Burst). Dadurch werden Sie drei neue Variablen
erzeugen, welche jeweils einen Datensatz mit einer L¨ange von 0.5 Sekunden enthalten. Dies ist exemplarisch in Abbildung 1.7 dargestellt.

Abbildung 1.7: Auswahl von drei 0.5 Sekunden langen Intervallen
am Anfang, in der Mitte und zum Ende einer EMG-Aktivierung.

(b) Berechnen Sie nun f¨ur jeden der drei isolierten Teile die spektrale Leistungsdichte mit der *get power* Funktion aus dem **Lab3Functions**
Code.

1. Praktikum 15

power, f r e q u e n c i e s = l 3 f . get power (EMGdata, s a m p l i n g f r e q )

Das Ergebnis der Funktion sollte ¨ahnlich wie in Abbildung 1.8 aussehen.

Abbildung 1.8: Auswahl von drei 0.5 Sekunden langen Intervallen
am Anfang, in der Mitte und zum Ende einer EMG-Aktivierung.

(c) Filtern Sie die spektrale Leistungsdichte mit dem gleichen *butterworth*
Filter, mit dem Sie auch die Einh¨ullende der Muskelaktivit¨at berechnet
haben und einer cutoff-Frequenz von 40 Hz. Das gefilterte Spektrum
wird in Abbildung 1.9 gezeigt.

1. Praktikum 16

Abbildung 1.9: Auswahl von eines 0.5 Sekunden langen Intervalls
nach Anwendung der Filter.

4. **Kontraktionsgeschwindigkeiten der Muskelfasern**
Um die Ver¨anderung der Kontraktionsgeschwinkeiten ¨uber die Zeit zu berechnen, m¨ussen das Frequenzspektrum und die darin dominanten Frequenzen f¨ur die drei Zeitpunkte w¨ahrend der Messung berechnet werden. Der
Median der spektralen Leistungsdichte ist daf¨ur ein passender Parameter.
Um die Median-Frequenz zu berechnen, muss erst die Fl¨ache unter der Kurve berechnet werden, welche die gesamte Leistung darstellt. Danach wird
der Punkt gesucht, welche die Fl¨ache gleichm¨aßig in zwei H¨alften teilt (Abb.
1.10). Daf¨ur kann der folgende Code verwendet werden:

a r ea f r eq = scipy . integrate . cumtrapz ( power, frequencies,
i n i t i a l =0)
total power = a r e a f r eq [ −1]
median freq = frequencies [ np . where ( a r ea f r eq
*>* = total power / 2 ) [ 0 ] [ 0 ] ]

1. Praktikum 17

Abbildung 1.10: Gefilterte Spektrale Leistungsdichte mit berechnetem Median.

Wiederholen Sie die Schritte f¨ur die drei Messungen f¨ur das Experiment
3, um die Erm¨udung zu analysieren. Danach k¨onnen Sie die ermittelten
Median-Frequenzen mit dem Zeitpunkt in der Messung plotten (siehe Abbildung 1.11

Abbildung 1.11: Median-Frequenzen bei Erm¨udungen drei unterschiedlichen Zeitpunkte.

1. Praktikum 18

Abbildung 1.12: Median-Frequenzen bei Erm¨udungen drei unterschiedlichen Zeitpunkte einer Messung.

1. Praktikum 19
### **Abgabe: Teil 3**

F¨ur Teil 3 des Praktikums werden Sie einen Laborbericht einreichen m¨ussen, in
dem Sie die nachfolgenden Fragen beantworten und ihren Code zur Signalverarbeitung von Biosignalen abgeben. Der Bericht soll in LATEX geschrieben werden.
Die daf¨ur ben¨otigte Vorlage k¨onnen Sie auf Sakai finden.

1. Zeigen Sie ein Diagramm der Komponenten des tragbaren Systems, das Ihre Gruppe zur Erfassung und Aufzeichnung von EMG-Daten w¨ahrend des
MVC-Experiments verwendet hat. F¨ugen Sie den Muskel und die Elektrodenplatzierung in dieses Diagramm ein. Beschriften Sie diese Komponenten
und erl¨autern Sie die Funktion der einzelnen Komponenten. Wenn die Komponenten bereits in fr¨uheren Arbeiten verwendet wurden, geben Sie an, wie
sie in diesem Experiment anders eingesetzt wurden. **(1 Darstellung, Ab-**
**satz oder Notizen, 3 Punkte)**

2. Zeigen Sie von einem Gruppenmitglied Screenshots des seriellen Plotters,
nachdem Sie folgende 3 Konfigurationen durchgef¨uhrt haben.

    Analog Serial Read (Achsen wie in Aufgabe 1.3 ¨andern)

    Analog Serial Read

**void** setup () *{*
S e r i a l . begin (9600);
analogReference (EXTERNAL) ;
*}*

WICHTIG: neues Jumper Kabel von 3,3 V auf AREF auf dem Arduino
Board

    ADC Setup - Lab3Code1

Beschriften Sie die Onsets und Offsets der Bursts. Geben Sie die Amplituden
f¨ur jeden Burst an und beschreiben Sie die Unterschiede, die Sie feststellen.
**(3 beschriftete Screenshots, wenige S¨atze; 3 Punkte)**

3. Stellen Sie sich vor, Sie versuchen, Ihren Bizeps zu kontrahieren.

(a) Wie kann ein einzelnes motorisches Neuron, ausgehend von der neuromuskul¨aren Verbindung, ein Aktionspotenzial in einer Muskelfaser
ausl¨osen? **(1 Absatz; 1 Punkt)**

(b) Wie f¨uhrt ein Aktionspotenzial in einer Muskelfaser zu einer Muskelkontraktion? **(1 Absatz; 1 Punkt)**

1. Praktikum 20

4. Erl¨autern Sie in einem Absatz, wie die Aktivit¨at der einzelnen Muskelfasern zu dem von den EMG-Elektroden gemessenen zusammengesetzten
Aktionspotenzial beitr¨agt. Beschreiben Sie, wie die gemessene Muskelaktivit¨at durch die Gr¨oße und Lage der Muskelfasern bestimmt wird und wie sie
durch subkutanes Fett beeinflusst wird. Erl¨autern Sie auch, wie das Gr¨oßenprinzip bestimmt, welche Fasern mehr beitragen, wenn Aktivit¨at und Kraft
gering sind **(1 Absatz; 3 Punkte)**

5. F¨uhren Sie Teil 5, Experiment 1 - MVC, dieses Praktikums durch. Verarbeiten Sie die Daten eines Gruppenmitglieds vor (Mittelwert entfernen, filtern,
gleichrichten, H¨ullkurve) und pr¨asentieren Sie die Ergebnisse. Erl¨autern Sie,
wie Sie die Daten vorverarbeitet haben und warum jeder Schritt notwendig
ist **(1 Abbildung mit 3 Subplots; 1 Absatz, 3 Punkte)**

6. Geben Sie in einer Tabelle die mittlere MVC-Muskelaktivit¨at f¨ur jedes Mitglied Ihrer Gruppe an. Geben Sie unbedingt die Einheiten an. Wenn die Daten in irgendeiner Weise ungew¨ohnlich sind (z. B. die MVC eines Mitglieds
ist viel h¨oher oder niedriger als die aller anderen), beschreiben Sie bitte die
Probleme und stellen Sie eine Hypothese auf, warum sie aufgetreten sein
k¨onnten **(1 Tabelle mit kleiner Erkl¨arung; 1 Punkt)**

7. Beschreiben Sie kurz den Aufbau Ihres MVC-Experiments. Warum erlaubt
dieser Aufbau dem Muskel, sich maximal zu kontrahieren? **(2 Punkte)**

8. F¨uhren Sie Experiment 2 - Relative Muskelaktivierung - aus diesem Praktikum durch. Stellen Sie die relative Muskelaktivit¨at (d. h. als Prozentsatz
der MVC-Messung) gegen die Gr¨oße des Gewichts/Widerstands f¨ur ein einzelnes Gruppenmitglied dar. Erl¨autern Sie in wenigen S¨atzen die physiologischen Mechanismen, die der aufgezeichneten Beziehung zugrunde liegen.
**(1 Abbildung, wenige S¨atze; 2 Punkte)**

9. F¨uhren Sie Teil 5, Experiment 3 - Erm¨udung, aus diesem Praktikum durch.
F¨uhren Sie eine Analyse im Frequenzspektrum zu Beginn, in der Mitte
und am Ende jedes der drei Erm¨udungsexperimente durch (insgesamt 9).
Zeichnen Sie eines der 9 Leistungsspektren von einem Ihrer Gruppenmitglieder auf (beachten Sie, dass MainCode3 alle 9 Plots enthalten sollte). Die
Darstellung sollte das rohe Leistungsspektrum, das gefilterte Leistungsspektrum und die durchschnittliche Frequenz des gefilterten Leistungsspektrums
enthalten. **(1 Abbildung; 2 Punkte)**

10. Erl¨autern Sie mit Worten und Diagrammen, wie das Leistungsspektrum
den Frequenzgehalt des gemessenen EMGs darstellt. Hinweis: Erl¨autern Sie
die Fasertypen. **(Diagramm(e) und 1 Absatz; 3 Punkte)**

1. Praktikum 21

11. Berechnen Sie die Medianfrequenz jedes Leistungsspektrums und stellen Sie
die Ver¨anderung der Medianfrequenz zu Beginn, in der Mitte und am Ende
jedes Erm¨udungstests f¨ur eines Ihrer Gruppenmitglieder dar (siehe 1.12).
Die Abbildung sollte neun Datenpunkte enthalten, wobei die drei Datenpunkte jedes Versuchs durch Linien verbunden werden. Erl¨autern Sie in ein
paar S¨atzen, ob diese Muster Ihren Erwartungen entsprechen und warum,
einschließlich der Frage, ob die Muster zwischen den drei wiederholten Versuchen konsistent sind. **(1 Abbildung, ein paar S¨atze; 3 Punkte)**

12. Erl¨autern Sie anhand recherchierter Quellen, wie EMG zum Betrieb myoelektrischer Prothesen eingesetzt wird. Beschreiben Sie kurz eine andere Situation, in der EMG in einem klinischen Umfeld n¨utzlich oder angemessen
ist (zitieren Sie mindestens eine Studie, die diese Methode verwendet, und
fassen Sie sie kurz zusammen - kurz heißt hier 3-5 S¨atze, um die Kernaussage zu erfassen). **(Nicht mehr als 1 Seite - Zitieren nicht vergessen!!!**
**; 6 Punkte)**

13. Ihr abgegebener Code funktioniert und erzeugt mit den abgegebenen Daten
die richtigen Plots, welche f¨ur diesen Bericht gefordert waren. **(1 Punkt)**

**Gesamte Punkte: 34**

**Abgabe auf Sakai:**
Die Abgabe erfolgt ¨uber das Sakai Portal. Verwenden Sie dabei diese Schreibweise
(Lab3 *Groupnumber* ) f¨ur die Gruppeneinreichung und speichern Sie die folgenden
Dateien in dieser *.zip* -Datei:

  - Laborbericht als PDF als *Bericht 3 Gruppennummer*

  - Main Skript der Python Auswertung als *MainCode3*

  - Alle Datens¨atze um *MainCode3* ausf¨uhren zu k¨onnen

  - Selbstgeschrieben Python Bibliotheken, welche f¨ur *MainCode3* ben¨otigt
werden

  - **Bitte alles in eine** ***.zip*** **-Datei speichern!!!**

# **Literaturverzeichnis**

[1] P. Konrad, “Emg-fibel,” **Eine praxisorientierte Einf¨uhrung in die kine-**
**siologische Elektromyographie**, 2011.

[2] H. J. Hermens, B. Freriks, R. Merletti, D. Stegeman, J. Blok, G. Rau,
C. Disselhorst-Klug, and G. H¨agg, “European recommendations for surface
electromyography,” **Roessingh research and development**, vol. 8, no. 2,
pp. 13–54, 1999.

[[3] Website, online erh¨altlich unter: https://www.sportbachelor.com/lexikon/](https://www.sportbachelor.com/lexikon/maximum-voluntary-contraction-mvc/)
[maximum-voluntary-contraction-mvc/; abgerufen am 25. August 2022.](https://www.sportbachelor.com/lexikon/maximum-voluntary-contraction-mvc/)

[[4] Website, online erh¨altlich unter: https://de.wikipedia.org/wiki/Isometrische](https://de.wikipedia.org/wiki/Isometrische_Kontraktion)

[Kontraktion; abgerufen am 25. August 2022.](https://de.wikipedia.org/wiki/Isometrische_Kontraktion)

IV

# **Abbildungsverzeichnis**

1.1 Arduino IDE 1.8.19 . . . . . . . . . . . . . . . . . . . . . . . . . . 3

1.2 Offset-Korrektur der EMG-Daten . . . . . . . . . . . . . . . . . . 10

1.3 Filtern der EMG-Daten . . . . . . . . . . . . . . . . . . . . . . . 11

1.4 Gleichrichten der EMG-Daten . . . . . . . . . . . . . . . . . . . . 11

1.5 Einh¨ullender der EMG-Daten . . . . . . . . . . . . . . . . . . . . 12

1.6 MVC Aktivierungsdauer . . . . . . . . . . . . . . . . . . . . . . . 13

1.7 Burst isoliertes Signal . . . . . . . . . . . . . . . . . . . . . . . . . 14

1.8 Burst isoliertes Signal . . . . . . . . . . . . . . . . . . . . . . . . . 15

1.9 Burst isoliertes Signal . . . . . . . . . . . . . . . . . . . . . . . . . 16

1.10 Spektrales Leistungsdichte mit Median . . . . . . . . . . . . . . . 17

1.11 Median-Frequenzen bei Erm¨udung . . . . . . . . . . . . . . . . . . 17

1.12 Median-Frequenzen bei Erm¨udung . . . . . . . . . . . . . . . . . . 18

V

# **Tabellenverzeichnis**

1.1 Praktikum Hardware Komponenten . . . . . . . . . . . . . . . . . 4

VI

