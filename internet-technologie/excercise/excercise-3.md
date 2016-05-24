# IT&WE: Übung 3

**Name**
Selcuk kekec           

**Matrikelnummer**
3025670

-------------------

## Aufgabe 1

### I Wieso und von wem wird Spam versendet?

> Quellen: Folien und [Wikipedia](https://www.google.de/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0ahUKEwiF5Z-mpvLMAhUHWSwKHdiNAH0QFggcMAA&url=https%3A%2F%2Fde.wikipedia.org%2Fwiki%2FSpam&usg=AFQjCNEFbaPOUty9F1yv0VQ7FIihZKfXOQ&sig2=TJBXkaTsKfo_dPwqYuQplg&bvm=bv.122852650,d.bGg)

Spam wird oft zu kommerziellen Zwecken eingesetzt und kann auf verschiedenste Arten auftreten (E-Mail, Blogeinträge, Wikis, SMS, InstantMessenger,...). Oft enthalten Spam-Nachrichten Verweise auf Dienstleistungen und Produkte bestimmter Hersteller. Es gibt aber auch Vorkommen von Scam, bei dem der Empfänger mit trickreichen Mitteln *betrogen* wird. Spam ist also keinesfalls positiv, sondern eine agressive Angebots- und Betrugsmasche. Die Sender von Spam-Nachrichten sind oft Betreiber, Sub-Betreiber von Online-Shops, die Spam als Werbemittel ansehen. Da die Anzahl offener Mail-Relays stark abgenommen hat wird es immer schwieriger Spam-Mails zu versenden. Deshalb weichen die Versender von Spam-Nachrichten, die im Auftrag von anderen handeln, auf Bot-Netze aus. 

### II Wie kommen Spamversender an die E-Mail Adressen der Empfänger?

> Quellen: Folien und [Wikipedia](https://de.wikipedia.org/wiki/Spam)

Die E-Mail-Adressen der Empfänger werden über Web-Crawler gesammelt. Dazu werden verschiedenste Quellen angezapft: USENET, WHOIS, RANDOM DOMAIN NAMES, DISCUSSION BOARDS,...

Es gibt verschiedenste Möglichkeiten die eigene E-Mail-Adresse davor zu schützen von diesen Crawlern entdeckt zu werden:

* Verschleierung: alice (at) example (dot) net
* Bild: Verwendung eines JPEGS,PNGS, GIFS, welches die eigene E-Mail-Adresse abbildet.
* JavaScript: Anstelle der Angabe in Plaintext, kann mittels JavaScript die Adresse zusammengebaut werden
* Wegwerf-Adressen

### III Was ist ein *Open Relay*? Wieso sollte man keines betreiben?

> Quellen: Folien und [Wikipedia](https://de.wikipedia.org/wiki/SMTP-Relay-Server)

SMTP-Relay-Server sind Dienste, die eine E-Mail annimmt und an die adressierten **Empfänger** weiterleitet. Die Angabe von mehreren Empfängern bewirkt also, dass die Nachricht mehrmals generiert und versendet wird. Ein schlecht konfigurierter SMTP-Relay wird hierbei als *Open Relay* bezeichnet. Diese Relays führen keinerlei Prüfung über Zuständigkeiten durch und ist ein perfektes Werkzeug für Spam-Emails. Es können sehr einfach massenhaft generierte E-Mails verschickt werden.

### IV Was bezeichnet man als *Backscatter*? Wie kann *Backscatter* vermieden werden?

> Quellen: Folien und [Wikipedia](https://de.wikipedia.org/wiki/Backscatter_(E-Mail))

Backscatter sind *Delivery Status Notifications*, welche an den vermeindlichen Absender einer E-Mail gesendet werden. Da Spam-Nachrichten niemals den waren Absender angeben, wird somit ein eigentlich Unbeteiligter über den bestimmten Status seiner vermeintlichen Nachricht benachrichtigt.

Das Unterbinden von Backscatter erfolgt zum einen über die Restriktion, dass Delivery Status Notifications lediglich an über SMTP-Auth authentifizierte Adressen gesendet werden. Andernfalls bricht der MTA die Verbindung rechtzeitig ab.

Eine andere Möglichkeit bietet sich an, wenn der MTA über die Adressen seiner Domain informiert ist und mit einem Virenscanner und einem Spamfilter zusammenarbeitet kann. Auf diesem Weg kann Backscatter an nicht real existierende Adressen vermieden werden.

### V Wie funktionieren *Bayessche Filter*? Wie können sie automatisch lernen?

> Quellen: Folien und [Wikipedia](https://en.wikipedia.org/wiki/Naive_Bayes_spam_filtering)

Bayessche Filter funktionieren auf Grundlage von Statistiken, die jedem Word eine Wahrscheinlichkeit der Verwendung in Spam- und Ham-Nachrichten zuordnen. Die Formel arbeitet dabei auf Basis von verschiedenen Wahrscheinlichkeiten:

* Wahrscheinlichkeit das Wort in Spam vorkommt **P( W | S )**
* Wahrscheinlichkeit das eine Nachricht Spam ist **P( S )**
  * Allgemeine Statistiken belegen diese Wahrscheinlichkeit mit 80%
* Wahrscheinlichkeit das Wort in Spam/Ham auftritt **P( W )**

Mittels dieser Werte wird die Wahrscheinlichkeit berechnet, dass eine Nachricht Spam ist, falls es ein ganz bestimmtes Wort enthält **P( S | W )**.

> (P(W|S) * P(S)) / P(W) = P(S|W)

Moderne Spam-Filter können vom Benutzer weiter verfeinert werden. Sobald eine Nachricht vom Nutzer explizit als Spam markiert wird, untersucht der Spam-Filter diese Nachricht und lernt von der Aktion des Nutzers. Den Wörtern dieser Nachricht wird eine höhere Spam-Wahrscheinlichkeit zugeordnet.

## Aufgabe 2

### I Was ist SpamAssassin und wie funktioniert es?

> Quellen: Folien und [Wikipedia](https://de.wikipedia.org/wiki/SpamAssassin)

**SpamAssassin** ist ein Programm, dass unerwünschte Spam-Nachrichten auf Grundlage verschiedener Mechanismen auswertet und einen Score ausrechnet, der die Spam-Wahrscheinlichkeit wiederspiegeln soll.

Auf Grundlage von definierten Grenzwerten im Bezug auf den Score kann SpamAssassin definierte Aktionen ausführen:

* Lehne Nachricht ab mit Error
* Akzeptiere und löschen Nachricht daraufhin
* In den Spam-Ordner verschieben
* Fallback: greylisting, challange/response, teergrube
* 
### II Welche Filter unterstützt SpamAssassin und was bewirken sie?

> > Quellen: Folien und [Wikipedia](https://de.wikipedia.org/wiki/SpamAssassin)

Dabei kommen verschiedene Techniken zum Einsatz:

* Statische Regeln: Reguläre Ausdrücke von spam-typischen Wort-Sequenzen
* RBLs (Realtime Blackhole Lists): Listen von Servern, welche bekanntlich Spam versenden
* HashTables a la Razor, Pyzor, DCC: Datenbank mit Hashes, welche aus den Bodies  von als Spam bewerteten Nachrichten erstellt wurden.
  * Clients und Server senden Hash an DCC
  * Das Auftreten der Hashes wird gezählt und gespeichert
  * Clients können Auftreten des Hashes abfragen und mit Hilfe definierter Grenzwerte darauf reagieren
* Bayessche Filter

### III Was ist mit Tarpit und Greylisting gemeint? Was sind seine Vor- und Nachteile?

> Quellen: Folien und [Wikipedia](https://en.wikipedia.org/wiki/Greylisting)

Tarpit (Teergrube) ist ein Verfahren, bei dem unerwünschte und verdächtige Netzwerkverbindungen künstlich verlangsamt werden, um eine lange Blockierung des Verbindungspartners zu erreichen. Durch das langsame Antworten ist der Client damit beschäftigt auf sehr träge ankommende Antworten des Servers zu warten.

Greylisting hingegen ist ein Verfahren, bei dem der Mailserver auf Grundlage der Kombination von

* IP-Adresse des absendenden MailServers
* E-Mail-Adresse des Absenders
* E-Mail-Adresse des Adressaten

die Nachricht annimmt oder ablehnt. Beim erstmaligen Auftreten dieser Kombination verhindert der MailServer die Zustellung mit der Meldung, dass ein temporärer Fehler aufgetreten sei. RFC-konforme SMTP-Server unternehmen normalerweise einen weiteren Zustellungsversuch. Dieser würde ab einem bestimmten Zeitintervall akzeptiert werden.


**Vorteile**:

* Vorteil: Software für den Massen-Versand von E-Mails versucht oft lediglich einmal das Versenden einer Nachricht
* Vorteil: Filterungen, die auf Netzwerkprüfungen basieren greifen durch den Zeitversatz oft besser, da eine gewisse Zeit der Auswertung bleibt
* Auswertung lediglich auf Basis von Envelope-Daten
  * Es muss nicht die komplette Nachricht mit Body und Anhängen geladen werden
  * Entlastet dahinterstehende Spamfilter
* Es gehen keine E-Mails verloren, wie bei heuristischen Spam-Filtern
* Paralleles führen einer Whitelist
  VreliretVre
**Nachteile**:

* Falsch konfigurierte MailServer könnten weitere Zustellversuche verweigern
* Zeitverzögerung: Es kann bei der Zustellung durch das erstmalige Ablehnen zu Verzögerungen kommen
* Verliert zunehmend an Effizienz, durch die Weiterentwicklung der Spam-Software

### IV Welche Möglichkeiten gibt es Clients vor dem E-Mail Versand via SMTP zu authentifizieren? Welches Verfahren hat sich durchgesetzt?

> Quellen: Folien und [Wikipedia](https://de.wikipedia.org/wiki/SMTP-Auth)

* Überprüfung der Adresse: Spoofing-Gefahr
* IP-Adresse
  * Nur möglich für geschlossene Gruppen mit festen IPs
* SMTP after POP
  * Benutzer wird mittels POP authentifiziert und die IP wird zwischengespeichert
  * SMTP überprüft, ob die IP authentifiziert wurde und lässt Verbindung zu oder lehnt diese ab
* SMTP-AUTH: benötigt EXTENDED SMTP
  * Plain login
    * Daten werden Base64-Kodiert übertragen
    * Kodierung != Verschlüsselung
    * Keine Sicherheit, solange kein Einsatz von TLS/SSL
  * Digest Authentication
    * Server sendet challange (zufällige generierter eindeutiger String)
    * Client entschlüsselt challange mit dem eigenen Passwort und sendet diese an den Server zurück
    * Server tut das selbe mit dem bekannten Password für den Benutzer und vergleicht den Response des Clients

### V Was sind DKIM und SPF? Wie können sie helfen Spam zu vermeiden? Vergleichen sie beide Ansätze!

> Quellen: Folien und Wikipedia

**DKIM:**

* DomainKey
* MTA signiert ausgehende E-Mails mit einer Signatur
* Empfangede MTA holt daraufhin den PublicKey des Sendenden vom Domain Name System und verifiziert.
* Signatur wird mit SHA-1 oder SHA-256 auf Basis des E-Mail-Inhaltes erstellt
* Dieser Hash wird mittels RSA verschlüsselt und zu besseren Kompatibilität mit dem ASCII-Zeichensatz Bas64-Kodiert.

* Empfangende MTA dekodiert die Signatur mit Base64 und entschlüsselt diese mit dem PublicKey (Bereitstellung durch DNS).
* Der selbstberechnete Hashwert der E-Mail wird mit dem entschlüsselten Wert verglichen

* DKIM dient lediglich zur Sicherstellung, dass der angegebene Absender nicht verschleiert wurde.
* Nicht direkt für Spamfilterung konzipiert
* Einfacher Authentifzierungsmechanismus


**SPF:**

* Verhindert das Fälschen von Absenderadressen
* Administrator benennt in der DNS-Zone, welche MTAs (Angabe per IP) im Namen der eigenen Domain E-Mails versenden dürfen
* Der empfangende MTA kann somit beim Erhalt einer Nachricht den Resource Record vom DNS der Domain abrufen und prüfen, ob der MTA vom Administrator überhaupt für den Versand vorgesehen war oder aber nicht.
* Kein direkter Mechanismus zur Spambekämpfung
* Erschwert lediglich Absenderadressfälschungen

Beide Mechanismen sind keine direkte Technik zur Spambekämpfung. Sie versuchen lediglich sicherzustellen, dass der Absender seine Identität nicht verschleiern kann. DKIM geht dabei den Weg über Verschlüsselung und Signaturen. Dabei müssen beide Seiten die notwendigen Mechanismen (SHA-1 o. SHA-256 und RSA) unterstützen. Die erstellte Signatur wird mittels Headern an den Empfänger übertragen, dass eine zusätzliche Last bedeutet. Da der Hash auf Grundlage des E-Mail-Bodies erstellt wird gibt es wegen des variablen Inhalts (Body ist jedesmal anders) keine Möglichkeit des Cachings. Hinzu kommt, dass für den Authentifizierungsprozess zusätzlich Rechenresourcen verschwendet werden.

SPF hingegen ist verzeichnisorientiert und verlässt sich dabei auf den vom Administrator bereitgestellten SPF-Record. Es benötigt keine Verschlüsselung oder anderweitige Bearbeitung, dass Rechenressourcen beansprucht. Des weiteren wird der E-Mail-Umfang nicht durch weitere zusätzliche Header erweitert. Somit ergibt sich kein Overhead.












