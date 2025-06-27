
  - Pflicht: Abgabe der Python Dateien in .zip-File (**Main Skript der Python Auswertung als *MainCode1.ipynb***)

  - Freiwillig: Praktikumsbericht zu übrigen Fragen

Für Teil 1 des Praktikums werden Sie **keinen** Laborbericht einreichen müssen, sondern nur ihren Python Code, mit dem Sie die Signale verarbeitet haben. Sie haben dennoch die Möglichkeit alle folgenden Fragen zu beantworten und im Rahmen eines Laborberichtes abzugeben. Dadurch bekommen Sie vor den eigentlich bewerteten Laborberichten Feedback und können dieses direkt in die Folgenden Berichte einbauen. Dabei geht es vor allem um die Form der Laborbericht und nicht den Inhalt. Der Bericht soll in LATEX geschrieben werden. Die dafür benötigte Vorlage können Sie auf Sakai finden.

**Die Abgabe des Python Codes umfasst das Bearbeiten der Aufgaben:**

  - 5 (a)

  - 6

  - 8 (a)

  - 9
  - 10

  - 12
  - 13

Es wird empfohlen das Python Scripts als **.ipynb** aufzubauen und die genannten Aufgaben untereinander abzuarbeiten.

1. Erstellen Sie Diagramme, in denen das kabellose Messsystem dargestellt ist. Beschriften Sie jede Komponente, jeden Bus (einschließlich Bustyp und -geschwindigkeit) sowie jeden Signalpfad, und beschreiben Sie diese jeweils kurz. (1-2 Sätze pro Komponente). **(3 Punkte)**

2. Arbeiten Sie folgende Fragen aus **(2 Punkte)** :

    (a) Welches Messverfahren verwendet Ihr Beschleunigungssensor?

    (b) Wie würden Sie den Beschleunigungssensor kalibrieren, um valide Daten aufzunehmen?

    (c) Beschreiben Sie die Messdaten Ihres Beschleunigungssensors, wenn dieser, in einem ausgedachten Szenario, auf einem Auto liegen würden und dieses sich mit einer konstanten Geschwindigkeit mit 9,81 m/s in die Richtung der x-Achse bewegt (z-Achse zeigt nach oben).

    (d) Wie würde das Signal aussehen, wenn der Sensor im freien Fall ist(y-Achse zeigt nach unten in Richtung Erde)?

3. Angenommen Sie bestimmte Ihre Körpertemperatur mit einem Sensor, der
Spannungen von 0 − 3.3 V messen kann und einen Messbereich von 0 − 40°C
hat. Ihr Mikrocontroller kann bis zu 5 V und mit einer Auflösung von 10
Bit messen. Welche Temperatur misst der Sensor, wenn der Mikrocontroller
einen Wert von 520 ausgibt? Zeigen Sie Ihre Rechnung! **(1 Punkt)**

4. Wenn Sie den Reset Button betätigen, startet ihr Mikrocontroller den Code neu. Geschieht dies aus der Setup- oder aus der Loop-Funktion? Wenn Sie die elektrische Aktivität Ihres Bizeps messen möchten, in welcher der beiden genannten Funktionen würden Sie Ihren Code hineinschreiben? **(1 Punkt)**

5. Drehen Sie den Beschleunigungssensor in alle 6 Richtungen (jede Achse nach oben und unten zeigend) und messen Sie jeweils 10 Sekunden in jedem Zustand. Prüfen Sie damit, ob jeweils eine Beschleunigung von 1 g angezeigt wird.

    (a) Stellen Sie die Daten in einem Plot dar. **(1 Darstellung, 2 Punkte)**

    (b) Sehen Sie sich die Daten an, wenn der Sensor mit einer Achse nach
unten oder oben zeigt. Ergeben die Daten Sinn? **(1 Paragraph, 2**
**Punkte)**

6. Plotten Sie die gefilterten gegen die ungefilterten Daten des vorherigen Experiments. Beschreiben Sie in ein oder zwei Sätzen, welchen Effekt der Filter erzielt hat und warum Sie diesen Filter verwendet haben. **(1 Darstellung, kurze Antwort, 2 Punkte)**

7. Geben Sie die essenziellen Zeilen des Filter-Algorithmus in Python an. **(Code, 1 Punkt)**

8. Führen Sie folgendes Experiment aus (Nehmen Sie dafür den gegebenen
Arduino Code **Lab1Code1** ): Nehmen Sie den Beschleunigungssensor in
Ihre geschlossene Hand und bewegen Sie ihn sehr schnell pro Sekunde einmal hoch und runter (ohne Rotation). Führen Sie dies für 10 Sekunden aus und speichern Sie die Daten.

    (a) Plotten Sie 4 Sekunden der Daten **(1 Darstellung, 1.5 Punkte)**

    (b) Warum stellen die Daten nicht exakt die durchgeführten Bewegungen dar?

9. Ändern Sie den vorherigen Code so, dass die Aufzeichnungen mit den Bewegungen übereinstimmen, indem Sie das Datenblatt des Sensors konsultieren. Dokumentieren Sie die Seite, auf der Sie die Information über das betreffende Register gefunden haben, sowie den Parameter und alle möglichen Werte, die dieser Parameter annehmen kann. Begründen Sie die Auswahl des verwendeten Wertes. Wiederholen Sie das Experiment. Plotten Sie wieder 4 Sekunden der Daten und vergleichen Sie den Plot mit dem aus der vorhergegangenen Aufgabe. Welche Gemeinsamkeiten und Unterschiede gibt es, und warum bestehen sie? **(1 Darstellung, 1 Paragraph, 2 Punkte)**

10. Nutzen Sie die gesammelten Daten, um die Messfrequenz zu bestimmen
**(Code, 1 Punkt)**

11. Diskutieren Sie die Plateaus der Peaks. Warum sind diese alle beim gleichen Wert? Wie könnte man dieses Problem lösen? **(1 Paragraph,**
**1.5 Punkte)**

12. Ändern Sie den vorherigen Code, um die Plateaus zu beseitigen, indem Sie das Datenblatt des Sensors konsultieren. Dokumentieren Sie die Seite, auf der Sie die Information über das betreffende Register gefunden haben, sowie den Parameter und alle möglichen Werte, die dieser Parameter annehmen kann. Begründen Sie die Auswahl des verwendeten Wertes. Wiederholen Sie das Experiment. Plotten Sie wieder 4 Sekunden der Daten und vergleichen Sie den Plot mit dem aus der vorhergegangenen Aufgabe. Welche Gemeinsamkeiten und Unterschiede gibt es, und warum bestehen sie? **(1 Darstellung, 1 Paragraph, 2 Punkte)**

13. Verwenden Sie das kabellose Messsystem und mit dem DataLogger und der Batterie. Nehmen Sie mit dem Code **Lab1Code2** etwa 10 Sekunden auf (Bewegung ist egal) und vergleichen Sie die Messfrequenz mit dem früheren Wert. Warum sind diese unterschiedlich? **(1 Paragraph, 2 Punkte)**

14. Ihr abgegebener Code funktioniert und erzeugt die richtigen Plots, welche für diesen Bericht gefordert waren. **(1 Punkt)**

**Gesamte Punkte: 24**

## **Abgabe auf Sakai:**
Die Abgabe erfolgt über das Sakai Portal. Verwenden Sie dabei diese Schreibweise (Lab1_*Gruppe_Gruppennummer*) für die Gruppeneinreichung und speichern Sie die folgenden Dateien in dieser *.zip*-Datei:

 -  (optional) Laborbericht als PDF als *Bericht_1_Gruppe_Gruppennummer*

  - **Main Skript der Python Auswertung als *MainCode1.ipynb***

  - Alle Datensätze um *MainCode1* ausführen zu können (z.B. Lab1Frage4)

  - Selbstgeschrieben Python Bibliotheken, welche für *MainCode1* benötigt werden

  - **Bitte alles in eine *.zip* -Datei speichern!!!**


