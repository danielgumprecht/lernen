## ER-Modell, Teile, Bestandteile, ER-Modell erstellen
Das ER-Modell ist ein grafisches Hilfsmittel für den Datenbankentwurf. Die Grundbausteine des ER-Modells sind Entities und Relationships. 

## Primärschlüssel und Fremdschlüssel beschreiben
- Primärschlüssel ist dazu da, in einer Tabelle einen Datensatz eindeutig identifizieren zu können. 
- Ein Fremdschlüssel ist ein Attribut in einer Relation, welches eine Beziehung zu einem Schlüsselfeld einer anderen Relation herstellt.

## Arten von Primärschlüsseln
Man unterscheidet zwischen eindeutigen Primärschlüsseln und zusammengesetzten Primärschlüsseln.

## Einsatz von Schlüsseln in Zwischentabellen
Zwischentabellen kommen dann zum Einsatz, wenn eine n:m Beziehung vorliegt. Eine solche Zwischentabelle besiztz im Normalfall mindestens 2 Attribute, die als Fremdschlüssel auf die jeweiligen Daten der Tabellen n und m verweisen.

## Kardinalitäten, Beziehungsarten, Beschreibe wie Beziehungsarten umgesetzt sind
- Die Kardinalität legt fest wie viele Entitäten zueinander in Beziehung stehen können

## Speziele Beziehungsformen (is a, generalisierung, Rekursion)
- Genau zwei Entities sind miteinander verbunden (Binär)
- Genau drei Entities sind miteinander verbunden (Ternär)
- Mehrere Entities sind miteinander verbunden (n-är)
- Eine Entity steht mit sich selbst in Beziehung (Rekursiv)

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

### Normalform 4 und 5

## Entwurfsphasen

### Anforderungsanalyse
- Zusammentragung aller Anforderungen an die neue Datenbank
- Klassifizierung nach bestimmten Kriterien
- Festlegung was zu speichern ist und wie die Daten zu bearbeiten sind
  
### Konzeptioneller Entwurf
- Festlegung des DBS vor dem logischen Entwurf

### Logischer Entwurf
- Umsetzung des konzeptionellen Schemas in das Datenmodell des Datenbanksystems
- Transformationsregeln
- Normalisierung des Datenbankschemas

#### Vereinfachung
- Optimierung auf zum Beispiel bevorzugte Abfragen mithilfe von Indizes

### Physischer Entwurf und Implementierung
- Definition des internen Schemas
- Festlegung geeigneter Speicherstrukturen und Zugriffsmechanismen
- Verbessertes Laufzeitverhalten durch einen effizienten Zugriff
- Implementierung des internen, komplementären und externen Schemas
- Definition von Relationen und Views (bei Relationalen Datenbanksystemen)
- Festlegung der Zugriffsrechte

## DDL
Die DDL (Data Definition Language) beschreibt das Datenschema (konzeptionelle Ebene) in der Daten gespeichert werden sollen. Das inkludiert den Aufbau der Tabellen mit den jeweiligen Datentypen, sowie Constraints, also Bedingungen, die beim hinzufügen von Daten überprüft werden.

## Constrains 
Zu Constraints zählen z.B. ```NOT NULL``` und ```PRIMARY KEY```. Wenn Constraint-Bedingungen nicht erfüllt werden, wird eine Felermeldung ausgegeben (exception).

Constraints können entweder bei der Definition angegeben werden oder durch ein ```ALTER``` später hinzugefügt.

## Sprachfamilien mit Beispielen und Creates, mit Constrains
#### DQL Abfrage Sprache (Data Query Language)
- Vertikale Selektion: Beschränkung der Attribute die im Ergebnis der Abfrage angezeigt werden. (SELECT)
- Horizontale Selektion: Beschränkung der Datensätze die dem User beim Ergebnis angezeigt werden solle. (WHERE)

#### DML (Data Manipulation Language)
Mit der DML werden Daten manipuliert
- INSERT: Daten in die Datenbank einfügen
- UPDATE: Daten in der Datenbank bearbeiten
- DELETE: Daten innerhalb der Datenbank bearbeiten

#### DDL: (Data Definition Language)
Mit der DDL werden die Strukturen einer Relation angepasst.

## DQL Abfragen und Möglichkeiten und Beispiele SELECT schreiben können
Die DQL (Data Query Language) ist eine Teil der SQL Sprachfamilie und erlaubt die Abfrage von Daten aus einer relationalen Datenbank.

SELECT-Statements sind meist nach einem festen Schema aufgebaut, dass entweder Syntaxmäßig vorgegeben wird bzw. es sich um eine Konvention handelt.

- Attributes: Attribute nach die ausgegeben werden sollen
- Aliases: Ein Proxy auf ein Attribut
- Aggregat-Functions: z.B- ```COUNT()```, ```MIN()```, ```MAX()``` - Funktionen die Attribute als Argumente annehmen.
- Table-Name: Name der Tabelle, über die ein Select ausgeführt werden soll.
- Joins: Relationen der Tabelle, die bei der Abfrage berücksichtigt werden sollen.
- Conditions: Spezfikationen, die die Daten, die ausgegeben werden erfüllen müssen.
- Groupings: Gruppierung nach öfter vorkommenden Daten
- Grouping-Conditions: Spezifikationen die virtuelle Felder erfüllen müssen
- Order: Reihenfolge in der Daten ausgegeben werden sollen
- Pagination: Limitierung der Daten ```LIMIT 1 OFFSET 1``` (maximale Anzahl der Daten und von welchem Datensatz aus diese ausgegeben werden sollen)

## Datentypen
Jedem Attribut wird ein bestimmter Datentyp zugeordnet. Dabei unterscheidet man zwischen verschiedenen Zahlentypen (Ganzzahlig, Dezimal), Zeichenketten (Text, Varchar), Datumstypen und Boolean (true, false).

## JOIN, Mengenschreibweise


## Vergleich Join zu Sub Select


## Gruppierung und Aggregatsfunktion
- Gruppierungen werden dann eingesetzt, um Datensätze nach einem oder mehreren Kriterien zusammenzufassen. Dies geschieht mittels des `GROUP BY` Statements.
- Aggregatfunktionen führen Berechnungen über alle oder ausgewählte Datensätze durch. Beispiele sind: `MAX`, `MIN`, `AVG` und `COUNT`

## Lebenszyklus 


## DBMS
Das Datenbankmanagementsystem verwaltet die Datenbank und regelt alle Zugriffe darauf. 

## ACID und DBMS
### Atomicy
Eine Transaktion wird entweder komplett ausgeführt oder garnicht. Bei Fehlern wird alles rückgängig gemacht.

### Consistency
Die Datenbank befindet sich durch die Integritätsbedingungen in einen Konsistenten Zustand.

### Isolation
Mehrere gleichzeitige Transaktionen stören sich nicht gegenseitig.

### Durability
Das Ergebnis einer Transaktion ist dauerhaft.

## Aufgaben vom Logbuch
- Redo Log - Speicherung aller abgeschlossenen Transaktionen
- Undo Log - Speicherung aller nicht abgeschlossenen Operationen einer Transaktion

Stromausfall - Mit dem Undo Log

## 3 Ebenen Model + Sprachfamilien zuordnen


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
- Ein Datenbanksystem besteht aus einer Anzahl von Datenbanken und den Datenbankmanagementsystem.
- Das Datenbankmanagementsystem ist die Schnittstelle zwischen der Datenbank und deren Benutzern.

## Breitstellung von Daten DBMS
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

#### Vorteile
- Einfaches Datenmodell
- Hohe Datenkonsistenz
- Geringe Datenredundanz
- Einheitliche Abfragesprache
- Mengenorientierte Datenverarbeitung

#### Nachteile
- Tabellarische Abbildung vom Daten
- Kein hierarchisches Schema
- Segmentierung von Daten
- Schlechtere Performance zu NoSQL

## Physische Struktur 
In welcher Form werden die Daten gespeichert und wie soll darauf zugegriffen werden?

## Transaktionen 
Eine Folge von mehreren Operationen die nur gemeinsam ausgefüllt werden können.  

## Anomalien
Das Fehlverhalten der Datenbank durch Verletzung der Regel every information once. Dadurch ist nicht mehr erkennbar welche Tabelle oder Spalte den richtigen Inhalt enthält

## Locks
#### Isolation Level
Der Grad der Parallelität von Transaktionen. Bei einem höheren grad können weniger Probleme mit der Konsistenz entstehen.

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
Durch den Datenbank Index wird die Suche und das sortieren nach bestimmten Feldern beschleunigt. Ein Index besteht aus einer Ansammlung von verweisen

## Content Mangement Systeme
Eine Software zur gemeinschaftlichen Erstellung digitaler Inhalte. Meistens zur Verwendung in Webseiten. Bei volldynamischen Systemen wird erst bei der Abfrage ein Format generiert.

## Backup
#### Full Backup
- Volles Backup

#### Inkrementelles Backup
- Aufeinander aufbauend
- Veränderungen seit dem letzen Backup werden gesichert
- Zur Wiederherstellung sind alle Backups seit dem letzen Vollbackup notwendig

#### Differentielles Backup
- Zur Wiederherstellung ist das Vollbackup und das gewünschte Differenzielle Backup notwendig