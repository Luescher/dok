# agi AV_KASO Abgleich
Verantwortlicher: Andrea Lüscher

## Beschreibung
Die Katasterschätzung verwaltet die Grundstücke inkl. der Grundstücksflächen in einer DB (KASO von aXenta). Die Fläche ist einer der Faktoren, mit welchem der Katasterwert errechnet wird. Die Nachführung der Grundstücke erfolgt mittels analoger Anzeige vom Grundbuch.
Die Grundstücksfläche wird aus dem Grenzverlauf, der in der amtlichen Vermessung (AV) festgehalten ist, errechnet. Die Fläche wird von der amtlichen Vermessung an das Grundbuch übergeben und das Grundbuch teilt die Fläche mittels Anzeige der Katasterschätzung mit.
Die Grundstücksdaten der Katasterschätzung, des Grundbuchs und der amtlichen Vermessung sollten identisch sein. Aufgrund des Vergleichs vom August 2016 hat sich gezeigt, dass die Daten der Katasterschätzung und der amtlichen Vermessung nicht identisch sind.
Das Monitoring „Abgleich KASO-AV“ ist ein Arbeitstool für die Katasterschätzung, damit die Daten der KASO nachgeführt resp. bereinigt werden können.

## Erfassung
Die Grundstücksflächen werden von der Katasterschätzung in einer Oracle-DB KASO von aXenta erfasst/verwaltet.
### DB Schema
Edit-DB: `agi_av_kaso_abgleich_import`
### Schnittstellen
Die Daten der Katasterschätzung werden mittels dem Gretljob `agi_av_kaso_abgleich_pub` von deren Oracle-DB in die Edit-DB kopiert.
Anschliessen werden die Daten so umgebaut (verglichen), dass lediglich die Einträge in der Differenztabelle aufgeführt werden, bei welchen die KASO-Daten nicht mit den AV-Daten übereinstimmen. Folgendes wird geprüft:

* Flächendifferenz zwischen AV und KASO
* unterschiedliche Grundstücksarten in AV und KASO
* Grundstück nur in der AV vorhanden
* Grundstück nur in KASO vorhanden

Die Zugriffsdaten für Oracle-DB KASO sind im KeePass abgelegt.

## Publikation
Die Differenztabellen werden für die Katasterschätzung im Web GIS Client mittels einem Objektblatt (Excelliste) visualisiert. 
### DB Schema
Pub-DB: `agi_av_kaso_abgleich_pub`
### Datenumbau
Die Daten werden mittels einem Gretljob von der Edit-DB in die Pub-DB geschrieben.

Gretljob ausführen: https://gretl.so.ch/job/agi_av_kaso_abgleich_pub/

Gretljob konfigurieren: https://github.com/sogis/gretljobs/tree/master/agi_av_kaso_abgleich_pub

### Web GIS Client
geschützte Layergruppe: `ch.so.agi.av_kaso_abgleich*`

Objektblatt: Template im AGDI `av_kaso_abgleich_differenzen`

## Betriebshandbuch
`H:\BJSVW\Agi\GDI\Betrieb\AV_Kaso_Abgleich\Betriebshandbuch.doc`
