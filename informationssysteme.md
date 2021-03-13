## ER-Modell, Teile, Bestandteile, ER-Modell erstellen
Das ER-Modell ist ein grafisches Hilfsmittel für den Datenbankentwurf. Die Grundbausteine des ER-Modells sind Entities und Relationships. 

## PK, FK Schlüssel beschreiben können, Welche Arten für PK gibt es, Einsatz Schlüssel in Zwischentabellen
Primärschlüssel ist dazu da, in einer Tabelle einen Datensatz eindeutig identifizieren zu können. 

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


## Constrains 

## Sprachfamilien mit Beispielen und Creates, mit Constrains
## DQL Abfragen und Möglichkeiten + Beispiele SELECT schreiben können
## Datentypen
## JOIN, Mengenschreibweise, Vergleich Join zu Sub Select
## Gruppierung und Aggregatsfunktion
## Lebenszyklus 
## DBMS
Das Datenbankmanagementsystem verwaltet die Datenbank und regelt alle Zugriffe darauf. 

## ACID und DBM
## Aufgabe Log Buch
## 3 Ebenen Model + Sprachfamilien zuordnen
## Vorteile von Datenbank gegebüber File Speicherung

## Vortile DBMS
- Auch bei hoher Datenredundanz geringer Aufwand (wenn richtig konfiguriert)
- Vermeidung von Inkonsistenzen (wenn richtig konfiguriert)
- Erleichterter Mehrbenutzerbetrieb
- Erleichterte Zugriffverwaltung

- Sicherung der Integrität 
- Datensicherung 
- Synchronisation 
- Zugriffsteuerung

Das Datenbankmanagementsystem ermöglicht
- Das Anlegen von Datenbanken
- Die Speicherung, Änderung und Löschung der Daten
- Das Abfragen der Datenbank
- Die Verwaltung von Benutzern, Zugriffen und Zugriffsrechten

## Teile des DBMS
- Ein Datenbanksystem besteht aus einer Anzahl von Datenbanken und den Datenbankmanagementsystem.
- Das Datenbankmanagementsystem ist die Schnittstelle zwischen der Datenbank und deren Benutzern.

- Data Dictionary
- Logbuch 

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
Eine Folge von mehreren Operationen die nur gemeinsam ausgefüllt werden sollen.  

## Anomalien
Das Fehlverhalten der Datenbank durch Verletzung der Regel every information once. Dadurch ist nicht mehr erkennbar welche Tabelle oder Spalte den richtigen Inhalt enthält

## Locks
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