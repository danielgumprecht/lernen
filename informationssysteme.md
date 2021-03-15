# Meine INSY Themenübersicht

## ER-Modell, Teile, Bestandteile, ER-Modell erstellen
Das ER-Modell ist ein grafisches Hilfsmittel für den Datenbankentwurf. Die Grundbausteine des ER-Modells sind Entities und Relationships.

## Primärschlüssel und Fremdschlüssel beschreiben
- Ein Primärschlüssel identifiziert einen Datensatz in einer Tabelle eindeutig.
- Ein Fremdschlüssel ist ein Attribut in einer Relation, das eine Beziehung zu einem Schlüsselfeld einer anderen Relation herstellt.
- Ein Fremdschlüssel bezeichnet die Übereinstimmung eines Datenfeldes in einer Tabelle mit dem Primärschlüssel einer anderen Tabelle.

## Arten von Primärschlüsseln
Man unterscheidet zwischen eindeutigen, zusammengesetzten und künstlichen Primärschlüsseln.

## Einsatz von Schlüsseln in Zwischentabellen
Zwischentabellen kommen dann zum Einsatz, wenn eine n:m Beziehung vorliegt. Eine solche Zwischentabelle besitzt im Normalfall mindestens 2 Attribute, die als Fremdschlüssel auf die jeweiligen Daten der Tabellen n und m verweisen.

## Kardinalitäten
Die Kardinalität legt fest wie viele Entitäten zueinander in Beziehung stehen können

## Spezielle Beziehungsformen (is a, generalisierung, Rekursion)
- Genau zwei Entities sind miteinander verbunden (Binär)
- Genau drei Entities sind miteinander verbunden (Ternär)
- Mehrere Entities sind miteinander verbunden (n-är)
- Eine Entity steht mit sich selbst in Beziehung (Rekursiv)
- Teilmengenbeziehung (Generalisierung)

## Normalformen mit Beispiel
### Normalform 1
- Ein Gebilde aus Zeilen und Spalten
- In jeden Datensatz sind nur Daten die zu einem Objekt der realen Welt gehören
- Jeder Datensatz kommt nur einmal vor
- In jeder Spalte befinden sich nur Daten die einem Attribut entsprechen
- Das Attribut kommt nur einmal in der Relation vor
- Für jedes Attribut ist nur ein Wert eingetragen

### Normalform 2

- Wenn die erste Normalform erfüllt ist
- Wenn jedes Nicht-Schlüsselfeld vom ganzen Primärschlüssel abhängig ist
- Wenn Datenfelder vom gesamten Schlüssel funktional abhängig sind

### Normalform 3

- Alle Datenfelder sind nur vom gesamten Schlüssel abhängig
- Es gibt untereinander keine Abhängigkeiten
- Wenn ein nicht Schlüsselfeld über ein anderes Nicht-Schlüsselfeld identifizierbar ist, wird von Transistiver Abhängigkeit gesprochen

## Entwurfsphasen



### Anforderungsanalyse

- Zusammentragung aller Anforderungen an die neue Datenbank
- Klassifizierung nach bestimmten Kriterien
- Festlegung was zu speichern ist und wie die Daten zu bearbeiten sind

### Konzeptioneller Entwurf

- Festlegung des Datenbanksystems

### Logischer Entwurf

- Umsetzung des konzeptionellen Schemas in das Datenmodell des Datenbanksystems
- Transformationsregeln
- Normalisierung des Datenbankschemas

### Vereinfachung

- Optimierung auf zum Beispiel bevorzugte Abfragen mithilfe von Indizes

### Physischer Entwurf und Implementierung

- Definition des internen Schemas
- Festlegung geeigneter Speicherstrukturen und Zugriffsmechanismen
- Verbessertes Laufzeitverhalten durch einen effizienten Zugriff
- Implementierung des internen, komplementären und externen Schemas
- Definition von Relationen und Views (bei Relationalen Datenbanksystemen)
- Festlegung der Zugriffsrechte

## DDL



Die Data Definition Language beschreibt die konzeptionelle Ebene, in der Daten gespeichert werden sollen. 

- Aufbau der Tabellen mit den jeweiligen Datentypen
- Constraints, also Bedingungen, die beim hinzufügen von Daten überprüft werden

## Constrains



Zu Constraints zählen `NOT NULL` und `PRIMARY KEY`. Wenn Constraint-Bedingungen nicht erfüllt werden, wird eine Fehlermeldung ausgegeben (exception).

Constraints können entweder bei der Definition angegeben werden oder durch ein `ALTER` später hinzugefügt.

## Sprachfamilien mit Beispielen und Creates, mit Constrains



### DQL Abfrage Sprache (Data Query Language)

- Vertikale Selektion: Beschränkung der Attribute die im Ergebnis der Abfrage angezeigt werden. (SELECT)
- Horizontale Selektion: Beschränkung der Datensätze die dem User beim Ergebnis angezeigt werden solle. (WHERE)

### DML (Data Manipulation Language)

Mit der DML werden Daten manipuliert 

- INSERT: Daten in die Datenbank einfügen
- UPDATE: Daten in der Datenbank bearbeiten
- DELETE: Daten innerhalb der Datenbank löschen

### DDL (Data Definition Language)

Mit der Data Definition Language werden die Strukturen einer Relation angepasst.

## DQL Abfragen und Möglichkeiten und Beispiele SELECT schreiben können



Mit der Data Query Language kann man Daten aus einer relationalen Datenbank abfragen

```sql
SELECT [Attributes][Aliases][Aggregat-Functions] 
FROM [Table-Name] [Joins] 
WHERE [Conditions] [Groupings] [Grouping-Conditions (HAVING)] [Order] [Pagination]
```

- Attributes: Attribute nach die ausgegeben werden sollen
- Aliases: Ein Proxy auf ein Attribut
- Aggregat-Functions: z.B. `COUNT()`, `MIN()`, `MAX()` - Funktionen die Attribute als Argumente annehmen.
- Table-Name: Name der Tabelle, über die ein Select ausgeführt werden soll.
- Joins: Relationen der Tabelle, die bei der Abfrage berücksichtigt werden sollen.
- Conditions: Spezfikationen, die von ausgegebenen Daten erfüllt werden müssen
- Groupings: Gruppierung nach mehrmals vorkommenden Daten
- Grouping-Conditions: Spezifikationen die virtuelle Felder erfüllen müssen
- Order: Reihenfolge in der Daten ausgegeben werden sollen
- Pagination: Limitierung der Daten

## Datentypen



Beim Erstellen einer Tabelle muss für jedes Datenfeld ein Datentyp angegeben werden. Der verwendete Datentyp entscheidet, ob in einem Feld Zahlen, Zeichenketten oder andere Daten gespeichert werden.

## JOIN, Mengenschreibweise



### INNER JOIN

Der INNER JOIN führt Datensätze aus der linken und rechten Tabelle zusammen, wenn die angegebenen Kriterien alle erfüllt sind

### LEFT JOIN

Der Datensatz aus der linken Tabelle kommt in das Ergebnis. Und wenn der Datensatz der rechten Tabelle den Kriterien entspricht wird er entsprechend in den Spalten eingetragen ansonsten bleiben die Spalten leer

### RIGHT JOIN

Der Datensatz aus der rechten Tabelle kommt in das Ergebnis. Und wenn der Datensatz der linken Tabelle den Kriterien entspricht wird er entsprechend in den Spalten eingetragen ansonsten bleiben die Spalten leer

### FULL OUTER JOIN

Jeder Datensatz der linken und rechten Tabelle kommt in die Ergebnismenge. Wenn sich über das Kriterium ein passender Partner findet, werden beide zusammengefügt. Wenn nicht dann bekommt die andere seite NULL ausgefüllt.

## Vergleich Join zu Sub Select



## Gruppierung und Aggregatsfunktion



- Gruppierungen werden dann eingesetzt, um Datensätze nach einem oder mehreren Kriterien zusammenzufassen. Das funktioniert mit dem `GROUP BY` Statement.
- Aggregatfunktionen führen Berechnungen über alle oder ausgewählte Datensätze durch. Beispiele sind: `MAX`, `MIN`, `AVG` und `COUNT`

## Lebenszyklus



1. Anforderungsanalyse - Ermittlung von Datenobjekten, Vorgängen und Randbedingungen
2. Konzeptioneller Entwurf - Modellierung der Sichten in ein ER-Modell
3. Logischer Entwurf - Transformation vom ER-Modell in ein Datenmodell
4. Entwurf der Verteilung im Netz
5. Physischer Entwurf - Erstellung der Datenbank mit einem Datenbanksystem
6. Test und Validation - Testen der Datenbank und der Abfragen
7. Anwendung und Wartung

## DBMS



Das Datenbankmanagementsystem verwaltet die Datenbank und regelt alle Zugriffe darauf.

Weitere Aufgaben:

- Sicherung der Integrität der Daten
- Daten bereitstellen
- Datensicherung
- Synchronisation zwischen Benutzern
- Zugriffsrechte bestimmen
- Logbuch verwalten

## ACID und DBMS



- Atomicy - Eine Transaktion wird entweder komplett ausgeführt oder garnicht. Bei Fehlern wird alles rückgängig gemacht.
- Consistency - Die Datenbank befindet sich durch die Integritätsbedingungen in einen konsistenten Zustand.
- Isolation - Mehrere gleichzeitige Transaktionen stören sich nicht gegenseitig.
- Durability - Das Ergebnis einer Transaktion ist dauerhaft.

## Aufgaben vom Logbuch



- Redo Log - Speicherung aller abgeschlossenen Transaktionen
- Undo Log - Speicherung aller nicht abgeschlossenen Operationen einer Transaktion

Stromausfall - Mit dem Undo Log kommt man wieder in den letzten konsistenten Zustand

Datenverlust - Mit dem Redo Log kommt man nach einspielen des letzten Backups wieder auf den letzten Stand

## 3 Ebenen Modell und Sprachfamilien zuordnen



Auf dem 3 Ebenen Modell werden die Sichtweisen auf einen Datenbestand dargestellt.

### Externe Ebene (DQL, DML)

- Darstellung der Daten die in einzelnen Anwendungen benötigt werden
- In Benutzeransichten werden nur die Daten angezeigt die ein Benutzer auch sehen darf
- Benutzer dürfen auf Daten zugreifen und diese auch bearbeiten

### Konzeptionelle Ebene (DDL)

- Zusammenfassung aller Daten eines Anwendungsbereichs die gespeichert werden sollen
- Logische Gesamtansicht aller Daten und Zusammenhänge

### Interne Ebene (DCL)

- Beschreibt die Organisation und Zugriffsmöglichkeiten der Daten auf den Speichermedien
- Physische Beschreibung (Datenorganisation im Speicher)

## Vorteile von Datenbank gegebüber File Speicherung



- Daten Strukturiert abspeichern und abfragen
- Integrität der Daten bleibt gesichert
- Vereinfachte Filterung der Daten

## Vortile DBMS



- Auch bei hoher Datenredundanz geringer Aufwand (wenn richtig konfiguriert)
- Vermeidung von Inkonsistenzen (wenn richtig konfiguriert)
- Erleichterter Mehrbenutzerbetrieb
- Erleichterte Zugriffverwaltung
- Sicherung der Integrität
- Datensicherung
- Synchronisation
- Zugriffsteuerung

## Teile des DBMS



- Sicherung der Integrität - Durch Integritätsbedingungen kann die logische Richtigkeit der Daten gewahrt werden
- Datensicherung - Mithilfe des Logbuchs kann das DBMS nach einem Absturz wieder in einen konsistenten Zustand gebracht werden.
- Synchronisation - Die Zugriffe werden so verwaltet, dass die Integrität der Datenbank gewahrt bleibt.
- Zugriffssteuerung - Benutzern nur bestimmte Sichten und Rechte geben.
- Data Dictionary - Der Anwender kann über das Dictionary Informationen über die Datenbank erhalten und Leistungsanalysen durchführen lassen. (z.B.: Datenbankschema, die Sichten und Zugriffsrechte)
- Logbuch

## Breitstellung von Daten DBMS



- Ein Datenbanksystem besteht aus einer Anzahl von Datenbanken und den Datenbankmanagementsystem.
- Das Datenbankmanagementsystem ist die Schnittstelle zwischen der Datenbank und deren Benutzern.

## Datenbankmodelle vergleichen



- Hierachische Datenbanken
- Netzwerkdatenbanken
- Relationale Datenbanken
- Spaltenorientierte Datenbanken
- Dokumentorientierte Datenbanken
- Objektorientierte Datenbanken
- Objektrelationale Datenbanken
- NoSQL Datenbanken

## Relationales Modell Vor und Nachteile, Aufbau



Bei einem relationalen Datenbank Modell werden die Daten in Tabellenform gespeichert, in so genannten Relationen. Zwischen den Relationen können Beziehungen definiert werden, es sind verschiedene Beziehungsarten möglich, die sich durch die Anzahl der miteinander in Beziehung stehen Datensätze unterscheiden.

### Vorteile

- Einfaches Datenmodell
- Hohe Datenkonsistenz
- Geringe Datenredundanz
- Einheitliche Abfragesprache
- Mengenorientierte Datenverarbeitung

### Nachteile

- Tabellarische Abbildung vom Daten
- Kein hierarchisches Schema
- Segmentierung von Daten
- Schlechtere Performance zu NoSQL

## Physische Struktur



Die Form in der die Daten gespeichert werden, und wie auf diese zugegriffen werden soll

- Zentralisiertes Datenbanksystem - Das gesamte Datenbanksystem ist auf einem Standort abgelegt.
- Verteiltes Datenbanksystem - Eine Menge von mehreren logisch zusammengehörigen Datenbanken die lokal getrennt voneinander sind.

## Transaktionen



Eine Folge von mehreren Operationen die nur gemeinsam ausgeführt werden können. Mit Commit können diese dauerhaft gespeichert werden.

## Anomalien



Das Fehlverhalten der Datenbank durch Verletzung der Regel every information once. Dadurch ist nicht mehr erkennbar welche Tabelle oder Spalte den richtigen Inhalt enthält

- Dirty Read - Rollback verpasst
- Lost Update - Etwas veraltetes wird eingelesen

## Locks



Mit Locks kann man bestimmte Tabellen sperren. Dabei kann man das Leserecht und das Schreibrecht einschränken. Eine Operation die im Fall von Backups notwendig ist.

## Rechtekonzept



Rechte der Benutzer können auf unterschiedlichen Ebenen vergeben werden. Der Zugriff der Benutzer kann auf ganze Datenbanken, einzelne Tabellen bis hin zu einzelnen Attributen eingeschränkt werden.

Wesentliche Rechte einer Datenbank sind 

- Lesen (SELECT)
- Einfügen oder Ändern (INSERT und UPDATE)
- Löschen (DELETE)

Weitere Rechte sind das Anlegen neuer Datenbanken und neuer Benutzer

## Benutzerveraltung mit MySQL



Aktionen auf einer Datenbank können nur mit einen angemeldeten Benutzer ausgeführt werden.

## Datenbankindex



Durch den Datenbank Index wird die Suche und das sortieren nach bestimmten Feldern beschleunigt. Ein Index besteht aus einer Ansammlung von verweisen.

## Content Mangement Systeme



Eine Software zur gemeinschaftlichen Erstellung digitaler Inhalte. Meistens zur Verwendung in Webseiten. Bei volldynamischen Systemen wird erst bei der Abfrage ein Format generiert.

## Backup



### Full Backup

- Volles Backup

### Inkrementelles Backup

- Aufeinander aufbauend
- Veränderungen seit dem letzen Inkrementellen werden gesichert
- Zur Wiederherstellung sind alle Backups seit dem letzen Vollbackup notwendig

### Differentielles Backup

- Veränderungen seit dem letzen Vollbackup werden gesichert
- Zur Wiederherstellung ist das Vollbackup und das gewünschte Differenzielle Backup notwendig