# **Setup mit Batterieversorgung**

In dieser Aufgabe soll das System mit einer Batterieversorgung betrieben werden.
Da der Mikrocontroller über keine onboard Speichermöglichkeiten verfügt, wird
dafür das OpenLog Modul mit Qwiic Anschluss verwendet. Dieses kann Daten auf
eine MicroSD Karte schreiben und erlaubt somit eine mobile und vom Computer
losgelöste Aufnahme von Daten. Dadurch ergeben sich neue Einsatzgebiete wie
Aufnahmen beim Gehen, Fahrradfahren oder anderen Sportaktivitäten, die zuvor
durch einen stationären Computer limitiert wurden.

1. **OpenLog mit Computer**

(a) Zuerst werden Sie prüfen, ob ihr OpenLog Chip mit der dazugehörigen SD-Karte ordnungsgemäß funktioniert. Dafür wird eine Verbindung mit dem Computer hergestellt und gleichzeitig die Daten auf die SD-Karte geschrieben. Zuerst muss die passende Bibliothek für das
OpenLog Modul installiert werden. Dies findet ähnlich wie in Aufgabe
2.1. über *Sketch →* *Bibliothek einbinden →* *Bibliotheken verwalten...*
*→* Eingabe in Suchzeile: ” *SparkFun Qwiic OpenLog* “ *→* *installieren*
statt.

(b) Wie zuvor schon beim Beschleunigungssensor durchgeführt soll über
***Datei*** *→* ***Beispiele*** *→* ***Beispiele aus eigenen Bibliotheken***
**(ganz unten)** *→* ***SparkFun Qwiic OpenLog*** *→* ***Example1 Writing-***
***Log*** der Beispiel-Code geöffnet und hochgeladen werden.


(c) **Nachdem** der bereits verbundene Mikrocontroller aktiviert wurde soll
die SD-Karte in das OpenLog Modul gesteckt und anschließend mit
einem Qwiic Kabel an den Mikrocontroller angeschlossen werden.

(d) Öffnen Sie den seriellen Monitor und stellen Sie eine Baud-Rate von 9600 ein. Die Ausgabe sollte folgende Zeilen anzeigen:

*OpenLog Write File Test*
*This goes to the terminal*
*Done!*

Trennen Sie danach die Verbindung zwischen Mikrocontroller und OpenLog.

(e) Entnehmen Sie die microSD Karte und verbinden Sie diese mit Ihrem
Computer. Prüfen Sie, ob eine neue .txt-Datei angelegt wurde, welche
den zuvor angegebenen Text enthält.

(f) Öffnen Sie *Example2_AppendFile* . Sie können nun den Namen der zu
speichernden Datei ändern, indem Sie das Argument in den Klammern
von *”myLog.append “* ändern. Jedes mal, wenn diese Zeile aufgerufen
ausgeführt wird, wird auch eine neue Datei erzeugt. Führen Sie anschließend die Punkte (c)-(e) erneut aus.
Versuchen Sie nach dem Anschließen den Reset-Button auf dem Mikrocontroller zu drücken und schauen Sie sich erneut die Text Dateien an.

2. **OpenLog mit Batterie**
Schließen Sie anstelle des Computers jetzt eine Batterie als Stromquelle an
**(Bitte vorher vom USB Kabel trennen!!!)** . Versuchen Sie erneut das
*Example1 und Example2* aus Teil 1 durchzuführen.
**ACHTUNG: Kommentieren Sie davor alle Zeilen aus, welche Daten über den seriellen Anschluss an den Computer senden wie z.B. Serial.begin(9600)(Kommentar = //).**

**ACHTUNG: Fehlerbehebung**

    Die Variante mit Batterie als Stromquelle funktioniert nicht immer
fehlerfrei. Um Fehler zu minimieren soll der Reset-Button nach der

Verbindung mit der 9 V Batterie einmal gedrückt werden. Dies startet
das hochgeladene C-Programm neu.

3. **Beschleunigungsdaten mit OpenLog und Batterieversorgung**
In diesem Teil werden Sie Beschleunigungsdaten im batteriebetriebenen Zustand aufnehmen und auf der SD-Karte speichern. Dafür müssen Sie ihr
Programm vom Computer auf den Mikrocontroller laden, die Verbindung



anschließend trennen, das OpenLog- und Sensor-Modul mit Qwiic Kabeln
verbinden (Reihenfolge egal) und die Batterie anschließen.

**Aufgabe:** Um OpenLog und den Beschleunigungssensor gleichzeitig zu nutzen, müssen Sie den Code der vorherigen Beispiele zusammenfügen. Schreiben Sie ein neues Skript mit dem Namen *MobileAcceleration*, in dem eine
mobile Datenerfassung und Sicherung von Beschleunigungswerten ermöglichen.

**ACHTUNG: Fehlerbehebung**

  - Eine Kontrolle der roten und grünen LED am OpenLog kann helfen:

    - Rot heißt es wird mit Strom versorgt. Blinkt es rot ist keine SDKarte eingelegt oder sie wird nicht erkannt. Das OpenLog Modul
kann eventuell nicht die SD Karte erkennen, wenn diese im Betrieb eingelegt wird. Daher die Stromversorgung unterbrechen und
danach einlegen.

    - Grün heißt es werden Daten auf die SD-Karte geschrieben. Wenn
es sehr schnell blinkt (oder durchgehend) speichert es Daten. Wenn
das Modul mit dem Mikrocontroller verbunden wird und die LED nicht leuchtet, ist etwas nicht funktionsfähig und es muss der Reset-Button gedruckt werden.

  - Wenn die SD-Karte nur wenige Daten aufnimmt, kann dies an einer
falschen Formatierung liegen. Demnach neu formatieren in den erforderlichen Formaten: FAT16 oder FAT32.

   - Sollten Sie die SD-Karte mit dem Mikrocontroller verbunden haben,
während Sie ein neues Programm hochladen, wird nach dem erfolgreichen Upload sofort auf die Karte geschrieben - einfach die Verbindung
trennen, um dies zu vermeiden.

