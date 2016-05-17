# Internet-Technologie & Web Engineering

## Einführung

### ISO / OSI Network Model

* 7 Ebenene
* Sender: Jede Ebene fügt Protocol Data Unit hinzu
* Receiver: Jede Ebene extrahiert notwendige PDU und führt Aktionen aus

![Auflösung der PDU in OSI](https://lh3.googleusercontent.com/-veQ4RwG218g/VzLy9KHeewI/AAAAAAAAO1U/_6snEfrBI1Ijm2P5kLcaXbdRtDS0wC5xQCKgB/s0/Auswahl_012.png "Auswahl_012.png")


### Vergleich: OSI vs. TCP/IP

![enter image description here](https://lh3.googleusercontent.com/-5-gqFZMX9gY/VzLzkY_FQUI/AAAAAAAAO1o/7hNtfrJlrzED0XNUw460ELVjMI08qcZHwCKgB/s0/Auswahl_013.png "Auswahl_013.png")

### Layer

#### Internet / Network Layer

* Datenübertragung zwischen System
* Protokolle: IPv4 / IPv6
* Dateneinheit: packets
* Notwendige Aufgaben
  * Routing: 
     * Bester Weg zum adressierten System durch das Netzwerk
     * Merken der Netzwerkstruktur bei Fehlern
  * Fragmentierung
     * Zerlegung großer Pakete in mehrere kleinere
     * MTU bestimmt zulässige packet size
  * Congestion Control
     * Handle overloaded network links
     * Packet loss: Sende ECN, damit eine andere Ebene das Paket erneut schicken kann

#### Transport Layer

* Datenübertragung zwischen Prozessen
* Protokolle: TCP, UDP
* TCP: segment , UDP: datagram
* Adresses over ports

##### TCP

* Connection-oriented
  *  Verbindungsaufbau (3-Way-Handshake)
  * Beenden der Verbindung
* Verarbeitung von Netzwerkfehlern
  * Pakete werden sicher zugestellt
  * Acknowledgement (Paket wurde zugestellt)
  * retransmission (Paket ist nicht angekommen und wird erneut gesendet)
  * reordering (Reihenfolge der Pakete wird korrigiert)

##### UDP

* Connectionless
  * TODO
  * Effizient durch wenig Overhead an Header / Funktionalität
* Unzuverlässig
  * Checksum-Check
  * Keine Retransmission
* Einsatz in low latency Applikationen
  * App muss Error-Handling übernehmen

#### Application Layer

* Übertragung von Daten für Applikationen
  * Web (HTTP)
  * E-Mail (SMTP) 
* Applikationsspezifisch
  * Protokoll
  * Dateneinheit
  * Adressierung und Aufgaben


#### Network Protocol

* Interoperabilität
* Definiert Regeln für die Kommunikation
  * Kommunikation
  * Syntax der Nachrichten
  * Semantik der Nachrichten
* Standardisierung und Definition durch IETF
  * RFC (Request for Comments)
  * STD (Internet Standard)


## Sockets

> Sockets bilden eine plattformunabhängige, standardisierte Schnittstelle (API) zwischen der Netzwerkprotokoll-Implementierung des Betriebssystems und der eigentlichen Anwendungssoftware. Ein Computerprogramm fordert einen Socket vom Betriebssystem an. Das Betriebssystem hat die Aufgabe, alle benutzten Sockets sowie die zugehörigen Verbindungsinformationen zu verwalten. (Wikipedia: https://de.wikipedia.org/wiki/Socket_(Software))

![enter image description here](https://lh3.googleusercontent.com/-gM7_2_-p4i0/VzMQVnXV08I/AAAAAAAAO2E/dZT4eB0TtdQBY442pdox4b2QjDuwbJfFwCKgB/s0/Auswahl_014.png "Auswahl_014.png")

* Schnittstelle zwischen Netzwerkprotokollen und Anwendungen, die über das Netzwerk kommunizieren möchten
* TCP/IP hat keine network API Definition
  * Sockets, TLI, XTI, Winsock, MacTCP
* Sockets: Standard Network API
  *  Verhalten sich wie UNIX Dateien (open, read, write, close)
  * Verschiedene Varianten der Socket API sind verfügbar für alle OS und Programmiersprachen

### Kommunikation

![enter image description here](https://lh3.googleusercontent.com/93S9Q2gQahVaVF5rt85KS0AhQ4TbdOD6C6tP00eDk9pyJYA_4RT2HzLLfGu3FFy-KZ9XaSus=s0 "Auswahl_015.png")

* Applikation schreibt und liest aus dem Socket
* Socket: Communication Endpoint
* Zwei Sockets sind unmittelbar mit einander verbunden, Kein Broker

> Unterstützt:
> IPv4 / IPv6
> TCP / UDP
> Client (Connecting socket) / Server (Listening Socket)

### Funktionalitäten von Sockets

* Erstellen und Löschen
* Auswahl des Protokolls
* Bestimmung: Kommunikationsendpunkt (Local / Remote)
* Senden / Empfangen von Daten
* Error-Notifications
* Protokoll via Socket-Optionen konfigurierbar

### Stream-oriented Communication (TCP)

![enter image description here](https://lh3.googleusercontent.com/--Mfdr7aLU_c/VzMTZzEkAfI/AAAAAAAAO20/EDDO0qWkpIoue9rGbwQg2A4xwlSDW9dEQCKgB/s0/Auswahl_016.png "Auswahl_016.png")

### Datagram-Oriented Communication!

![enter image description here](https://lh3.googleusercontent.com/-meMr2GSsAnE/VzMT1I3fICI/AAAAAAAAO3E/aHP8HGuet5gHVAslHlFHJ77RebuIlekoQCKgB/s0/Auswahl_017.png "Auswahl_017.png")

### Usage

> Folien 11 - 20

### Stateless vs. Stateful

* Stateless Server(Simple for Server)
  * Es gibt keine Status für Clients (waiting, busy, not available)
  * Alle notwendigen Informationen werden sind im Request enthalten
* Stateful Server (Simple for Clients)
  * TODO

### Input / Output Models

* **Blocking I/O**: read() blockiert bis Daten verfügbar sind
* **Multi-Threading**: Jeder Client bekommt seinen eigenen Thread
  * Nicht skallierbar für große Anzahl von Clients (stack memory per stack)
  * **Non-blocking I/O**: read() gibt EWOULDBLOCK zurück solange keine Daten vorliegen
  * **Asyncronous I/O**: Callback als read()-Parameter
     * Daten werden Event-gesteuert verarbeitet
     * Schwieriege Programmierung von Stateful Server
  * **I/O multiplexing**: TODO

### Verarbeitung

#### Sequential Processing

Ein Prozess/Thread für alle Client-Requests:

![enter image description here](https://lh3.googleusercontent.com/-oQBTqFEB3UU/VzMtnC3L4pI/AAAAAAAAO3k/o2XbtfmQU1IiWKUzYtqnWi5lCc-CH2ruwCKgB/s0/Auswahl_018.png "Auswahl_018.png")

#### Parallel Processing

* STREAM-ORIENTED: Neuer Thread für jede Connection
* STREAM-ORIENTED: Gleichzeitige Verarbeitung von Requests in separaten Threads 
* DATAGRAM-ORIENTED: Verwaltung in Thread-Pools

![enter image description here](https://lh3.googleusercontent.com/-uxqus_UhnOs/VzMuSmNAR4I/AAAAAAAAO34/fe0DycEeO283JlbzcsUGq1zC49j_jHJJACKgB/s0/Auswahl_019.png "Auswahl_019.png")

![enter image description here](https://lh3.googleusercontent.com/-M_orkd9wo_8/VzMu9MS0tWI/AAAAAAAAO4M/aAiMhGcHj_YHs__YWHtYgTjPrK7e3IhYACKgB/s0/Auswahl_020.png "Auswahl_020.png")

### Fazit
* Sockets sind eine API für den Transportlayer
* Unix I/O Prinzip: "Everything is a file"
* Übetragung von bytes
* Keine Serialisierung
* Schwierige Programmierung

## Data Representation

* Netzwerk überträgt lediglich bytes
* Daten können alles mögliche representieren
* **Heterogeneity**: Data representation ist Plattformabhängig
* **Transformation**: Überführung in andere Datenformate notwendig -> Schwierig
  *  Pair-wise transformation
      * Mehr Code
      * Bessere Performanz
      * Verarbeitung durch Empfänger, deshalb muss er alle Formate verstehen
  * Canonical representation
    * Weniger Code
    * Schlechtere Performanz
    * Externe Repräsentation

### Byte Order (Endianness)

> Most systems: little-endian
> Most network protocolls: big-endian

![enter image description here](https://lh3.googleusercontent.com/eX2W7PE-4IX6Ieg51DcJJOS0iwYP8Jw_2GnhowyBpbk4ae-jYZoJeF0jTv79ShJcLTK99lIh=s0 "Auswahl_021.png")

![enter image description here](https://lh3.googleusercontent.com/4VBh6ggph30OmPplnCyd4lRxmNEJK47SqPtvppCK6R2sl5Y-XkCcbbGCRR_18fvNPKe-eeMM=s0 "Auswahl_022.png")

### Text Encoding

* Charakter werden als bytes repräsentiert
* Verschiedene Character sets (US-ASCII, ISO, UniCode)

#### US-ASCI 
* 7 bits
* 128 Zeichen
* Non-Printable und Printable Chars


#### ISO 8859 
* 8 bits 
* kompatibel zu US-ASCII
* Verschiedene Versionen

#### Unicode

* Code point für alle Chars
* kompatibel zu US-ASCII
* Verschiedene Formate
  * UTF-8: variable length 1-4 bytes
    * Verschwendet Bits bei nicht ASCII Zeichen
  * UTF-16: variable length 2 or 4 bytes
    *  2 bytes minimum (U+0000 - U+FFFF)
    * 4 bytes ( > U+FFFF)
      * **Surrogate Pairs**: Kodierung als zwei 16-Bit Zahlen 
  * UCS-2: fixed length 2 bytes (nicht alles darstellbar)
  * UTF-32: fixed length 4 bytes
    * 32-Bit für alle Zeichen
    * leichte Handhabung
    * Verschwendung von Bits für meiste Zeichen

##### UTF-8 Decoding Algorithm

##### UTF-16 Surrogates

##### Byte Order in Unicode

* UTF-8
  * Jedes Byte ist eine 8-Bit Zahl
  * Endian nicht relevant
  * Vorgabe durch bsp. Sockets
* UTF-16
  * Beides möglich durch BOM
  * BOM-Markierung
    * Unsichtbar
    * Am Anfang des Strings

## Text-Based and Binary Encoding

### Text-basierte Protokolle

* Einfach zu verstehen und zu debugen

### Binary Protkolle

* Effizienz
* Geringe Message-Größe
* Konvertierung

### Schema

* Statisches Schema
  * Syntax und Semantik sind fest definiert
  * Probleme bei Änderungen des Protokolls
* In-Band Signaling
  * Definition und Wert werden gemeinsam verschickt <<Type, Length, String>, <Type, Length, int>>
  * ABER: Schema sagt nichts über Semantik - Spezifikation schon
  * Protokoll-Version einbetten um semantische Änderungen zu verdeutlichen

### Extensible Markup Language (XML)

* Canonical representation
* Text-basiert
* Selbst beschreibend
* Validierung auf Grundlage eines Schemas
* Plattform unabhängig
* Ideal für den text-basierten Austausch von Informationen
* Hirarchische Struktur
* Nur syntaktische Vorgaben - Interpretation offen
* Lesbar für Menschen 
* Validierung und Transformationen möglich

![enter image description here](https://lh3.googleusercontent.com/-18qzQeqc3UE/VzNy9JZNbWI/AAAAAAAAO5w/3CdxGgEDpf03uegxzxj4o5EffrxpDqS3wCLcB/s0/Auswahl_023.png "Auswahl_023.png")

#### Konventionen

* Unicode only
* Ein Root-Element
* Start- und End-Tags (case sensitive)
* Alle Elemente müssen geschlossen werden
* Richtiges Nesting
* Attribute in '"'-Zeichen
* Reservierte Chars müssen escaped werden


## JavaScript Object Notation (JSON)

* Selbst beschreibend
* Keine Features
* Data2JSON und senden -> JSON2Data (parsing)
* Plattform unabhängig
* Datentypen:
  * String
  * Boolean
  * Array
  * Object (Key / Value)
  * null

## Common Data Represention (CDR)

* Prinzip: Empfänger macht das schon
* Sender bestimmt Byte Order
* Externe Definition eines Schemas notwendig
* Datentypen
  * Simple (short, long, float, char, ...)
  * Complex (sequence, string, union, struct)
  * Data Alignment - Padding mit nulls notwendig

![enter image description here](https://lh3.googleusercontent.com/-iwrzqRdW524/VzN3Tz84BmI/AAAAAAAAO6A/vaiRZ2XcuK0XuU_b8SZ2WdkTdZxz_xHDQCLcB/s0/Auswahl_024.png "Auswahl_024.png")


## ISO ASN.1

* Standard für die Representation von Datenstrukturen
* Canonical 
* Big-Endian für Zahlen
* Syntax für Schemata
  * Übersetzung von abstrakter Syntax in konkrete Syntax
* Transfer: Verschiedene Encoding Formate

### Syntax-Arten

* Abstract
  * Beschreibt die Struktur der Daten unabhängig von der Programmiersprache
* Concrete
  * Beschreibt die Struktur der Daten für eine bestimmte Programmiersprache
* Transfer
  * Struktur der Daten für die Überführung in eine andere Form

![enter image description here](https://lh3.googleusercontent.com/-UDjR-p730HY/VzN46LjsBoI/AAAAAAAAO6U/gS1gpaeA1B4RhYT5XnRn3qrLqzkGvbO6QCLcB/s0/Auswahl_025.png "Auswahl_025.png")































> Written with [StackEdit](https://stackedit.io/).