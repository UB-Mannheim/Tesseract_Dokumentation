# **Tesseract für Windows**

## **1. Installation der Software**

### **1.1 Download von Tesseract über Windows Installer**  
Die UB Mannheim stellt verschiedene [Tesseract-Installer-Versionen](https://digi.bib.uni-mannheim.de/tesseract/) bereits. Wobei die [Version 5.1](https://digi.bib.uni-mannheim.de/tesseract/tesseract-ocr-w64-setup-v5.1.0.20220510.exe) die aktuellste ist.  
Sie gehen nun wie folgt vor, um Tesseract unter Windows zu installieren:  
-> Datei speichern  
-> Installation ausführen durch Doppelklick oder Rechtsklick und „Ausführen“  
Im Folgenden wird den Anweisungen des Installers gefolgt und entsprechende Einstellungen vorgenommen:  
-> Sprache auswählen  
-> Lizenzvereinbarungen annehmen  
-> Zu installierende Komponenten auswählen: ScrollView; Training Tools; Shortcuts creation, Language data; additional Script und Language data auswählen (für die meisten wahrscheinlich wichtig: Latin Script, Fraktur Script, evtl. Greek Script); additonal Language Data auswählen (für die meisten wahrscheinlich wichtig: German, Latin, English – Middle (1100-1500), evtl. Greek, French, German Fraktur, French – Middle (ca. 1400-1600), Greek Ancient (-1453), Italian, Italian (Old), Spanish, Spanish (old))  
-> Zielverzeichnis, indem das Programm gespeichert werden soll auswählen  
-> Startmenü Ordner für Programmverknüpfungen oder neuen Ordner benennen  
-> Installation fertigstellen  

**Nachträgliches Herunterladen von Standardmodellen:**   
-> Best-Modelle liefern die besten Ergebnisse, jedoch langsamer als Fast Modelle. Empfehlung: Fast Modelle verwenden, da die Best Modelle kaum besser sind, jedoch deutlich langsamer. 
-> Sie können eine [Liste aller verfügbaren Sprachen und Schriften (Standardmodelle)](https://github.com/tesseract-ocr/tessdoc/blob/main/Data-Files-in-different-versions.md) auf Github finden.  

**Die Modelle finden Sie unter den folgenden Links:**  
[**Schriften (Fast-Modelle)**](https://github.com/tesseract-ocr/tessdata_fast/tree/main/script)  
[**Sprachen (Fast-Modelle)**](https://github.com/tesseract-ocr/tessdata_fast)  
[**Schriften (Best-Modelle)**](https://github.com/tesseract-ocr/tessdata_best/tree/main/script)  
[**Sprachen (Best-Modelle)**](https://github.com/tesseract-ocr/tessdata_best)  

**Gehen Sie wie folgt vor:**  
-> Gewünschtes Modell auswählen (Schriften in Ordner Scripts)  
-> Downloaden  
-> Datei aus Downloadordner ausschneiden und unter "C:\Program Files\Tesseract-OCR\tessdata" (kann sich je nach Speicherort unterscheiden)  
  
**Nachträgliches Herunterladen von Spezialmodellen:**  
Für historische Drucke laden Sie die [**Spezialmodelle der UB Mannheim**](https://ub-backup.bib.uni-mannheim.de/~stweil/tesstrain/) herunter.  
- Für Frakturtexte können vor allem die Modelle frak2012 und Gt4HistOCR relevant sein  
-**Gehen Sie wie folgt vor:**  
  -> Gewünschtes Modell auswählen  
  -> tessdata_fast/ auswählen (möglich auch tessdata_best/, jedoch sind Ergebnisse von tessdata_fast/  gleichwertig und die Texterkennung ist deutlich schneller)  
  -> Version auswählen und Datei speichern  
  -> Datei im Downloadordner umbenennen, da jedes mal der exakte Name angegeben werden muss um Modell zu nutzen (es empfiehlt sich z. B. Namen wie frak2021_0.905_1587027_9141630.traineddata in frak2021.traineddata zu kürzen) 
  -> ausschneiden und unter "C:\Program Files\Tesseract-OCR\tessdata" speichern (kann sich je nach Speicherort unterscheiden)

### **1.2 Download von Tesseract Xplore**  
[TesseractXplore](https://github.com/JKamlah/tesseractXplore) ist eine graphische Oberfläche für Tesseract, die die Handhabung deutlich erleichtert, da es ansonsten über die Kommandozeile bedient werden muss. Tesseract Xplore steht auf Github zum [Download](https://github.com/JKamlah/tesseractXplore/#win-cmdexe) zur Verfügung.

-> Datei speichern  
-> TesseractXplore ausführen (evtl. muss Smartscreen deaktiviert werden; Windows Sicherheit -> App-& Browsersteuerung -> Zuverlässigkeitsbasierter Schutz -> Einstellungen -> SmartScreen für Microsoft Edge deaktivieren)  
-> Lizenzabkommen annehmen  
-> Zielverzeichnis, indem das Programm gespeichert werden soll auswählen  
-> Installation fertigstellen  
-> Graphische Oberfläche funktioniert automatisch, wenn Tesseract wie in Punkt 1.1 beschrieben vorher installiert wurde, ansonsten kann es in den Settings unter „Settings“ ->  „Extra Tesseract-Settings“ über Button „Install tesseract“ nachträglich installiert werden  
-> Schriften und Sprachen nachträglich in TesseractXplore installieren; über Spalte „select model“ -> “find a new model“ -> gewünschte Sprache eingeben wie z.B. „Spanish“ und ggf. Filter einstellen (Best oder Fast und Script oder Language) -> „Download“ (funktioniert auch für Spezialmodelle)  

## **2. Anwendung von Tesseract**    
### **2.1 Anwendung von TesseractXplore**   
1. Bilder oder Ordner per Drag & Drop in das Fenster ziehen  
Oder über “Image Selection” die entsprechenden Bilder bzw. Ordner auswählen.   
2. Anschließend die „Tesseract Settings“ einstellen  
- **Select Model:** hier ein geeignetes Model auswählen, welches die besten Ergebnisse für das ausgewählte Dokument erzielt.  
- **Select Page Segmentation:** Je nachdem wie das Layout des Dokumentes beschaffen ist, sollte die Seitensegmentierung eingestellt werden.  
- **Select OCR Engine Mode (OEM):** Wählt aus, mit welcher Methode der Text erkannt werden soll. Die Standardeinstellung sollte in den meisten Fällen beibehalten werden.  
- **Select Output format:** Hier wird ausgewählt in welchem Dateiformat der erkannte Text ausgegeben werden soll. Zur Auswahl stehen **HOCR, ALTO, PDF und TSV**  
  - **HOCR:** Dokument, in dem sich zusätzlich zum Text, auch Layout, Erkennungsgenauigkeit, Formatierungen und andere Infos erfassen lassen
  - **ALTO:** offenes XML Schema zur Beschreibung von Layout-Informationen digitalisierter Objekte  
  - **PDF:** Transkription wird als Textlayer über PDF gelegt  
  - **TSV:** einfache Textdateien, die im Texteditor geöffnet und editiert werden können  
- **Print on Screen:** Wenn diese Funktion eingeschalten ist, wird der erzeugte Text direkt auf dem Bildschirm angezeigt. Dies ist vor allem bei Testläufen sinnvoll.  
- **Select Output Directory:** Hier kann angegeben werden, wo die Zieldatei abgelegt werden soll. Durch die Standardeinstellung wird es im gleichen Ordner wie die Ausgangsdatei abgelegt.  
- **Create Group Folder:** Kann ein eigener Ordner für erkannte Texte angelegt werden, ansonsten werden sie einfach in Ausgangsordner abgelegt. Zudem kann ein Subfolder angelegt werden, wo dann z.B. nach Dateityp getrennt, Dokumente abgelegt werden wie hocr, alto, pdf etc.  
3. Mit einem Rechtsklick auf das hochgeladene Bild, öffnen sich eine Reihe von Optionen. Man kann beispielsweise über „Edit Image“ das Bild bearbeiten. Es können z.B. die Kontraste, Helligkeit oder Neigung des Textes verändert werden. Über „Remove from Selection“ kann das Bild wieder entfernt werden.  
4. Nachdem alle Einstellungen vorgenommen und evtl. die Bilder bearbeitet wurden, kann die Texterkennung über den „Run“-Button gestartet werden.  
5. Wenn man verschiedene Modelle vergleichen möchte kann man den Text jeweils auf dem Bildschirm anzeigen lassen und über den Button „save to stdout“ speichern. Mittels eines Rechtsklick auf das Bild können dann über „Compare stdout“ die Ergebnisse direkt miteinander verglichen werden.  

**Keyboard Shortcuts**   
Das Nutzen von Shortcuts erleichtert die Handhabung von Tesseract Xplore. Die [wichtigsten Shortcuts](https://github.com/JKamlah/tesseractXplore/#gui-usage) finden Sie auch auf Github.  
**Tasten**|**Aktion**|**Bildschirm**  
F1   |Zu den Kivy-Einstellungen wechseln|Alle  
F2   |Zu den App Einstellungen wechseln|Alle  
F5   |Zum Home-Bildschirm wechseln|Alle  
F6   |Zur Modell-Auswahl wechseln|Alle  
F7   |Zur Modell-Suche wechseln	Alle  
F9   |Online bzw. Offline schalten|Alle  
F10  |Randlos schalten|Alle  
F11  |Vollbild anschalten|Alle  
F11  |Darkmode bzw. Lightmode anschalten|Alle  
Strg + S |	Einstellungen speichern|Alle  
Strg + Q |	Verlassen|Alle  
Strg + R |	Tesseract Einstellungen zurücksetzen|Image Selection  
Strg + O |Ausgewählten Bildordner öffnen|Image Selection  
Strg + ‚+‘|Heranzoomen|Image Selection  
Strg + ‚-'|Herauszoomen|Image Selection  
Strg+Enter|Bild-Tagger ausführen|Image Selection  
Strg+Enter|Modelsuche starten|Modellsuche  
Shift+Strg+X|Löscht ausgewählte Bilder|Image Selection  
Shift+Strg+X|Löscht Suchfilter|Modellsuche  

## **2.2 Anwendung von Tesseract über die Kommandozeile**  
Beispiel für Windows Pfad: "C:\Users\Larissa\Documents\Tesseract_Test"  
-> Nun öffnen Sie die Tesseract-OCR-Console:  
-> Am einfachsten ist die Anwendung, wenn man angibt, dass man die Outputdatei dort ablegt, wo sich die Inputdatei befindet:  
-> Befehl: 
```
$ cd <“Pfad“>  
```
-> Beispiel:  
```
$ cd "\Users\muster\Documents\\Beispielbilder_OCR"
```
-> Befehl zur Transkription:  
```
$ tesseract <Name der Inputdatei> <Name der Outputdatei> -l <Modell> <gewünschte Formate wie pdf txt; mehrere durch Leerzeichen trennen>  
```
-> es können auch weitere Parameter spezifiert werden:  
```
$ tesseract <Name der Inputdatei> <Name der Outputdatei> -l <Modell> --<oem ocrenginemode> --<psm pagesegmode> [Outputformate]
```
-> Beispiel:  
```
$ tesseract img01.jpg ocrimg01 -l frak2021 pdf txt alto
```

Andere Möglichkeit, bei der Input- und Outputordner genau definiert werden:  
```
tesseract < “Pfad zur Inputdatei“> <“Pfad zur Outputdatei“> <Sprache/Script> <gewünschte Outputformate>
```
Beispiel:
```
$ tesseract  "C:\Users\muster\Documents\Beispielbilder OCR\bsb-demo.jpg" c:\temp\bsb-demo-ocr -l frak2021 txt
```
**Hinweis:** Es können mehrere Modelle verwendet werden, wenn diese durch ein „+“ miteinander verbunden werden.  

## **3. Voraussetzungen für erfolgreiche Texterkennung**  
- Neigung, Farbigkeit, Kontrast, Layout und Schriftart des Originaldokumentes, Auflösung und Qualität der Bilddatei  
- Unterstützt werden folgende Formate: BMP, PNM, PNG, JFIF, JPEG, and TIFF.  
- Verwendung eines passenden Modells, v.a. bei Fraktur empfehlen sich die Spezialmodelle der UB Mannheim  
- Für bestmögliche Ergebnisse müssen einige Voraussetzungen erfüllt werden: gute Auflösung der Vorlagen (300-400dpi); Bereinigung von Flecken etc., Begradigung; Text darf nicht „um die Ecke gehen“ bzw. im Falz verschwinden; Kontrastverschärfung; keine Binarisierung   

### **3.1 Hilfsprogramme**   
- [**Scantailor:**](https://scantailor.org/) Bearbeitung von Scans: u.a. Seiten aufgeteilt, begradigt, Entfernung unerwünschter Ränder, Bearbeitung automatisiert, aber auch manuell  
- [**Unpaper:**](https://github.com/unpaper/unpaper) Kommandozeilenprogramm für Nachbearbeitung von Scans und Bildern; gut für automatische Stapelverarbeitung von großen Datenmengen, Vorbereitung von Texterkennung, Digitalisierung, Konservierung und Archivierung von Scans  
- [**Convert:**](https://imagemagick.org/index.php) Teil der Softwaresammlung ImageMagick; Verbesserung von Scans  
- [**ExactImage:**](https://exactcode.com/opensource/exactimage/) Sammlung von Kommandozeilen-Werkzeugen zur Bearbeitung von Grafik-Dateien; hohe Bearbeitungsgeschwindigkeit, für schwache Rechner geeignet  
- [**Meld:**](https://meldmerge.org/) bietet die Möglichkeit verschiedene Transkriptionen miteinander zu vergleichen  

## **4. Häufige Fehler, die zu schlechten Ergebnissen führen**
- Verwendung ungeeigneter Modelle
- zu schlechte Bildqualität der Inputdatei
- andere Probleme mit Scan wie schwache Kontraste, Wellenbewegung des Textes im Falz etc., schiefer Text, Tabellen, Vorkommen verschiedener Schriftarten

