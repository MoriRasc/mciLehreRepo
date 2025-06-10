# **Verarbeitung und Darstellung**

Für diese Aufgabe wird Python zur Auswertung der aufgenommenen Daten verwendet. Es dürfen sowohl VS Code als auch Jupiter Notebooks zum Lösen der
Aufgabe verwendet werden. Aufgrund der einfachen Zugänglichkeit, werden die
Skripte vom Lehrenden über Jupiter Notebooks zur Verfügung gestellt, um erste
praktische Erfahrungen mit der digitalen Signalverarbeitung zu machen. Das Python Script ist auf SAKAI unter dem Ordner **Ressourcen/Praktikum/Praktikum 1/P1 Visualisierung Messdaten.ipynb** zu finden.

1. **Einrichtung der Umgebung**
Da bereits VS Code und Jupiter Notebooks im ersten und zweiten Semester verwendet wurden, wird der Installationsprozess nicht erneut beschrieben.
Wenn ab diesem Zeitpunkt der Begriff Python verwendet wird, ist damit
immer das Post-Processing der aufgenommenen Daten gemeint und findet
nicht in der Arduino Umgebung statt.

2. **Importieren der Daten**
Die Daten werden entweder über die SD-Karte direkt gespeichert oder aus
dem seriellen Monitor herauskopiert (dafür immer erst den Mikrocontroller
vom PC trennen, um die Daten¨ubertragung zu stoppen).
**Aufgabe:** Lesen Sie die Daten in ihrer Python Umgebung in einen **Pandas**
**Dataframe** ein.

3. **Verarbeitung und Darstellung**
Für das Filtern der Daten sind verschiedene Bibliotheken in Python notwendig. F¨ur diesen Teil werden folgende Bibliotheken benötigt:

   - pandas
    - matplotlib.pyplot
    - numpy
    - scipy.signal (Signalfilterung)

Für die Filterung der Beschleunigungsdaten können sie einen *butterworth*
*filter* der 4. Ordnung als Tiefpassfilterung verwendenden. Testen Sie die
Möglichkeiten dieses Filters, indem Sie die Grenzfrequenz als Argument in
der Filterfunktion ändern. Der Filter könnte dann wie folgt aussehen:

````java
b,a = scipy.signal.butter(4, Grenzfrequenz, ’ low ’)

filtered_data = scipy.signal.filtfilt(b, a, data)
````

**ACHTUNG: Fehlerbehebung**

  - Wenn Sie eine Testmessung vornehmen und dabei den Reset-Button
drücken, führt dies zu einem erneuten Start des Zeit-Counters. Sie
können die Zeit bis zum Neustart danach händisch in der Textdatei löschen.



  - **Bitte alles in eine** ***.zip*** **-Datei speichern!!!**


