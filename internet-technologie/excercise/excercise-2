# IT&WE: Übung 2

**Name**
Selcuk kekec           

**Matrikelnummer**
3025670

-------------------


## Aufgabe 1

## I

Quoted-Printable ist ein Versuch, Zeichen, die ausserhalb der US-ASCII-Kodierung (> 7 Bit) liegen, darzustellen. Dabei werden jene Zeichen in ihre hexadezimale Repräsentation mit einem führenden "=" übersetzt. 

> Unterschied: 
> * Quoted-Printable: ist nach der Kodierung weitesgehend lesbar
> * Quoted-Printable: Verwendung um E-Mail-Content zu kodieren
> * Base64: übersetzt 8-Bit-Binärdaten in eine Zeichefolge bestehend aus lesbaren ASCII-Zeichen (A-Z, a-z, 0-9,+,/,=) 
> * Base64: 3 Bytes werden in 4x6-Bits übersetzt
> * Base64: Teil von MIME und wird zum Versenden von E-Mail-Anhängen verwendet
> * Base64: Kodieren von Binärdaten

> Vorteile:
> * Quoted-Printable: Weitesgehend Lesbar
> * 

> Nachteile:
> * Base64: Overhead


## II

### Dekodierung "SVB2Ng==" = "IPv6"

|                     	| S        	| V        	| B        	| 2        	| N      	| g      	| =    	|
|---------------------	|----------	|----------	|----------	|----------	|--------	|--------	|------	|
| Binary: Base64      	| 010010   	| 010101   	| 000001   	| 110110   	| 001101 	| 100000 	| 0000 	|
| Decimal: Base64     	| 18       	| 21       	| 1        	| 54       	| 13     	| 32     	| 0    	|
| Binary: 8-Bit Bytes 	| 01001001 	| 01010000 	| 01110110 	| 00110110 	|        	|        	|      	|
| ASCII               	| I        	| P        	| v        	| 6        	|        	|        	|      	|

### Kodierung "SMTP" = "U01UUA=="

|                	| S        	| M        	| T        	| P        	|        	|        	|   	|
|----------------	|----------	|----------	|----------	|----------	|--------	|--------	|---	|
| ASCII-Binary   	| 01010011 	| 01001101 	| 01010100 	| 01010000 	|        	|        	|   	|
| 6-Bit Sections 	| 010100   	| 110100   	| 110101   	| 01010100 	| 010100 	| 000000 	|   	|
| Decimal        	| 20       	| 52       	| 53       	| 20       	| 20     	| 0      	|   	|
| Base64         	| U        	| 0        	| 1        	| U        	| U      	| A      	|   	|


## III

MIME ist eine Erweiterung des RFCs 822, welche eine Kompatibilität für zusätzliche Umlaute und Multimedia bietet. MIME definiert dazu lediglich die zu nutzenden Header und deren Bedeutung bei der Übermittlung von Daten. So kann über spezielle Header der Typ (**Content-Type**) des Inhalts der Nachricht, sowie die Kodierungsart (**Content-Transfer-Encoding**) angegeben werden. Diese Informationen helfen dem Empfänger die Daten richtig zu enkodieren und somit die ursprüngliche Nachricht wieder herzustellen. MIME ist somit lediglich der Umschlag für die übertragenen Daten. 
Standardmäßig erfolgt die Kodierung von Nicht-7-Bit-ASCII-Zeichen mittel Quoted-Printable. Binärdaten hingegen werden über Base64 kodiert. Bei E-Mails ist zwingend eine Kodierung notwendig. HTTP erlaubt hingegen die direkte Übertragung von **binary**, wobei die Daten ohne Kodierung übertragen werden.

MIME erlaubt zudem die Übertragung verschiedener Inhalte im gleichen Umschlag. Dazu definiert es den "Content-Type: multipart/mixed". Dabei werden die verschiedenen Inhalte über "--frontier"-Separatoren voneinander getrennt. Somit kann eine E-Mail mit Betreff und Inhalt und zusätzlich bspw. ein Anhang übermittelt werden.

## IV

**HELO** und **DATA** sind Commands, welche das SMTP-Protokoll für die Kommunikation anbietet. Dabei fungiert **HELO** als Befehl zum Aufbauen einer Verbindung zwischen Client und Server. **DATA** hingegen signalisiert dem Server, dass er nun e-mail-bezogenen Daten empfangen wird.

Das RFC 4021 definiert hingegen lediglich Header und deren Bedeutung für den **DATA**-Bereich und stellt keine Commands für die Kommnunikation bereit.

## Aufgabe 2

Leider bekomme ich andauernd einen **554 SMTP synchronization error**:

```java
package com.company;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.PrintWriter;
import java.net.Socket;

public class Main {

    public static void main(String[] args) {
        Socket socket       = null;
        try {
            socket = new Socket("debby.vs.uni-due.de", 25);
            BufferedReader bufferedReader   = new BufferedReader(new InputStreamReader(socket.getInputStream()));
            PrintWriter printWriter     = new PrintWriter(socket.getOutputStream(), true);

            printWriter.println("HELO localhost");
            System.out.println("HELO: "+bufferedReader.readLine());

            printWriter.println("MAIL From: senycorp@googlemail.com");
            System.out.println("MAIL From: "+bufferedReader.readLine());

            // send to this address
            printWriter.println("RCPT To: spam@debby.vs.uni-due.de");
            System.out.println("RCPT To: "+bufferedReader.readLine());

            printWriter.println("DATA");
            System.out.println("DATA: "+bufferedReader.readLine());

            printWriter.println("Date: Thu, 19 May 2016 12:12:12 -0400");
            printWriter.println("From: Selcuk Kekec <senycorp@googlemail.com>");
            printWriter.println("Subject: Hi guys");
            printWriter.println("To: spam@debby.vs.uni-due.de");
            printWriter.println("X-Mailer: Spam Mailer X");
            printWriter.println("Hi,");
            printWriter.println("das ist eine Test-Message.");
            printWriter.println(".");
            System.out.println(bufferedReader.readLine());

            // clean up
            printWriter.close();
            bufferedReader.close();
            socket.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```


