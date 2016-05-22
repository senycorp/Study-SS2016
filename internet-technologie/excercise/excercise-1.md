# IT&WE: Übung 1

**Name**
Selcuk kekec           

**Matrikelnummer**
3025670

-------------------

## Aufgabe 1

### I

> UTF-8 verwendet dazu bestimmte Byte-Reihenfolgen um zu signalisieren, aus wie vielen Bytes ein Zeichen besteht. Allgemein kann gesagt werden, dass wenn das Bit an der höchsten Stelle "0" ist, das Zeichen aus lediglich einem Byte besteht. Andernfalls ist von einem Zeichen auszugehen, dass 2 bis 4 Bytes beansprucht.

1 Byte: 0XXXXXXX
2 Bytes: 110XXXXX 10XXXXXX
3 Bytes: 1110XXXX 10XXXXXX 10XXXXXX
4 Bytes: 11110XXX 10XXXXXX 10XXXXXX 10XXXXXX

### II

&#228; - 0xC3 0xA4	
&#174; - 0xC2 0xAE	
&#169; - 0xC2 0xA9	
&#163; - 0xC2 0xA3	
&#86; -  0x56

### III

> &#1811;   (U+0713): Syrischer Buchstabe Gamal
> &#9760;   (U+2620): Skull and crossbones
> &#10004; (U+2714): Heavy check mark
> &#12785; (U+31F1): Katakana letter small si

### IV

Die verschiedenen UTF-Kodierungen unterscheidenen sich in folgenden Aspekten:

* Speichernutzung (Variabel oder Fixed)
* Rückwärtskompatibilität zu ASCII
* Byte Order

UTF-8 kodiert Zeichen beispielsweise variabel (1-4 Bytes) genau wie UTF-16 (2-4 Bytes) auch. UTF-32 nutzt hingegen eine fixe Länge von 4 Bytes für jedes Zeichen, dass zu einem hohen Grad an Speicherverschwendung führt. Die fixe Länge macht jedoch eine algorthmische Verarbeitung obsolet, sodass UTF-32 zwar Speicher verschwendet dafür aber sehr performant ist. Leider ist UTF-32 nicht kompatibel zu ASCII, UTF-8 und UTF-16 jedoch schon. 

Bei der Byte Order ist UTF-8 zu vernachlässigen, da die Byte Order keinen Unterschied für UTF-8 bedeutet, dass eine Code-Unit-Size von 8-Bits hat. Im Gegensatz dazu verhahlten sich UTF-16 und UTF-32 variabel und erlauben die Angabe der Byte Order über den sogenannten "Byte Order Mark", welcher unmittelbar am Anfang genannt werden muss.

> UTF-8 und UTF-32 sind Kodierungsmechanismen, die Unicode in eine eindeutige Bytefolge übersetzen. Dazu nutzen beide verschiedene Ansätze. Es gibt jedoch keine UTF-32-spezifischen Zeichen, welche von UTF-8 nicht unterstützt werden könnten. Beide arbeiten auf Grundlage von UniCode und sind in der Lage alle Zeichen darzustellen. UTF-8 kann maximal 4 Bytes für die Kodierung verwenden, wobei 21 Bits davon für die Kodierung der Zeichen verwendet werden kann und 11 Bits für das Erkennungsschema von 4 Byte-Zeichen beansprucht werden. Dabei ergeben sich 2^21 Kombinationen. UTF-32 hingegen nutzt das volle Spektrum

### V

UTF-32 verspricht durch die Verwendung von fixen Längen zwar konstante Zugriffszeiten, verschwendet dafür aber jedoch viel Speicher und ist zudem nicht kompatibel zu ASCII.

## Aufgabe 2

### I

(12245589) = (0) 0000 | (0) 0000 | (B) 1011 | (A) 1010 | (D) 1101 | (A) 1010 | (5) 0101 | (5) 0101

| Speicher | Big-Endian | Little-Endian |
|:--------:|:----------:|:-------------:|
|    b0    |     BA     |       00      |
|    b1    |     DA     |       55      |
|    b2    |     55     |       DA      |
|    b3    |     00     |       BA      |


### II

Wenn Alice die Zahl korrekt in network byte order verschickt muss das Betriebssystem sicherstellen, dass eine Umwandlung in Little-Endian durchgeführt wird, bevor es weiter an Bob gereicht wird. Viele Standards und Spezifikationen in Form von RFCs zu Protokollen legen bereits einen Byte-Order fest, der eingehalten werden muss.


### III

Da beide Kodierungen Zeichen als Single-Byte kodieren spielt es hier keine Rolle. Das erste Zeichen eines Strings wird immer an der kleinsten Speicheradresse gespeichert:

Als Beispiel wäre bei dem String "Hallo Welt" an der niedrigsten Speicheradresse der Buchstabe "H" als Byte abgelegt. Beide Interpretationsformen würden hier zu keinem Fehler führen und der abgelegte Text würde korrekt ausgelesen werden können. Auch würde ein bitweiser Vergleich zweier Strings funktionieren.




> Written with [StackEdit](https://stackedit.io/).