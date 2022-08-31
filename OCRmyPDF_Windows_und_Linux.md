# OCRmyPDF für Windows und Linux

Die besten OCR-Ergebnisse lassen sich prinzipiell erzielen, wenn die Ausgangsdatei in Bildformaten wie .jpeg, .tiff oder .png vorliegen, jedoch liegen die Dokumente gelegentlich nur in .pdf-Format vor. 
Dann empfiehlt es sich das Programm [OCRmyPDF](https://ocrmypdf.readthedocs.io/en/latest/index.html) zu verwenden. Das Programm nutzt zur Texterkennung [Tesseract](https://tesseract-ocr.github.io/tessdoc/), hierbei wird aktuell Version 4.xx benötigt. Zur Nutzung von OCRmyPDF müssen Sie also zuvor Tesseract und ihre gewünschten Modelle installiert haben. Wir stellen zudem eine Anleitung zur Installation von [Tesseract unter Linux](https://github.com/UB-Mannheim/Tesseract_Dokumentation/blob/main/Tesseract_Doku_Linux.md) und [Tesseract unter Windows](https://github.com/UB-Mannheim/Tesseract_Dokumentation/blob/main/Tesseract_Doku_Windows.md) bereit. 
Im Folgenden wird die Installation und Nutzung von OCRmyPDF unter Ubuntu 20.04 im *Windows Subsystem for Linux* beschrieben. Falls Sie Windows nutzen, können Sie WSL ganz einfach über den Microsoft Store herunterladen.

## 1. Installation:  

### 1.1 Ubuntu upgraden
Zunächst empfiehlt es sich immer Ubuntu auf den neusten Stand zu bringen:  
```
$ sudo apt update
$ sudo apt upgrade
```
### 1.2 Herunterladen von zusätzlichen Programmen  
Zur Nutzung von OCRmyPDF werden folgende Programme benötigt: Imagemagick, parallel, ghostscript qpdf, unpaper und tesseract-ocr. Mit folgendem Befehl können diese installiert werden:  
```
$ sudo apt-get install imagemagick parallel ghostscript qpdf unpaper tesseract-ocr
```
### 1.3 Download von OCRmyPDF  
Um mit einer aktuellen Version von OCRmyPDF arbeiten zu können, sollten Sie diese ebenfalls herunterladen:  
```
$ sudo apt-get install ocrmypdf
```
### 1.4 Installation des JBIG-Encoders
Zudem sollte der JBIG-Encoder installiert werden, da sonst die ausgegeben PDF-Dateien sehr groß werden. Dafür geben Sie folgende Befehle in die Kommandozeile ein:  
```
$ git clone https://github.com/agl/jbig2enc
$ cd jbig2enc
$ sudo apt install automake
$ sudo apt install libtool
$ ./autogen.sh
$ sudo apt install libleptonica-dev
$ ./configure && make
$ [sudo] make install
``` 
## 2. Nutzung:
**Wissenswertes:** Ein Fenster, das Ihnen Hilfestellungen bietet, öffnen Sie mit folgender Eingabe:  
```
$ ocrmypdf --help
```
### 2.1 Duchführung der Texterkennung
Um eine Texterkennung durchzuführen, begeben Sie sich in den Ordnern indem die PDF-Dateien liegen und öffnen dort mittels SHIFT und Rechtsklick eine Linux-Shell. Alternativ müssen Sie dem Programm den Pfad zur Datei nennen. Dann geben sie folgenden Befehl ein:  
```
$ ocrmypdf <input.pdf> <output.pdf>
```
**Beispiel:**    
```
$ ocrmypdf Beispiel.pdf Beispiel-OCR.pdf
```
Standardmäßig nutzt OCRmyPDF das Modell für englische Sprache, wenn Sie ein anderes Modell nutzen möchten, dann müssen Sie den Befehl anpassen:  
```
$ ocrmypdf -l <Modell-Name> <input.pdf> <output.pdf>
```
**Beispiel:**  
```
$ ocrmypdf -l frak2021 Beispiel.pdf Beispiel-OCR.pdf
```
Wenn Sie mehrere Modelle miteinander kombinieren möchten, können Sie diese so miteinander verbinden:  
```
$ ocrmypdf -l <Modell1+Modell2> <input.pdf> <output.pdf>
```
**Beispiel:**    
```
$ ocrmypdf -l frak2021+eng Beispiel.pdf Beispiel-OCR.pdf
```
### 2.2 Zusätzliche Ausgabedateien:
Wenn Sie zusätzlich zu Ihrem Ausgabe-PDF, die OCR noch in Form einer Textdatei möchten, dann geben Sie folgenden Befehl ein:
```
$ ocrmypdf --sidecar <output.txt> -l <Modell> <input.pdf> <output.pdf>
```
**Beispiel:**    
```
$ ocrmypdf --sidecar Beispiel-OCR.txt -l frak2021 Beispiel.pdf Beispiel-OCR.pdf
```
Sollte Ihre PDF-Datei bereits eine Textebene haben, deren Qualität z.B. nicht ausreichend ist, können Sie das Programm zwingen trotzdem eine OCR durchzuführen:  
```
$ ocrmypdf --force-ocr -l <Modell> <input.pdf> <output.pdf>
```
**Beispiel:**    
```
$ ocrmypdf --force-ocr -l frak2021 Beispiel1.pdf Beispiel-OCR.pdf
```
Mit zusätzlicher Erzeugung einer Textdatei, kann die Reihenfolge dazu so aussehen:  
```
$ ocrmypdf --sidecar output.txt --force-ocr -l <Modelll> <input.pdf> <output.pdf>
```
Bei dieser Dokumentation werden nur die aus unserer Sicht wichtigsten Punkte zusammengefasst. Falls Sie eine weitergehende Anleitung benötigen, finden Sie diese auf der Seite von [OCRmyPDF](https://ocrmypdf.readthedocs.io/en/latest/cookbook.html#cookbook) direkt.

