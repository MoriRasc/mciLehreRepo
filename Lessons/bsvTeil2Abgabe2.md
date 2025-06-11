  - Pflicht: Abgabe der Python Dateien in .zip-File

  - Pflicht: Praktikumsbericht zu übrigen Fragen

Für Teil 2 des Praktikums werden Sie einen Laborbericht einreichen müssen, in
dem Sie die nachfolgenden Fragen beantworten und ihren Code zur Signalverarbeitung von Biosignalen abgeben. Der Bericht soll in LATEX geschrieben werden.
Die dafür benötigte Vorlage können Sie auf Sakai finden.

1. Erstellen Sie ein Diagramm, in dem das kabellose Messsystem dargestellt
wird. Beschriften Sie dabei jede Komponente und beschreiben Sie diese kurz
(Stichpunkte). **(2 Punkte)**

2. Beschreiben Sie was im seriellen Plotter zu erkennen ist, wenn Sie Ihre
Messdaten aufnehmen und der Laptop dabei nicht am Stromnetz angeschlossen ist. Was passiert, wenn Sie mit beiden Händen an das Metallgehäuse des Laptops greifen und der Laptop am Stromnetz angeschlossen
ist? **(kurze Erklärung, 1 Punkte)**

3. Führen Sie *Aufgabe 1: Experiment in Ruhe* für jeden Teilnehmer Ihrer Gruppe aus und plotten Sie etwas 5 Sekunden der gefilterten Daten.
Markieren Sie für einen Teilnehmer die P-Welle, den QRS-Komplex und
die T-Welle im Plot. Beschreiben Sie das physiologische Phänomen, welches für die jeweiligen elektrischen Signale des EKGs verantwortlich ist. **(1 Darstellung mit allen Teilnehmern + Markierung der Wellen für eine Person, 1 Paragraph, 3 Punkte)**

4. Geben Sie den Code an, welcher für die Aufnahme der Rohdaten des EKGSignals verantwortlich ist. **(1 Punkt)**

5. Plotten Sie etwa 5 Sekunden des EKG-Signals vom *Experiment in Ruhe*
von einem der Teilnehmer (gefiltert). Nutzen Sie die Ergebnisse der PeakSuche-Funktion, um die R-Zacken im Plot zu labeln. **(1 Darstellung, 1 Punkt)**

6. Verwenden Sie Python, um die mittlere Herzfrequenz und HRV (mit der
Standardabweichung) für jeden der drei Teilnehmer zu bestimmen. Vergleichen Sie die Ergebnisse in einer Tabelle (eine Zeile pro Teilnehmer). Denken
Sie daran, alle Datensätze zu den jeweiligen Teilnehmern mit abzugeben.
Die Berechnung soll im Code *MainCode2* stattfinden. **(1 Tabelle, wenige Sätze, 2 Punkte)**

7. Tragen Sie in dem auf Sakai verfügbaren Dokument *HeartRateData* die
mittlere Herzfrequenz und Herzfrequenzvariabilität für alle Teilnehmer ein.
Sobald alle Gruppen ihre Messungen und Ergebnisse eingetragen haben,
werden Sie durch den Praktikumsleiter informiert und können mit den folgenden Schritten fortfahren:

    (a) Downloaden Sie das Dokument im Tabellenformat und verwenden Sie
Python, um zwei Histogramme zu erstellen. Eines soll die Verteilung
der mittleren Herzfrequenz der Klasse zeigen, das andere die Herzfrequenzvariabilität. Der Plot soll als Beschriftung Ihren Gruppennamen
enthalten. Die Daten im jeweiligen Plot sollen nach Geschlecht farblich markiert werden. Dies erlaubt einen Vergleich der Herzfrequenz
zwischen den Geschlechtern. Was können Sie beobachten? Falls Sie
keine Unterschiede erkennen - was kann die Ursache dafür sein? **(2 Darstellungen, 3-5 Sätze, 3 Punkte)**

    (b) Interpretieren Sie Ihre persönlichen Daten in Bezug auf die Gesamtverteilung in der Klasse. **(1 Punkt)**

    (c) Vergleichen Sie die Verteilung der mittleren Herzfrequenz der Klasse mit dem, was die Literatur vorgibt. Sind Ihre Aufnahmen wirklich **”[ruhende Herzfrequenzen“]?** Warum oder warum nicht? **(2 Punkte)**

8. Lassen Sie einen Ihrer Gruppenteilnehmer das *Aufgabe 1: Experiment in Bewegung* machen. Stellen Sie die gefilterte Herzfrequenz über die gesamte Zeit dar. **(1 Darstellung, 1 Punkt)**

9. Fokussieren Sie sich nun auf (a).i Teil des Experiments, also dem Ruhen auf dem Ergometer (2 min).

    (a) Plotten Sie die gefilterte Herzfrequenz gegen die Zeit während den
ersten 3 Minuten. Markieren Sie im Plot, wann das Treten und somit
die Steigerung der Leistung beginnt. **(1 Darstellung, 1 Punkt)**

    (b) Beschreiben Sie die Dynamik des Anstiegs der Herzfrequenz. Warm
sind Start der Ubung und Anstieg der Herzfrequenz nicht zum selben [¨]
Zeitpunkt? **(1 Punkt)**

    (c) Beschreiben Sie, was unter dem Begriff *Cardiac Output* verstanden
wird (2-4 Sätze). Warum bewirkt eine plötzliche Aktivierung der Muskulatur keine direkte Anderung des Cardiac Outputs? [¨] **(1 Punkt)**

10. Betrachten Sie nun den Zeitabschnitt, in dem der Proband mit der Aktivität stoppt und die folgenden drei Minuten nach dem Stoppen, während der
Proband seinen Puls erholen lässt.

    (a) Plotten Sie die gefilterte Herzfrequenz gegen die Zeit (4 Minuten) und
markieren Sie den Plot an der Stelle, bei dem die Aktivität aufgehört
hat. **(1 Darstellung, 1 Punkt)**

    (b) Kommt die Herzfrequenz zum ursprüngliche Ruhepuls zurück? Wenn
ja, wie lange hat dies gedauert und warum dauert dieser Prozess so
lange? **(1 Punkt)**
  
    (c) Denken Sie, dass die Zeit bis zur Erholung der Herzfrequenz bei Athleten kürzer ist, als bei untrainierten Personen? Warum? **(1 Punkt)**

11. Lesen Sie das Paper, welches unter Sakai-Ressourcen-Praktikum2-Paper zu
finden ist[1], und erklären Sie, wie die Autoren die Verbindung zwischen
Herzfrequenz und Energieverbrauch entwickelt haben. Was ist der Unterschied zwischen den drei beschriebene Gleichungen? Welche der Gleichungen würden Sie für die Berechnung Ihres Energieverbrauchs in diesem Experiment verwenden? Begründen Sie Ihre Auswahl. **(2 Paragraphen, 3 Punkte)**

12. Berechnen Sie den metabolischen Energieverbrauch über die Zeit mit der
Gleichung, welche Sie ausgewählt haben. Ergibt die relative Änderung des
metabolischen Energieverbrauchs Sinn für das, was Sie für das Experiment
erwarten? Begründen Sie Ihre Aussage. **(1 Darstellung, wenige Sätze, 2 Punkte)**

13. Berechnen Sie den gesamten Energieverbrauch für das Experiment. Drücken
Sie das Ergebnis in Einheiten von Joule, Kalorien, Rittersport Tafeln, Bier
und als Anteil des Kalorienbedarfs für Ihre Person. Formeln zu Berechnung
Ihres täglichen Kalorienbedarfs finden Sie im Internet. Implementieren Sie
Ihre Berechnungen in Python und geben Sie die Ergebnisse im Bericht an.
**(2 Punkte)**

14. Ihr abgegebener Code funktioniert und erzeugt die richtigen Plots, welche
für diesen Bericht gefordert waren. **(1 Punkt)**

15. Erläutern Sie, wie die Herzfrequenzvariabilität Aufschluss über die Steuerung der Herzfrequenz durch das autonome Nervensystem gibt und warum
dies wichtig ist. Wie könnten sich HRV und HR bei einem Spitzensportler
und einer chronisch kranken Person unterscheiden? Verwenden Sie in Ihrer
Antwort Beispiele und verweisen Sie auf die Literatur. **(1 langer Paragraph (unter einer Seite), 6 Punkte)**

**Gesamte Punkte: 37**

## **Abgabe auf Sakai:**
Die Abgabe erfolgt über das Sakai Portal. Verwenden Sie dabei diese Schreibweise (Lab2_*Gruppe_Gruppennummer*) für die Gruppeneinreichung und speichern Sie die
folgenden Dateien in dieser *.zip* -Datei:

  - Laborbericht als PDF als *Bericht_2_Gruppe_Gruppennummer*

  - Main Skript der Python Auswertung als *MainCode2*

  - Alle Datensätze um *MainCode2* ausführen zu können (z.B. Lab1Frage4)

  - Selbstgeschrieben Python Bibliotheken, welche für *MainCode2* benötigt
werden

  - **Bitte alles in eine *.zip* -Datei speichern!!!**

## **Literaturverzeichnis**

[1] H. Hiilloskorpi, M. Pasanen, M. Fogelholm, R. M. Laukkanen, and
A. Mänttäri, “Use of heart rate to predict energy expenditure from low to
high activity levels,” **International journal of sports medicine**, vol. 24,
no. 05, pp. 332–336, 2003.

