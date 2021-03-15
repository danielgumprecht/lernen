# 1. Modellierung
## Entwurfsphasen
Die Entwurfsphasen einer DB werden in 5 Teile geteilt:

### Anforderungsanalyse
Hier werden alle Anforderungen aller Benutzer zusammengefasst und nach Kriterien wie (Abteilung, Benutzergruppe) klassifiziert. Weiters wird festgelegt was gespeichert wird und wie die Daten zu bearbeiten sind. 

### Konzeptioneller Entwurf
Am ende dieser Phase hat man das ER-Model und es sind alle Beziehungen und welche Daten mit welchen Eigenschaften in der DB abgebildet werden. Bevor der Logische Entwurf erstellt werden kann, muss festgelegt werden, für welches DBS die Datenbank aufgebaut werden soll. 

### Logischer Entwurf
Nun erfolgt die Umsetzung des Konzeptionellen Shemas in das Datenbankmodell des DMS. Anschließend wird die DBS normalisiert, wodurch Redundanzen beseitigt werden.

### Verfeinerung des Entwurfs
Hier können Beispielweiße Indizes hinzugefügt werden, welche die Datensuche in häufig verwendeten Spalten erleichtern.

### Physischer Entwurf / Implementierung
Hier werden geeignete Speicherstrukturen und Zugriffsmechanismen und Zugriffsrechte festgelegt.

# 2. Strukturierte Abfragesprache

## Sprachumfang von SQL


## Datentypen

Jedem Attribut wird ein bestimmter Datentyp zugeordnet. Dabei unterscheidet man zwischen verschiedenen Zahlentypen (Ganzzahlig, Dezimal), Zeichenketten (Text, Varchar), Datumstypen und Boolean (true, false).

- INTEGER → 4 Byte
- DOUBLE → 8 byte
- VARCHAR → (1-255)

#### Numerische Datentypen für ganzzahlige Werte
- SMALLINT → 32768 bis +32767
- INTEGER →  2147483648 bis +2147483647
- BIGINT → 9223372036854775808 bis +9223372036854775808

#### Numerische Datentypen für Fließkommazahlen
- FLOAT(n) → Die Gesamtstellenanzahl kann durch n festgelegt werden. Je nach Angabe von n können 7 bis 15 signifikante Stellen plattformunabhängig gespeichert werden.
- REAL → 7 signifikante Stellen
- DOUBLE PRECISION → 15 signifikante Stellen

#### Numerische Datentypen für Festkommazahlen
- NUMERIC(Präzision, Skalierung)
- DECIMAL(Präzision, Skalierung)
- Der Parameter Präzision (1-15) legt die Gesamtzahl der signifikanten Stellen der Zahl
fest. Der Parameter Skalierung (1-15) bestimmt die Anzahl der Nachkommastellen, die kleiner oder gleich der Gesamtzahl der Stellen sein muss. Der Unterschied zwischen NUMERIC und DECIMAL liegt darin, dass NUMERIC die exakte Anzahl und DECIMAL die minimale Anzahl der signifikanten Stellen angibt.

#### Datentypen für Datums- und Zeitwerte
- DATE → 01.01.1000 bis 31.12.9999
- TIME → 00:00:00 bis 23:59:59
- TIMESTAMP → '1970-01-01 00:00:01' bis '2038-01-19 03:14:07'

#### Datentypen für Zeichen und Texte
- CHAR (Länge)
- VARCHAR(Länge)
- BLOB
- TEXT

#### Logischer Datentyp
- BOOLEAN

## JOIN

### INNER JOIN

Der INNER JOIN führt Datensätze aus der linken und rechten Tabelle genau dann zusammen, wenn die angegebenen Kritieren alle erfüllt sind.

```sql
SELECT
  RechnungsNr,
  KundenNr,
  Betrag,
  Rechnungen.Kartennummer,
  Firma,
  Inhaber,
  Ablaufdatum
FROM Kreditkarte
INNER JOIN Rechnungen ON Kreditkarte.Kartennummer = Rechnungen.Kartennummer
```

### LEFT/RIGHT JOIN

Left Join → Ein Datensatz aus der linken Tabelle kommt in jedem Fall in das Ergebnis. Wenn ein Datensatz der rechten Tabelle dem ON-Kriterium entspricht, so wird er entsprechend in den Spalten eingetragen ansonsten bleiben die Spalten leer (*NULL).* 

Der right join arbeitet genau entgegengesetzt.

```sql
SELECT
  RechnungsNr,
  KundenNr,
  Betrag,
  Rechnungen.Kartennummer,
  Firma,
  Inhaber,
  Ablaufdatum
FROM Rechnungen
LEFT JOIN Kreditkarte ON Kreditkarte.Kartennummer = Rechnungen.Kartennummer
```

### FULL OUTER JOIN

Der FULL OUTER JOIN ist die Kombination aus LEFT und RIGHT JOIN. Jeder Datensatz der rechten und der linken Tabelle kommt in die Ergebnismenge. Finde sich über das ON-Kriterium ein passender Partner werden beide zusammengefügt. Wenn nicht dann wird die andere Seite mit NULL ausgefüllt.

```sql
SELECT
  RechnungsNr,
  KundenNr,
  Betrag,
  Rechnungen.Kartennummer,
  Firma,
  Inhaber,
  Ablaufdatum
FROM Rechnungen
OUTER JOIN Kreditkarte ON Kreditkarte.Kartennummer = Rechnungen.Kartennumme
```

## Aggregatfunktionen
dienen vor allem der statistischen Auswertung der gespeicherten Daten. In vielen Fällen werden nicht die einzelnen Datensätze einer Abfrage benötigt, sondern beispielsweise nur eine Information über die Anzahl der ermittelten Datensätze oder über einen Minimalbzw. Maximalwert. Für diesen Zweck existieren in SQL Aggregatfunktionen, die Berechnungen über alle oder ausgewählte Datensätze durchführen. Beispiele für Aggregatfunktionen sind: `MIN()`, `MAX()`, `AVG()` und `COUNT()` wobei diese Funktionen Attribute als Argumente annehmen.

# 3. Grundlagen
## Datenbank Lebenszyklus
- **Anforderungsanalyse:** Hier werden die Inhalte der neuen Datenbank eingegrenzt und die Benutzergruppen und Anwendungen definiert. Dabei werden die Datenobjekte, deren Eigenschaften und Beziehungen sowie mögliche Vorgänge (Aktualisierungen, Abfragen) und Randbedingungen ermittelt. Das Resultat ist die Anforderungsspezifikation.
- **Konzeptioneller Entwurf:** In dieser Phase werden die Sichten modelliert und in ein Gesamtschema integriert. Dafür werden meist Entity-Relationship-Diagramme verwendet (ER-Modell)
- **Logischer Entwurf:** Hier werden die grafischen Darstellungen (ER-Modell) in das Datenmodell des Ziel-DBS transformiert und die gesamte Datenbank wird so aufbereitet, dass eine effektive Speicherung möglich ist. (Normalisierung)
- **Entwurf der Verteilung im Netz:** Ist eine Datenbank verteilt so ist ein Entwurf für die Verteilung der Datenbank erforderlich.
- **Physischer Entwurf/Implementiertung:** Die Datenbank wird mithilfe des DBMS erstellt. Für relationale DBS geschieht dies mit SQL.
- **Test und Validation:** Die Datenbank und die erstellten Abfragen werden nun getestet und die Ergebnisse werden auf ihre Gültigkeit bezüglich der Anforderungen geprüft (validiert).
- **Anwendung und Wartung:** In dieser Phase muss die Datenbank ständig gewartet werden.

## Entwicklung von Datenbanken
## Teile des Datenbanksystems und seine Funktionen und Aufbau
- **Sicherung der Integrität**

    Durch Integritätsbedingungen kann die logische Richtigkeit der Daten gewahrt werden

- **Datensicherung**

    Mithilfe des Logbuchs kann das DBMS nach einem Absturz jeglicher Art wieder in einen konsistenten Zustand gebracht werden.

- **Synchronisation**

    Das DBMS hat die Aufgabe, parallel ablaufende Transaktionen der Benutzer zu synchronisieren, d.h. die Zugriffe so zu verwalten, dass die Integrität der Datenbank gewahrt bleibt.

- **Zugriffssteuerung**

    Das DBMS hat Funktionen die es ermöglichen bestimmten Benutzern nur bestimmte Sichten und Rechte zu geben.

- **Data Dictionary**

    Der Anwender kann über das Dictionary Informationen über die Datenbank erhalten und Leistungsanalysen durchführen lassen. (z.B.: Datenbankschema, die SIchten und Zugriffsrechte)

- **Logbuch**

    Das DBS verfügt über ein extern gespeichertes Logbuch in welchem Informationen über Transaktionen enthalten sind. Mehr info unter Undo/Redo Log.


# 4. Architektur des Datenbanksystem
## Datenbankmodelle (Aufzählung und Gegenüberstellung)
### Hierarchische Datenbanken

Dieses Datenmodell wurde entwickelt um unterschiedlich lange Datensätze zu verarbeiten. Es handelt sich hier um eine Knotenstruktur bei der jeder untergeordnete Knoten von seinem übergeordneten abhängig ist. Die Struktur entspricht einer Vater-Sohn-Beziehung. 


IMS/DB von IBM ist eine hierarchische Datenbank. 

Nachdem die hierarchischen Datenbanken bis auf einzelne Nischen aus der praktischen Anwendung verdrängt wurden, finden heute mit der starken von XML ihre theoretischen Ansätze wieder eine Anwendung.

- **Vorteile:** einfache Struktur, schneller Zugriff, auch für große Datenmengen geeignet
- **Nachteile:** nachträgliche Strukturänderungen kaum möglich, setzt Kenntnisse der Struktur voraus, pro Satz nur ein Feld und eine Verknüpfung

### Netzwerkdatenbanken

Das Netzwerk Datenbankmodell besitzt keine strenge Hierarchie. Ein Datenfeld besteht aus einem Namen und einem Wert.

Es sind m:n Beziehungen möglich, d.h. ein Datensatz kann mehrere Vorgänger haben. Des Weiteren können auch mehrere Datensätze an erster Stellen stehen. Der Vorteil dieses Modell ist, das es unterschiedliche Suchwege als Lösungsweg angibt, was natürlich auch zu Problemen führen kann, wenn der Entwickler genau einen Lösungsweg benutzen will. Auch die Übersichtlichkeit verringert sich, wenn das Modell ständig weiter wächst.

Heute wird das Netzwerkdatenbankmodell als eine Art Verallgemeinerung des hierarchischen Datenbankmodells gesehen.


Beispiel: UDS (Universelle Datenbank System) von Siemens

- **Vorteile:** flexibler als hierarchische Datenbankmodelle, leistungsfähiger als relationale Datenbankmodelle, gute Integrität
- **Nachteile:** Implementierung, Erweiterung und Wartung kompliziert, wird schnell unübersichtlich, Datenstruktur bestimmt über Aufbau

### Relationale Datenbanken

Die relationale Datenbank ist die am weitesten verbreitetste. Daten werden in Tabellenform gespeichert (sog. Relationen), dazwischen können Beziehungen definiert werden (1:1, 1:n, n:m). Die grafische Darstellung der Relationen erfolgt meist im ER-Modell. Abfragesprache: SQL.


Beispiel: MySQL, MariaDB

- **Vorteile:** einfach umzusetzen, Daten bleiben weitgehend unabhängig voneinander, SQL-Fähig
- **Nachteile:** weniger leistungsfähig als andere, keine Gewährleistung für Datenintegrität, fehler- und störungsanfällig

### Spaltenorientierte Datenbanken

Spaltenorientierte Datenbanken basieren ebenfalls auf Relationen (*Tabellen),* allerdings erfolgt die physische Speicherung hier in einer anderen Form. Die Werte der Tabellen werden pro Spalte - also über ein Attribut - auf das externe Speichermedium geschrieben.

**Relationale Datenbank:** 
GW, 0023; XY, 0023; XY, 0101; XY, 6291; ME, 6291; ST, 6291

**Spaltenorientierte Datenbank:** 
GW, XY, XY, XY, ME, ST; 0023, 0023, 0101, 6291, 6291, 6291


Beispiel: Apache Cassandra

- **Vorteile:** Geschwindigkeitsvorteile bei der Auswertung von Daten, schnellere Bearbeitung wenn du ein Attribut geändert werden muss. Sie liefern schnelle Auswertungen trotz enormer Datenmengen, da sie, im Gegensatz zu reihenorientierten DBMS sofort die relevanten Blöcke lesen können, ohne den kompletten Datensatz lesen zu müssen.
- **Nachteile:** langsamere Lesedauer wenn kompletter Datensatz gelesen werden muss

### Dokumentorientierte Datenbanken

Zugehörige Informationsmengen werden in ein Dokument gespeichert. Die Daten innerhalb eines Dokuments werden in Feldname-Wert-paaren abgespeichert. Dabei muss nicht jedes Feld in jedem Dokument vorhanden sein und einzelne Felder können in unterschiedlichen Dokumenten eine unterschiedliche Anzahl von Werten besitzen.


Beispiel: Elasticsearch, HCL Notes

- **Vorteile:** Dokumentenorientierte Datenbanken sind sehr viel flexibler: Die Struktur der einzelnen Dokumente muss nicht konsistent sein. Auch große unstrukturierte Datenmengen können so in der Datenbank untergebracht werden.; 

Außerdem ist es einfacher, neue Informationen einzugliedern: Während man bei einer relationalen Datenbank einen neuen Informationspunkt in alle Datensätze einfügen muss, reicht es bei einem Document Store, die Neuheit in nur wenige Datensätze zu integrieren. In weitere Dokumente kann der zusätzliche Inhalt eingefügt werden – muss er aber nicht.
- **Nachteile:** Referenzen passen nicht in das Konzept, also keine Beziehungen sonst sehr komplex und sperrig.

### Objektorientierte Datenbanken

Objektorientierte Datenbanken (OODB) sind nach dem Paradigma der objektorientierte Programmierung entwickelt worden. Ziel ist es ein DBS zu haben, in welchem Objekte unserer Umwelt mit ihren Eigenschaften und ihrem Verhalten nachgebildet und ohne großen Aufwand gespeichert werden können.  OODB's sind nur wenig verbreitet.

Jedes Objekt der DB enthält:

- Dateninformationen (Attribute)
- Verweise auf andere Objekte
- Operationen (Methoden)

Beispiel: db4o

- **Vorteile:** Daten können flexibel repräsentiert werden, mehrfache Verwendung von Objekten möglich
- **Nachteile:** Implementierung recht kompliziert, geringe Geschwindigkeit

### Objektrelationale Datenbanken

Objektrelationale Datenbanken wurden entwickelt um die Vorteile des relationalen und des objektorientierten Modells in einem DB-Modell zu vereinigen. Es wurde das vorhandene relationale Modell genutzt, das um die objektorientierten Konzepte erweitert wurde.

Beispiel: PostgreSQL

- **Vorteile: ste fragen**
- **Nachteile:**

### NoSQL-Datenbanken

NoSQL steht für „Not only SQL“ und bezeichnet Datenbanksysteme, die einen nicht-relationalen Ansatz verfolgen. Diese Datenbanken, denen verschiedene Datenbankmodelle zugrunde liegen können, sind horizontal skalierbar und lassen sich für Big-Data-Anwendungen einsetzen.

**Was NoSQL-Datenbanken auszeichnet**

In NoSQL-Datenbanken sind die Forderungen umgesetzt, große, exponentiell wachsende Datenmengen performant zu verarbeiten sowie skalierbare, leistungsfähige und verteilte Architekturen zu unterstützen. Folgende typischen Eigenschaften zeichnen die NoSQL-Systeme aus:

- Die horizontale Skalierbarkeit,
- das Vermeiden von unnötiger Komplexität,
- eine hohe Performance und ein hoher Durchsatz,
- die Nutzung von allgemein gebräuchlicher Hardware,
- die Vermeidung von relationalen Ansätzen des Datenmappings,
- die Einfachheit in der Installation und Konfiguration von verteilten Datenbank-Clustern sowie
- die Unterstützung der aktuellen Hardwaregenerationen.

NoSQL-Datenbanken können in drei Gruppen eingeteilt werden:

- Dokumentenorientierte Datenbanken (HCL Notes)
- Graphen-Datenbanken (Neo4J)
- Key/Value-Datenbanken (Big Table, Redis)


## Datenbankmodelle (Relationales Datenbankmodell)

Das **Relationale Modell**, basierend auf der relationalen Algebra, ermöglicht es, Daten als Entitäten (2-Dimensionale Tabellen) zu speichern. Durch Fremdschlüssel können Datensätze aus verschiedenen Tabellen miteinander in **relation** gesetzt werden. Dies ermöglicht das Daten redundanzfrei gespeichert werden können und es zu keinen **Inkonsistenzen** kommt.

Nachteile bestehen in der Skalierberkeit und den Verlust der ACID-Eigenschaften dadurch (horizontale Skalierung, eventual consistency). Das feste Datenschema ist ein Nachteil bei BigData-Anwendungen, die eine hohe flexibilität benötigen.

- **Vorteile:** einfach umzusetzen, Daten bleiben weitgehend unabhängig voneinander, SQL-Fähig
- **Nachteile:** weniger leistungsfähig als andere, keine Gewährleistung für Datenintegrität, fehler- und störungsanfällig

# 5. Erweiterte Funktionalitäten
## Transaktionsverwaltung (Lock, Rollback, Probleme)

Transaktionen sind eine Gruppe von logisch zusammenhängenden Datenbankoperationen (SQL-Anweisungen), die nur gemeinsam ausgeführt werden sollen. 

Kann auf Grund eines Fehlers, einer Zugriffsverletzung oder Ähnlichem eine der Operationen nicht ausgeführt werden, dann wird keine der Operationen in der Transaktion ausgeführt und der Datenbestand wird in den Ausgangszustand versetzt.

Das Datenbanksystem garantiert bei der Ausführung einer Transaktion die Einhaltung der vier grundlegenden Eigenschaften, die auch als ACID-Eigenschaften bezeichnet werden

Eine Transaktion ist eine Folge von Operationen, die auf einer Datenbank ausgeführt werden. Darunter fallen `INSERT`, `UPDATE`, `DELETE` bzw. DQL und DML Operationen.

Eine Transaktion startet mit einem konsistenten (richtigen, wirklichen) Zustand der Datenbank. Anschließend werden die Operationen, die der User mit der Datenbank durchgehen möchte, durchgeführt.

1. Alle Operationen werden erfolgreich ausgeführt und können mittels eines Commits in der Datenbank dauerhaft gespeichert werden.
2. Sollte mindestens eine Operation innerhalb einer Transaktion fehlerhaft sein, werden alle Operationen innerhalb der Transaktion mittels eines Rollbacks auf den Status bevor die Transaktion gestartet wurde zurückgesetzt.

### Anomalien
Anomalien in Datenbanken treten bei einer **nicht existierenden oder fehlerhaften Normalisierung** auf.

Lost Update & dirty read

lost update: man liest etwas ein was veraltet ist (bzw noch nicht commited wurde)

dirty read: rollback verpasst und rechnet mit dem wert vor dem rollback

Lösung: Sperrmechanismen wie Lesesperre, Schreibsperre

## Benutzerverwaltung und Zugriffsrechte
MariaDB verwaltet die Benutzernamen in der Tabelle *user* in der Datenbank *mysql*. Um einen neuen Benutzer anzulegen verwendet man in der Regel spezielle Befehle *(CREATE USER und GRANT)* welche den Server veranlassen, die Tabelle *user* zu bearbeiten.

Beim Anlegen des Benutzers muss neben dem Benutzernamen zusätzlich angegeben werden von welchem Hosts im Netzwerk der Zugriff erfolgen darf.

```jsx
CREATE USER 'user'@'host' IDENTIFIED BY 'passwort';
```

- Der Hostname bezeichnet den Netzwerknamen des Computers, von dem aus der Zugriff erfolgen soll.
    - % → Alle Computer im Netzwerk
    - [localhost](http://localhost) → Lokaler Computer, auf dem der MariaDB-Server installiert ist.
    - [db.testserver.de](http://db.testserver.de) → Computer mit dem Domainnamen db.testserver.de
    - %.[testserver.de](http://testserver.de) → Computer, deren Domain auf testserver.de endet
    - server → Computer mit dem Netzwerknamen *server*.

### Zugriffsrechte mit GRANT definieren

```jsx
GRANT rechteliste ON datenbankobjekt TO benutzername [WITH GRANT OPTION];
```

- Die Anweisung beginnt mit dem Schlüsselwort Grant
- Danach folgt die Angabe des zu vergebenden Rechts. (Bei mehreren mit Kommata trennen)
    - ALL → Gewährt alle Rechte
    - DELETE → Recht zum Löschen von Datensätzen
    - EXECUTE → Ausführungsrecht für Stored Procedures
    - INSERT → Recht zum Einfügen neuer Datensätze
    - SELECT → Leserecht
    - UPDATE → Recht zum Ändern von Datensätzen
- Nach dem Schlüsselwort ON folgt der Name des Datenobjektes (z.B.: tabelle_schueler)
- Am Ende folgt nach dem Schlüsselwort TO der Benutzername.
- Mit dem optionalen Schlüsselwort `WITH GRANT OPTION` kann der Benutzer seine Rechte an andere weitergeben.

Datenbankobjekte **können** mit der *-Notation definiert werden →  `GRANT rechte ON *.* TO ...` → Die betreffenden Rechte gelten für alle Datenbanken und Tabellen. Diverse Möglichkeiten wie `datenbank.*` sind natürlich auch gültig.

### Zugriffsrechte mit REVOKE entfernen

```jsx
REVOKE rechteliste ON datenbankobjekt FROM benutzername;
```

### Erteile Privilegien entfernen

Möchte man einem Benutzer das Privileg entfernen anderen seine Rechte weiterzugeben (`WITH GRANT OPTION`) macht man dies wie folgt.

```jsx
REVOKE GRANT OPTION FOR ALL ON tabellenname FROM benutzername CASCADE;
```

- Mit der Revoke-Anweisung und der Option `GRANT OPTION FOR ALL` werden dem Benutzer an dieser Stelle alle Rechte für die Tabelle entzogen. Mit der Option `CASCADE` wird auch allen Benutzern, die das Privileg von dem Benutzer erhalten haben, das Privileg entzogen.

## Indizes

Ein Index wird für ein bestimmtes Datenfeld oder auch mehrere Datenfelder angelegt, nach denen häufig sortiert oder in denen häufig gesucht wird. Er ähnelt dem
Inhaltsverzeichnis eines Buches und ist in Form eines B*-Baumes aufgebaut. Das
Durchsuchen der Datensätze wird durch einen Index zum Teil erheblich beschleunigt. Für einen Schlüssel wird vom DBMS meist automatisch ein Index erstellt. Für
eine Tabelle können Sie mehrere Indizes definieren.

Indizes erleichtern die Suche nach Datensätzen, insbesondere bei sehr großen Datenmengen.
Standardmäßig durchsucht das Datenbanksystem bei der Suche nach bestimmten Werten in
einer oder mehreren Spalten nacheinander alle Datensätze einer Tabelle. Existiert für eine oder
mehrere Spalten jedoch ein Index, dann wird dieser zur Suche herangezogen und beschleunigt
die Suche.

- vor allem sinnvoll wenn es viele Datensätze gibt bzw. die Tabelle sehr groß ist.

```jsx
CREATE INDEX indexname ON tabellenname (datenfeldname);
DROP INDEX indexname ON tabellenname
```
## Backup und Restore

### **Full Backup**

Bei einer Vollsicherung werden jedes Mal alle zu sichernden Daten in einer Sicherungsdatei auf dem Zieldatenträger gespeichert. Dadurch sind alle gesicherten Daten in nur einer Datei enthalten, was die Verwaltung der Backups vereinfacht.

**Vorteile:** 

- Die Erstellung bzw. Wiederherstellung der Sicherung ist schneller als eine differentielle oder inkrementelle Sicherung.
- Die Handhabung ist einfacher, da nur eine Datei für eine Wiederherstellung benötigt wird.

**Nachteile:** 

- Eine regelmäßig durchgeführte Vollsicherung benötigt mehr Speicherkapazität, als eine differentielle oder inkrementelle Sicherung

### Inkrementelle Datensicherung

Beim inkrementellen Backup wird eine Vollsicherung des Datenbestandes durchgeführt. Anschließend werden Sicherungen zum letzten Backup gemacht. Das bedeutet, dass beim ersten Mal eine Sicherung der Veränderungen seit dem letzten Backup (egal ob inkrementell oder Vollbackup) gemacht werden. Zur Wiederherstellung des Datenbestandes werden alle Bänder benötigt. Fehlt eines der Bänder bzw. ist eine Sicherung nicht vorhanden, ist eine Wiederherstellung des gesicherten Datenbestands nicht möglich.


**Vorteile:**

- Eine regelmäßig durchgeführte inkrementelle Sicherung benötigt weniger Speicherkapazität, als eine Vollsicherung oder differentielle Sicherung.

**Nachteile:**

- Eine Wiederherstellung der Sicherung ist langsamer, als die der Voll- oder differentiellen Sicherung.
- Die Handhabung ist komplizierter, da alle Dateien der „Sicherungskette“ für eine Wiederherstellung benötigt werden.

### Differentielle Datensicherung

Das differentielle Backup ist dem inkrementellen Backup sehr ähnlich. Es wird erneut eine Vollsicherung gemacht. Anschließend werden die Veränderungen zum letzten Vollbackup gesichert. Demnach ist zur Wiederherstellung des Datenbestandes das Vollbackup und das gewünschte differentielle Backup notwendig.

**Vorteile:**

- weniger Speicherbedarf als bei Vollbackup, aber mehr als beim inkrementellen Backup
- Vollbackup und die differentielle Sicherung zum gewünschten Zeitpunkt notwendig

**Nachteile:**

- Eine Wiederherstellung der Sicherung ist langsamer als die der Vollsicherung.
- Die Handhabung ist komplizierter, da zwei Dateien für eine Wiederherstellung benötigt werden.
- Dateien, die einmal verändert werden, müssen bei jedem differentiellen Backup neu gesichert werden. Dadurch hat man ein erhöhtes Datenaufkommen.

Die optimale Backup-Methode muss je nach Anwendungsfall gewählt werden. Häufig macht eine Kombination aus allen drei Methoden am meisten Sinn. Zum Beispiel kann ein wöchentliches Vollbackup erfolgen und zusätzlich jeden Tag ein inkrementelles Backup, um das Datenaufkommen niedrig zu halten und mit den entsprechenden Sicherungen die Daten schnell und zu verschiedenen Zeitpunkten wieder herzustellen.

Systempuffer flashen weil dort die letzten Befehle gespeichert werden

Snapshot: Ein Snapshot ist ein virtuelles Abbild einer Festplatte oder eines Systems, was zu bestimmten Zeitpunkten („Momentaufnahme“) als Backup ausgeführt wird.
## Content Management Systeme

Contentmanagementsysteme sind Programme die es erlauben, auch ohne Programmierkentnisse und in wenig Zeit, komplexe Webseiten wie Blogs oder E-Commerce Systeme zu erstellen. In deren Hintergrund agiert meist eine Relationale Datenbank wie MySQL. Weit verbreitete CMS wie Wordpress bieten auch eine Vielzahl an Plugins an, die das bestehende System um zusätzliche Funktionalität erweitern. Solche Systeme zu benutzen bringt meist einige Vorteile mit sich, wie: - eine erhöhte Sicherheit, da eine große Community aber auch Firmen diese kontinuierlich testen. - eine Kostenreduktion, da es keine eigenen Entwickler dafür braucht und wenn men ein FOSS System wählt, auch keine gebühren zahlen muss. - eine höhere Flexibilität, da man Plugins einfach hinzufügen/löschen kann und nur Basisfunktionalität hardcoded ist.

Ein Content Management System ist eine Datenbank gesteuerte/betriebene Management Software für dynamische Webseiten. Beispiele für solche CMS sind WordPress, Joomla oder Typo 3. Vorteile an solchen Seiten sind das man z.B. wie bei WordPress einzelne Rollen (Redaktionssystem) vergeben kann, wie der Admin darf löschen aber der Mitarbeiter darf nur Seiten beschreiben. Weiters werden Templates vorgegeben die man einfach mit Content befüllen kann. 

**statische Webseite:** Webseiten mit Inhalt am Server, welche einzeln als HTML-Datei gespeichert wird.  

**dynamische Webseite:** Webseite rennt auch auf einem Server der mit einer Datenbank verknüpft ist. Zugegriffen wird da über eine Oberfläche wie WordPress mit PHP, JavaScript und HTML.