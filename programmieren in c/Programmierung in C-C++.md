
# Programmierung in C/C++

# Kapitel 1: Einführung in die Konzepte von Programmiersprachen

* C/C++ sind von Neumann Sprachen

## Von Neumann Model
 * Vorgabe der Architektur
  	* memory, control unit arithmetic/logical unit
 * Daten und Kommandos werden im Speicher abgelegt
 * Command counter hält Addrese des nächsten Befehls
 * Programme in der VN Architektur
   * Sequenzen von Befehlen welche von der CPU ausgeführt werden
   * Kontrollstrukturen: Jump-Befehl für explizite Steuerung (Control flow)
   * Variablen sind symbolische Zeiger auf eine Speicheradresse

## Sprachkonstrukte

* Sprachkonstrukte bestehen aus:
  * Syntax (Form und Vorgabe zur Erstellung von Konstrukten)
  * Semantik (Aussage des Konstrukts)
* Konstrukte (variables, types, procedures, objects)
  *  Bestehen aus Attributen
  *  Binding: Zuweisung eines Wertes zu einem Attribut des Konstrukts
  *  Dynamische und statische Bindung
    * dynamisch: Zur Laufzeit
    * Statisch: Vor der Laufzeit

### Beispiel: Variablen

Attribute eines Variablen-Konstrukts:

* Wert
* Name
* Scope
* Adresse
* Typ
* Lebensdauer
* Veränderbarkeit

## Compiled vs. Interpreted

Beide Strategien lesen eine Datei

* Compiler übersetzt Progamm in Code
 * Kann auf Korrektheit prüfen
 * Kann Code optimieren (bsp. für Multicore)
 * Compiler generiert
   * ausführbar
   * zwischencode
   * in anderer Sprache (cross-compiling)
 * Compiler übernimmt nicht alle Aufgaben
   * Linker: Kombiniert verschiedene Programmteile
   * Loader: Ladet Programm in den Hauptspeicher

* Interpreter
 * Liest Programm und führt Befehle sofort zur Laufzeit aus

* Just-in-time compiler
  * Liest, analysiert und führt Code sofort aus
  * Code wird ebenfalls optimiert

## Language runtime

* Realisierung durch
  * compiler-generated code
  * Bibliotheken
  * OS calls
* Aufgaben
  * Runtime checks
  * Error handling
  * Memory management

Die Java-Runtime wäre dabei die Java Virtual Machine

## Runtime Checks, Error handling, Memory management

TODO: Folien der ersten Vorlersung

# Kapitel 2: Programmierung in C

* Imperative Programmiersprache
* Designed für kleine Programme im UNIX-Umfeld
* Hardware-unabhängige Abstraktionsebene von Assembler
* kleine Anzahl an Keywords
* Funktionalitäten aus Bibliotheken nutzbar
* Kleine Laufzeitumgebung
* Einfache Portierung

## Hosted vs. Freestanding
* Hosted: Unterstützung von Standard libraries (OS)
* Freestanding: Begrenzte Unterstüzung von Bibliotheken
  * Ausführung unmittelbar auf Hardware oder Embedded Systems

## Vor- und Nachteile

* Vorteile
  * Einfach zu lernen
  * Sehr effizient
  * Lesbarer Sourcecode (Pflegbarkeit)
* Nachteile
  * Kann zu schwer pflegbaren oder ineffizienten Code führen

## Konzepte

* Structured programming
  * Kontrollstrukturen
* Static (weak) typing
  * Basis und zusammengesetzte Datentypen
* Autonome Funktionen
* Pointers
* Preprocessor und Macros
* Standard library

## Variablen und Datentypen

* müssen vorher deklariert werden
* statische Typenbindung (static type binding)
* statischer Benamung
* Scopes und Lifetime veränderbar
* Unterstützt basic types und composite types (structs)

## Compiling process


![Auswahl_001.png](/home/senycorp/Bilder/Auswahl_001.png)

![Auswahl_002.png](/home/senycorp/Bilder/Auswahl_002.png)

## C Code Files

* Header files (.h)
 * types, variables, function declarations, macros
 * Beschreiben interfaces
 * Können per #include an externer Stelle eingefügt werden
* Source code files (.c)
  * types, variables, function definitions
  * main() als Einstiegspunkt für den Compiler
  * hat konkrete Implementierung
  * Übersetzung in object code (.o)
* Libraries
  * Vorkompilierte Funktionen (System, DLLs)

## Java vs. C

### Unterschiede

JAVA
* Denition und Deklaration in .java files
* Übersetzung in Byte Code
* Libraries als .jar
* Übersetzung von JVM
  * Sucht automatisch nach externem ByteCode (kein statisches Linking)
  * Nachteil: Compiler braucht vollen Zugriff auf Code bei der Kompilierung

C
* Separation von Deklaration und Definition
* Einbindung von Definitionen (.h) über #include
* Code aller verlinkten Dateien wird zu einer ausführbaren Datei zusammengefasst

## Der C-Präprozessor

* Ausführung des Präprozessors vor Kompilierung
* Aufgaben:
  * Einbindung externer Dateien
  * Definition von Konstanten
  * Makros
  * Steuerung der Kompilierung
  * Steuerung der Ausführung
* Beginnen mit "#" und dürfen nicht mit ";"
* Simples kopieren des Codes
 * "#"include <filename>: Für Standard Libraries und Bibliotheken aus voreingestellten Ordnern
 * "#"include "filename": Für eigene Dateien aus dem lokalen Ordnerumfeld

## Konstanten

* \#define identifier replacement-text
  * Präprozessor ersetzt alle Vorkommen von "identifier" mit "replacement-text"
* Konstanten-identifier müssen Unique sein
* Vorteil: Verbrauchen keinen Speicher
* Nachteil: Keine Kontrolle über Typen, Debugging
* const-Variablen sind zu bevorzugen

## Makros

* Konstanten mit Parametern
* Verhalten sich wie Funktionen
* Sind gefährlich
* "#"undef zum löschen einer Definition

![Auswahl_003.png](/home/senycorp/Bilder/Auswahl_003.png)

![Auswahl_004.png](/home/senycorp/Bilder/Auswahl_004.png)

## Conditional Compilation

* Bedingungen in Header-Files erlauben optionale Ausführung von Code
* Konstanten können über gcc gesetzt werden: gcc -DDEBUG=1 -o program program.c
![Auswahl_005.png](/home/senycorp/Bilder/Auswahl_005.png)

## \#error und \#pragma

## \# and \##


![Auswahl_006.png](/home/senycorp/Bilder/Auswahl_006.png)

## Vordefinierte Konstanten


![Auswahl_007.png](/home/senycorp/Bilder/Auswahl_007.png)

## Data types

* Beschreiben unterstützte ranges
* Wie werden Daten im Speicher abgelegt/repräsentiert
* Welche Operationen werden unterstützt

### Integers

* char, short int, int, long int, long long int
* Standard: signed ausgenommen char
* Wertebereich nicht klar definiert: Hirarchie
  * sizeof(char) < sizeof(short) < sizeof(int) < sizeof(long) < sizeof(long long)
  * Minimum Wertebereich definiert
    * char 8-bit
    * short 16-bit
    * long 32-bit
    * long long 64-bit

#### Integer Literale

* Präfix
  * 0 für oktal
  * 0x für hexadezimal
* Suffix: Angabe von signed/unsigned und Typ möglich jedoch nicht mehr notwendig

####  Character Literals

TODO

## Unicode

Keine Unterstützung in alten Versionen. In C11 jedoch schon.

## Floating points

* Float (single precision)
* double (double precision)
* long double (extended precision)

Genauigkeit hängt von genauer Implementierung ab und ist platformabhängig.

!! Es gibt keine unsigned floating points !!

## Void

Void hat keinen Wert und kann nicht abgerufen. Es wird lediglich für Funktionen ohne Rückgabetypen verwendet und Pointers.

## Komplexe Zahlen

* C99 setzt komplexe Zahlen für "Hosted"-Umgebungen voraus, aber nicht für "embedded"-Systeme
* C11 bezeichnet beides als optional
* Verfügbarkeitsprüfung über Konstante __STDC_NO_COMPLEX
* C++ hat komplett andere Templates

## Boolean

* Erst mit C99 verfügbar
* Integer als boolean (0 = false, >0 = true)
* C99: _Bool
* C++ hat einen eigenen Datentyp

## Enumerations

* Liste von Integers mit Identifier
* Unique Identifier
* Keine Sicherheit über Typ

## typedef

* Kein neuer Datentyp lediglich ein Alias für einen Bestehenden

``` c
typedef int age;
```

## Zusammenfassung


![Auswahl_008.png](/home/senycorp/Bilder/Auswahl_008.png)

## Variables and Constants
Variablen und Konstanten müssen vor der Verwendung deklariert werden. Dies dient zu Vereinfach des Parsings. Moderne Compiler setzen dies nicht mehr voraus.

* Declaration
 * Identifier ist case sensitive
 * Name und Typ (static)
 * Mehrfache Deklaration für die selbe Variable möglic asdh
* Definition
 * Analog zur Deklaration
```
 int a;
```
  * Reserviert Speicherbereich für Variable und macht eine Zuweisung
* Initialization
  * Zuweisung eines initialen Wertes zu einer Variable
  * Nicht zwangsläufig statisch

## Scopes

* Scopes sind der Geltungsbereich einer Variable, in der es abrufbar ist.
* Überlappende/Verschachtelte Scopes sind möglich
* Gleicher Identifier für Variablen in verschiedenen Scopes möglich

Es gibt 4 Arten von Scopes:

* File Scope
  * Gilt für eine Datei
  * Globale Variablen: Definition außerhalb einer Funktion
* Function Scope
  * Innerhalb einer Funktion deklarierte Variablen sind nur dort gültig und zugänglich
* Block Scope
  * {}-Blocks
  * Innerhalb des Blocks und der Funktion deklarierte Variablen sind zugänglich
* Function-prototype scope
  * Parameter list: Naming nicht wichtig nur die Anzahl

## Storage Classes

* Lifetime,Zeitpunkt und Ort des Speicherbereichs, Freigabe des Speicherbereichs

## Auto

```
{
	auto int month;
}
```

* Nur in Block-Scopes nutzbar
* Freigabe unmittelbar nach dem Verlassen des Scopes

## Register

* Nur in Block-Scopes nutzbar
* Schiebt Variable in high-speed register
* Sinnvoll für oft genutzte Variablen (loop counter)
* Optimierung macht es jedoch unnötig
```
{
	register int month;
}
```

## Static

* Standard für GLOBALS
* Speicherreservierung vor Programmstart (Static memory mnagement)
* Variable existiert bis zum Programmende
* Scope rules gelten weiterhin
* Auch für Block Scopes nutzbar
* Funktionsparameter ausgenommen

```
{
	static int month;
}
```

## Extern

* Definierte Variablen aus anderen Dateien einbinden
* Nur für GLOBALS
* Deklaration ohne Definition

## _THREAD_LOCAL

* Seit C11 verfügbar
* Jeder Thread bekommt eigene Kopie
* Reservierung bei Start, Freigabe bei Ende eines Threads
* Nutzbar mit *extern* und *static*

```
_Thread_local int a;

void example(void) {
	static _Thread_local int b;
}
```

## Konstanten

* Keyword: *const*
* Muss bei der Definition initialisiert werden
* **nicht veränderbar**

## Volatile

* Keyword: *volatile*
* Signalisiert dem Compiler, dass eine Veränderung der Variable durch externe Programmsegmente möglich ist
* Multi-Threading
* Compiler unterlässt Optimierung

## Variable Alignment

* Zugriff auf gerade Speicheradressen ist effizienter als auf Ungerade
* Padding zum Auffüllen
* Ab C11
* Alignment beeinflussbar durch **_Alignas**


![Auswahl_009.png](/home/senycorp/Bilder/Auswahl_009.png)

![Auswahl_010.png](/home/senycorp/Bilder/Auswahl_010.png)


## Control Structures

* if
* while-do, do-while
* switch()-case
* for()-loop mit break und continue

## Sequence Points

``“any point in a computer program's execution at which it is guaranteed that all side effects of previous evaluations will have been performed, and no side effects from subsequent evaluations have yet been performed.” (Wikipedia)``

> Written with [StackEdit](https://stackedit.io/).