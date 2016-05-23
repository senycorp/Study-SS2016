# IT&WE: Übung 3

**Name**
Selcuk kekec           

**Matrikelnummer**
3025670

-------------------

## Aufgabe 1

### I Wieso und von wem wird Spam versendet?

Spam wird oft zu kommerziellen Zwecken eingesetzt und kann auf verschiedenste Arten auftreten (E-Mail, Blogeinträge, Wikis, SMS, InstantMessenger,...). Oft enthalten Spam-Nachrichten Verweise auf Dienstleistungen und Produkte bestimmter Hersteller. Es gibt aber auch Vorkommen von Scam, bei dem der Empfänger mit trickreichen Mitteln *betrogen* wird. Spam ist also keinesfalls positiv, sondern eine agressive Angebots- und Betrugsmasche. Die Sender von Spam-Nachrichten sind oft Betreiber, Sub-Betreiber von Online-Shops, die Spam als Werbemittel ansehen. Da die Anzahl offener Mail-Relays stark abgenommen hat wird es immer schwieriger Spam-Mails zu versenden. Deshalb weichen die Versender von Spam-Nachrichten, die im Auftrag von anderen handeln, auf Bot-Netze aus. 

### II Wie kommen Spamversender an die E-Mail Adressen der Empfänger?

Die E-Mail-Adressen der Empfänger werden über Web-Crawler gesammelt. Dazu werden verschiedenste Quellen angezapft: USENET, WHOIS, RANDOM DOMAIN NAMES, DISCUSSION BOARDS,...

Es gibt verschiedenste Möglichkeiten die eigene E-Mail-Adresse davor zu schützen von diesen Crawlern entdeckt zu werden:

* Verschleierung: alice (at) example (dot) net
* Bild: Verwendung eines JPEGS,PNGS, GIFS, welches die eigene E-Mail-Adresse abbildet.
* JavaScript: Anstelle der Angabe in Plaintext, kann mittels JavaScript die Adresse zusammengebaut werden
* Wegwerf-Adressen

### III Was ist ein *Open Relay*? Wieso sollte man keines betreiben?

SMTP-Relay-Server sind Dienste, die eine E-Mail annimmt und an die adressierten **Empfänger** weiterleitet. Die Angabe von mehreren Empfängern bewirkt also, dass die Nachricht mehrmals generiert und versendet wird. Ein schlecht konfigurierter SMTP-Relay wird hierbei als *Open Relay* bezeichnet. Diese Relays führen keinerlei Prüfung über Zuständigkeiten durch und ist ein perfektes Werkzeug für Spam-Emails. Es können sehr einfach massenhaft generierte E-Mails verschickt werden.

### IV Was bezeichnet man als *Backscatter*? Wie kann *Backscatter* vermieden werden?

Backscatter sind *Delivery Status Notifications*, welche an den vermeindlichen Absender einer E-Mail gesendet werden. Da Spam-Nachrichten niemals den waren Absender angeben, wird somit ein eigentlich Unbeteiligter über den bestimmten Status seiner vermeintlichen Nachricht benachrichtigt.

Das Unterbinden von Backscatter erfolgt zum einen über die Restriktion, dass Delivery Status Notifications lediglich an über SMTP-Auth authentifizierte Adressen gesendet werden. Andernfalls bricht der MTA die Verbindung rechtzeitig ab.

Eine andere Möglichkeit bietet sich an, wenn der MTA über die Adressen seiner Domain informiert ist und mit einem Virenscanner und einem Spamfilter zusammenarbeitet kann. Auf diesem Weg kann Backscatter an nicht real existierende Adressen vermieden werden.

### V Wie funktionieren *Bayessche Filter*? Wie können sie automatisch lernen?

Bayessche Filter funktionieren auf Grundlage von Statistiken, die jedem Word eine Wahrscheinlichkeit der Verwendung in Spam- und Ham-Nachrichten zuordnen. Die Formel arbeitet dabei auf Basis von verschiedenen Wahrscheinlichkeiten:

* Wahrscheinlichkeit das Wort in Spam vorkommt **P( W | S )**
* Wahrscheinlichkeit das eine Nachricht Spam ist **P( S )**
  * Allgemeine Statistiken belegen diese Wahrscheinlichkeit mit 80%
* Wahrscheinlichkeit das Wort in Spam/Ham auftritt **P( W )**

Mittels dieser Werte wird die Wahrscheinlichkeit berechnet, dass eine Nachricht Spam ist, falls es ein ganz bestimmtes Wort enthält **P( S | W )**.

> (P(W|S) * P(S)) / P(W) = P(S|W)

Moderne Spam-Filter können vom Benutzer weiter verfeinert werden. Sobald eine Nachricht vom Nutzer explizit als Spam markiert wird, untersucht der Spam-Filter diese Nachricht und lernt von der Aktion des Nutzers. Den Wörtern dieser Nachricht wird eine höhere Spam-Wahrscheinlichkeit zugeordnet.



















