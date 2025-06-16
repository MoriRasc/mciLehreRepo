# **Aufgabe 2: Analyse der Rohdaten**

In diesem Teil des Praktikums werden Sie lernen bzw. vertiefen, wie sich die Herzfrequenz, Herzfrequenzvariabilität und der Energieverbrauch durch die Analyseder Rohdaten berechnen lassen.

## **Detektion der R-Zacke und Berechnung der Herzfrequenz**

Die Berechnung der Herzfrequenz kann durch den Abstand zweier aufeinander folgender R-Zacken des QRS-Komplexes vorgenommen werden. Eine
übliche Methode in Python ist die Verwendung der *scipy.signal* Bibliothek
mit der **[find peaks Funktion](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.find_peaks.html){:target="_blank"}** . Diese funktioniert sehr gut in Kombination
mit einem zusätzlichem Threshold, jedoch nur bei sehr sauberen Rohdaten. Auch wenn Sie alle zuvor beschriebenen Schritte befolgt haben, werden sie dennoch Rauschen und verschiedene Arten von Artefakten in Ihren

Daten wiederfinden. Dadurch funktioniert eine einfache Kombination aus
*find peaks* und einem Threshold nicht mehr. Für eine bessere Verarbeitung
der Daten wird ihnen der Code **Lab2Functions** zur Verfügung gestellt.
Dieser ist kommentiert und sollte für Sie einfach verständlich sein.

Bevor Sie jedoch direkt zum Verwenden dieses Programmes springen, sollten Sie sich zuerst die Rohdaten ansehen und ob diese ein hochfrequentes
Rauschen (ca.50 Hz) beinhalten. Sollte dies der Fall sein, glätten Sie zuerst
die Daten, indem Sie folgenden Code anwenden:

````python
import scipy.signal
b, a = scipy.signal.butter(4, Wn, ’low’, analog=False)
ecg_filtered = scipy.signal.filtfilt(b, a, ecg)
````
Wenn wir uns nun über die digitalen Filtermöglichkeiten der des Butterworth Filters informieren, werden wir auf diese **[Website](https://docs.scipy.org/doc/scipy/reference/generated/scipy.signal.butter.html){:target="_blank"}** gelangen. Dort
wird für unsere kritische Frequenz folgende angegeben: *”For digital filters,if fs is not specified, Wn units are normalized from 0 to 1, where 1 is the Nyquist frequency (Wn is thus in half cycles / sample and defined as 2`*`critical frequencies / fs).“*

Wenn wir eine Abtastrate von 1000 Hz wählen, liegt die Nyquist-Frequenz
bei 500 Hz. In diesem Fall ist *Wn = 1*, das Filtern wäre somit bei 500 Hz.
Bei einem *Wn = 0.5* wäre die cutoff-Frequenz 250 Hz. Da wir das Rauschen
ab etwa 50 Hz unterdrücken möchten, wäre somit eine cutoff-Frequenz ab
40 Hz sinnvoll. Dafür müssen wir *Wn = 0.08-0.1* wählen. Versuchen Sie

verschiedene Werte für *Wn* und nehmen Sie jenes *Wn* bei dem so viel
hochfrequentes Rauschen gefiltert wird, aber so viele Informationen der eigentlichen EKG-Welle erhalten bleiben. Dokumentieren Sie ihre Auswahl
und plotten Sie original gegen gefiltert in einem Graphen.

Um nun aus dem gefilterten Signal eine die R-Zacken zu identifizieren,
müssen folgende drei Schritte befolgt werden:

1. **Hochpunkte der Ableitung des EKG-Signals identifizieren**
Hierfür werden Sie die Ihnen zur Verfügung gestellte Datei
**Lab2Functions.py** verwenden, welche Sie auf Sakai finden können.
Dafür müssen Sie die Bibliothek in ihren Code einbinden, indem sie
*import Lab2Functions as ekg* einbinden. Die Funktion benötigt das
EKG-Signal und die Zeit als Input. Es berechnet anschließend die Ableitung des Signals. Danach wird die *find peaks* Funktion verwendet,
um die Hochpunkte und somit die Stellen der stärksten Steigung zu
identifizieren. Diese treten beim QRS-Komplex beim Ansteigen zur RZacke auf. Die Funktion gibt die Ableitung und die Indizes der Hochpunkte zurück und könnte folgendermaßen aussehen:

````python
d_ECG, peaks_d_ecg = ekg.decg_peaks(ECG, time)
````

2. **Entfernen der ”falschen“ Hochpunkte**

In diesem Schritt werden Sie die Funktion *d_ecg_peaks()* verwenden,
um automatisiert die Peaks der R-Zacken zu finden. Dies geschieht
über einen Threshold Wert und einen minimalen Abstand, den die
Hochpunkte zueinander haben müssen. Als Input müssen die Outputs
der vorherigen Funktion eingesetzt werden, die Zeit sowie der Threshold für Höhe und Distanz zwischen den Hochpunkten (Höhe = 0.4,
Distanz = 0.5). Die Funktion sollte nun alle ”echten “ Hochpunkte
ausgeben. Kontrollieren Sie ihre Ergebnisse, indem Sie sich die Plots
anschauen und nehmen Sie entsprechende Feinjustierungen vor, wenn
die gegebene Parameter nicht zum gewollten Ziel führen. Die Funktion
könnte folgendermaßen aussehen:
````python
Rwave_peaks_d_ecg = ekg.d_ecg_peaks(d_ECG, peaks_d_ecg, time, 0.4, 0.5)
````

3. **Maximaler Signalwert zwischen zwei abgeleiteten Hochpunkten finden**

Die Hochpunkte aus den vergangenen Berechnungen spiegeln nur die
höchsten Steigungen wider, aber nicht die eigentlichen Signal-Maxima.
Dafür soll die Funktion *Rwave_peaks()* verwendet werden. Die Funktion betrachtet zwei Maxima der abgeleiteten Daten und sucht dazwischen nach einem Maximum. Dieses sollte kurz nach dem ersten
Ableitungs-Maximum auftreten (in den ersten 20 % zwischen den beiden Maxima). Als Input müssen das EKG-Signal, d ECG, die gefunden
Hochpunkte aus der *d_ecg_peaks()* Funktion und die Zeit. Als Output
werden die Zeitpunkte der R-Zacke zurückgegeben. Die angewendete
Funktion könnte folgendermaßen aussehen:

````python
Rwave_t = ekg.Rwave_peaks(ECG, d_ECG, Rwave_peaks_d_ecg, time)
````
**Sie sollten nun die Zeitpunkte der R-Zacken erhalten haben!**

## **Berechnung der Herzfrequenz und Herzfrequenzvariabilität (HRV)**
Berechnen Sie nun die Herzfrequenz über den Abstand der erhaltenen RZacken. In den Daten werden Sie eventuell Ausreißer haben, welche durch
Messfehler oder den vorherigen Algorithmus verursacht werden. Um diese
einzelnen Ausreißer zu glätten, wird mittels folgendem Code ein weiterer
Butterworth Filter angewendet:

````python
b2, a2 = sp.signal.butter(4, Wn, btype=’lowpass’) #find a good value for Wn
exercise_hr_filt = sp.signal.filtfilt(b2, a2, exercise_hr)
````
Sie können nun die HRV berechnen, indem Sie die ungefilterten Daten verwenden und die numpy Funktion *std()* nutzen.

## **Schätzung des Energieverbrauches**
Um den Energieverbrauch bei leichten bis schweren Aktivitäten schätzen
zu können, geben Hiilloskorpie et al. verschiedene Gleichungen an, welche
sie unter dem Paper *“Use of heart rate to predict energy expenditure from*
*low to high activity levels”* veröffentlichten [[1]](#1). Lesen Sie das auf Sakai zur
Verfügung gestellte Paper und wenden Sie mindestens eine der Formeln an,
um einen Graphen des vorhergesagten Energieverbrauchs über die Zeit zu
erhalten. Danach können Sie die genaue Anzahl der Kalorien berechnen,
welche nach der Formel für diese Aktivität verbraucht wurden (Ergebnis in
kcal).


## Literaturverzeichnis
<a id="1">[1]</a> 
H. Hiilloskorpi, M. Pasanen, M. Fogelholm, R. M. Laukkanen, and
A. Mänttäri, “Use of heart rate to predict energy expenditure from low to
high activity levels,” **International journal of sports medicine**, vol. 24,
no. 05, pp. 332–336, 2003.