# Rechnerarchitektur: Übung 2
-----------------------------
> **!!! Diese Übung wurde nicht mit der Korrektur verglichen !!!**
-----------------------------
## Aufgabe 1

### I

**Word Alignment** ist ein Konzept zur Organisation von Daten im Speicher. Hierdurch wird erreicht, dass das Laden von Daten aus dem Speicher zügig verläuft. Prinzipiell ist das Lesen von ungeraden Speicheradressn langsam. Deshalb wir mit Hilfe von Padding-Bytes eine konforme Ordnung zusammenhängender Daten erricht. Dabei wird darauf geachtet, dass die SPeicheradresse von der Wordbreite des Systems teilbar ist (zB. 32-Bit). Einige Prozessoren sind nicht einmal in der Lage von ungerade Speicheradressen zu lesen.

### II

1. Prozessorregister (sehr klein / sehr teuer)
2. Prozessorcache (klein / teuer)
3. Random Access Memory (groß / teuer)
4. Flash / USB
5. HDD
6. Tapes

### III

Ein Computer ist lediglich in der Lage nummerische Werte in binärer Form zu speicher und zu verarbeiten. Zeichenkodierungen sind deshalb dazu da, Bitfolgen in Symbole zu übersetzen. Dabei wird jemden Zeichen ein eindeutiger Zahlenwert zugeordnet. US-ASCII ist ein solcher Standard, der mittels 7-Bit + Parity-Bit Zeichen und Symbole kodiert. Leider können nicht alle Sonderzeichen und Umlaute dargestellt werden, weshalb US-ASCII sich nicht für alle Sprachen dieser Welt eignet.

### IV

UniCode verwendet mehr als ein Byte um durch den erweiterten Wertebereich mehr Zeichen darstellen zu können. Dabei stellt UniCode lediglich das Mapping von Symbolen zu einer erweiterbaren Bitfolge zu Verfügung. Diese definierten Codepoints können dann mit Hilfe verschiedener Kodierungsmechanismen dargestellt werden. Bei UTF-8 werden diese Codepoints variable (1-4 Bytes) dargestellt. Ferner ist es weiterhin kompatibel zu US-ASCII. Die Länge der Zeichen wird mit Hilfe erkennbarer Bitmuster kodiert:

> 1 Byte: 0XXXXXXX
> 2 Byte: 110XXXXX 10XXXXXX
> 3 Byte: 1110XXXX 10XXXXXX 10XXXXXX
> 4 Byte: 11110XXX 10XXXXXX 10XXXXXX 10XXXXXX

## Aufgabe 2

### I

* Verfahren zur Kommunikation zwischen CPU und Peripherie
* I / O Register werden im RAM abgebildet
* Steuerung von Hardware somit über simple Speicheroperationen möglich
* Keine speziellen / hardwarespezifischen Kommandos notwendig
* In die CPU integrierte Mikrocomputer werden normalerweise über Memory-Mapped I / O gesteuert

**Vorteile**:

* Steuerung in Hochsprachen möglich (C / C++)
* Kein Assembler / Maschinencode notwendig

**Nachteil**:

* Adressraum wird belegt
* Adressierbarer Speicher verkleinert sich
* RAM nicht nutzbar



**Alternative:**

* I / O: Portmapped-IO
* Steuerung über I / O - Register der Controller
* Isolierte Adressierung
* Prozessor entscheidet, I / O oder Memory-Mapped
* Spezielle Instruktionen ( IN / OUT )

### II DMA - Direct Memory Access

* Direkte Kommunikation zwischen Peripherie und Speicher
* Normalerweise nicht möglicht: CPU bekommt, speichert zwischen und schreibt Daten in den Speicher
* DMA: Direct-Memory-Access
  * Ermöglicht Peripherie den direkten Zugriff auf den RAM
  * Entlastet somit die CPU: Keine Verschwendung von CPU-Takten
* Spezieller BUS auf dem Motherboard verbindet alle Steckplätze mit Hauptspeicher
* PC hat nur eine DMA-Leitung
* Unterscheidung der Geräte über einen Index

**Funktionsweise:**

1. Sobald ein Gerät mit dem RAM kommunizieren möchte, trennt DMA-Controller die CPU vom BUS-System
2. DMA führt Befehl (READ / WRITE) in 4 Takten aus. Die CPU bräuchte 40 Takte.
3. DMA gibt BUS-System frei und verbindet die CPU erneut.

** Vorteile:**

* Entlastung der CPU
* hohe Geschwindigkeit
* hohe Datenraten

**Nachteil:**

* DMA übernimmt komplette Kontrolle über das BUS-System
* CPU wird also zeitweise von dem BUS abgeschnitten

### III Interrupt Controller

* Polling: Warteschleife um das Ende eines angeforderten Befehls abzuwarten entfällt
* CPU erteilt Befehl und wird bei Beendigung benachrichtigt
* **Multiplexing:** Mehrere I / O-Controller können gleichzeitig einen Interrupt anfordern (Warteschlange)
* **Kaskadierung:** Interrupts unterbrechen sich bei Bedarf gegenseitig (Hirarchie)

**Register:**

* IRR: Interrupt Request Register
  * enthält die Geräte, welche ein Interrupt auslösen möchten
  * 1-Bit pro I / O-Controller
* ISR: Interrupt Service Register
  * zeigt, wessen Interrupt gerade ausgeführt wird
  * 1-Bit pro I / O-Controller
* IMR: Interrupt Mask Register
  * schaltet einzelne Register aus

### IV Interrupt: Verlauf

1. I / O wünscht Interrupt: IRR-Bit wird gesetzt
2. Sobald Möglich wird der Interrupt ausgeführt: Verschieben von IRR in das ISR
3. Interrupt-Controller leitet die Anforderung an die CPU weiter und legt die Interrupt-Nummer auf den BUS
4. CPU holt Interrupt-Nummer und schaut in den Interrupt-Vektor
5. CPU führt Befehl aus und das Bit aus ISR wird wieder entfernt












