# Tesseract für Linux

## 1. Installation der Software

### 1.1 Eventuell: **Windows Subsystem for Linux (WSL)** installieren:
**Alternative 1:** Sie können Debian oder Ubuntu einfach als App im Windows Store herunterladen.
**Alternative 2:*Oder Sie laden es über die Kommandozeile herunter:  
-> PowerShell aufrufen und eingeben (ggf. als Administrator ausführen): 
```
$ wsl --install
```
-> Standardmäßig wird nun Ubuntu installiert; wenn eine andere Version installiert werden soll: 

```
$ wsl --install -d <Distribution Name> #(Distribution Name = Name der Linux Distribution)
```
Alle verfügbaren Linux-Distributionen anzeigen:
```
$ wsl --list --online oder wsl -l -o 
```
Nach der Installation befolgen Sie diese Schritte:  
-> PC neustarten  
-> Nach WSL suchen und ausführen  
-> Gewünschten Benutzername und Passwort anlegen  
-> Updaten über die Befehle:  
```
$ sudo apt update
$ Sudo apt ugrade
```

### 1.2 Falls das Endgerät sowieso Linux nutzt, kann Punkt 1.1 übersprungen werden
 **Installation von Tesseract**  
-> In Linux-Kommandozeile eingeben:  
```
$sudo apt install tesseract-ocr
```
-> Das Programm fragt nun, ob man benötigten Speicherplatz verwenden möchte (After this operation, 30.2 MB of additional disk space will be used. Do you want to continue? [Y/n]
-> Mit Enter bestätigen 
-> Anschließend können die benötigten Sprachen via Link heruntergeladen werden:
```
wget <Link>
```
Beispiel:  
```
wget https://github.com/tesseract-ocr/tessdata_fast/raw/main/deu.traineddata
```
Um den richtigen Link zu erhalten, klicken Sie die gewünschte Sprache in Github an und machen dann einen Rechtsklick auf „View Raw“ oder „Download“ und wählen die Option „Link-Adresse kopieren“ aus.  
Eine Liste aller verfügbaren Sprachen und Schriften (Standardmodelle) findet man unter: https://github.com/tesseract-ocr/tessdoc/blob/main/Data-Files-in-different-versions.md
**Schriften (Fast-Modelle):** https://github.com/tesseract-ocr/tessdata_fast/tree/main/script
**Sprachen (Fast-Modelle):** https://github.com/tesseract-ocr/tessdata_fast
**Schriften (Best-Modelle):** https://github.com/tesseract-ocr/tessdata_best/tree/main/script
**Sprachen (Best-Modelle):** https://github.com/tesseract-ocr/tessdata_best
Die **Spezialmodelle der UB Mannheim** finden Sie unter folgendem Link: https://ub-backup.bib.uni-mannheim.de/~stweil/tesstrain/
-> Alle gewünschten Sprachen und Schriften können jederzeit mit dem obigen Befehl heruntergeladen werden.
-> vorhandene Sprachen können auch in der Kommandozeile über den Befehl gefunden werden:  
```
apt search tesseract- lang
```
-> für vorhandene Schriften funktioniert folgender Link: 
```
apt search tesseract- script
```
-> Damit die heruntergeladenen Modelle auch im richtigen Ordner abgelegt werden, kann über folgenden Befehl herausgefunden werden, wo die Modelle liegen:  
```
$ tesseract -l XXX XXX XXX
```
Anschließend kann der Pfad kopiert werden und dorthin gewechselt werden:  
```
$ cd <Pfad>
```
Beispiel: 
```
$ cd /usr/share/tesseract-ocr/4.00/tessdata/
```
Nachdem das entsprechende Modell heruntergeladen wurde, kann nun noch der Name des Modells geändert werden. Dies ist vor allem bei Sondermodellen nützlich, da diese oft lange Versionsnamen haben.  
```
$ sudo mv <alter Name> <neuer Name>
```
Beispiel:  
```
$ sudo mv GT4HistOCR_0.705_440562_2193500.traineddata GT4HistOCR.traineddata
```
Alternativ können auch in WSL, die Dateien innerhalb der Windows-Benutzeroberfläche abgelegt werden: 
Geben Sie dafür in den Begriff „\\wsl$“ als Pfad in den Explorer ein. Anschließend werden Ihnen alle vorhandenen Linux-Distributionen angezeigt. Sowohl unter Ubuntu als auch unter Debian lautet der standardmäßige Pfad zum Tessdata-Ordner, indem Modelle abgelegt werden: \\wsl$\Debian\usr\share\tesseract-ocr\4.00\tessdata.  
Nun wählen Sie auf Github das gewünschte Schrift- oder Sprachmodell aus und klicken anschließend entweder auf „View Raw“ oder „Download“ und laden das Modell herunter. Jetzt können Sie es aus dem Download-Ordner ausschneiden und in den Tessdata-Ordner einfügen. Auch hier sollten Sie bei den Spezialmodellen der UB auf eine handliche Umbenennung setzen.
Welches Modell soll ich auswählen?
- Sprachmodelle wurden in der Vergangenheit gerne eingesetzt für OCR, jedoch ist die OCR damit häufig lückenhaft, da in einem deutschen Text auch französische oder italienische Wörter vorkommen können. Ihnen liegt meist auch ein Wörterbuch zugrunde, mit dem Ergebnisse automatisch abgeglichen werden.  
- Aufgrund dessen wurden Schriftmodelle trainiert, da ein Modell für lateinische Schrift auch jedes Wort in lateinischer Schrift lesen kann egal in welcher Sprache.  
- Die Spezialmodelle erkennen weitere Besonderheiten und so erzielt man mit ihnen häufig das beste Ergebnis.  
- Empfehlung: wenn man einen modernen deutschen Text erkennen möchte, sollte man als Schriftmodell Latin auswählen, wenn man aber ältere Texte erkennen möchte, dann sollte man auf die Sondermodelle wie frak2021 und GT4HistOCR zurückgreifen.  

## 2. Anwendung von Tesseract
### 2.1 Verarbeitung einzelner Bilder
- Zunächst Pfad angeben: dazu einfach im Fenster, in welchem die Dateien abliegen: SHIFT+Rechtsklick  „Hier Linux-Shell öffnen“ 
- Oder Pfad händisch eingeben, aber Achtung Pfade werden in Linux anders angegeben als unter Windows:
Beispiel für Windows Pfad: C:\Users\Larissa\Documents\Tesseract Test
Entsprechende Benennung in Linux: Linux: /mnt/c/Users/Larissa/Documents/Tesseract Test
- Eingabe in Linux-Konsole :
```
$ cd “/mnt/c/Users/Larissa/Documents/Tesseract Test” 
```
-> Enter
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

### 2.2 Verarbeitung mehrerer Bilder  
Hierfür gibt es drei Optionen:  
Für alle Optionen zuerst im Ordner der zu verarbeitenden Bild durch Shift+Rechtsklick ein Linux-Fenster öffnen, dadurch wird Pfad automatisch eingefügt.  
Durch folgenden Befehl, kann angezeigt werden, welche Bilder das Programm findet:  
```
$ find -name \*.<Bilddateientyp z.B. jpg oder png> 
```
Beispiel:  
```
$ find -name \*.jpg
```
1. Option über find: 
```
$ find -name \*.<Bilddateientyp> | while read f; do tesseract -l <Modell> $f ${f%.<Bilddateientyp> }<evtl. Ausgabedatei>; done
```
-> erstellt automatisch Textdateien, ansonsten muss vor Semikolon andere Ausgabedatei geschrieben werden
Beispiel:  
```
lwill@ubnote13:/mnt/c/Users/lwill/Documents/Larissa Will/OCR Tests/Test_Stapelverarbeitung$ find -name \*.jpg | while read f; do tesseract -l deu $f ${f%.jpg}; done
```
2. Option zur parallelen Verabeitung: 
```
$ find -name \*.<Bilddateientyp> -maxdepth 1 | parallel -j 4 --progress 'tesseract {} {.} -l <Modell> <eventuell Ausgabedatei>'
```
Beispiel:
```
lwill@ubnote13:/mnt/c/Users/lwill/Documents/Larissa Will/OCR Tests/Test_Stapelverarbeitung$ find -name \*.jpg -maxdepth 1 | parallel -j 4 --progress 'tesseract {} {.} -l deu pdf'
```
3. Option über fd-find (hierfür muss zunächst fd-find installiert werden): 
```
$ apt-get install fd-find
```
Anschließend: 
```
$ fdfind -e <Bilddateientyp> -d 1 --exec tesseract -l <Modell> {} {.} <evtl. Ausgabedatei>
```
Beispiel:  
```
lwill@ubnote13:/mnt/c/Users/lwill/Documents/Larissa Will/OCR Tests/Test_Stapelverarbeitung$ fdfind -e jpg -d 1 --exec tesseract -l deu {} {.} hocr
```
Auch hier sollten Sie bei den Spezialmodellen der UB auf eine handliche Umbenennung setzen.
 
