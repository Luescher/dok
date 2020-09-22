# afu geotope

Verantwortliche: Andrea Lüscher

## Beschreibung
Infolge einer Ablösung des veralteten Servers «srsofaioi4531», mussten die Anwendungen INGESO, IS-Boden und VSB abgelöst werden. Siehe auch Projektmanagementplan: `H:\BJSVW\Agi\Projekte\AFU\Ablösung INGESO VSB ISBoden Anwendungen\Projektmanagment\Projektmanagementplan_v01.docx`.

Die Daten werden mittels einem QGIS Projekt in der Edit-DB erfasst und in einem QGIS-Projekt mit den Daten aus der Pub-DB ausgewertet. Im Web GIS Client werden die Daten aus der Pub-DB abgebildet. Bei einer Datenänderung, werden die aktuellen Daten  von den MA des AFU via eines Greljobs von der Edit-DB in die Pub-DB geschrieben.

Damit die Erfassung und Auswertung einfacher ist, gibt es für die Erfassung und die Auswertung ein eigenes QGIS-Projekt mit einem eigenen QGIS-Profile. In diesen Profiles sind nur die Werkzeuge aktiviert, welche wirklich benötigt werden.

Im Web GIS Client kann pro Geotop das Objektblatt "Inventar der geowissenschaftlich schützenswerten Objekte" geöffnet werden. Das Objektblatt wird mittels einem Jasper-Report erstellt.

## Erfassung
Die Daten werden im QGIS erfasst und in der Edit-DB verwaltet.
### DB Schema
Edit-DB: `afu_geotope`
### Anleitungen Erfassung im QGIS
`H:\BJSVW\Agi\Projekte\AFU\Ablösung INGESO VSB ISBoden Anwendungen\AP_Datenumbau_Realisiserung\Geotope\Anleitung_Erfassung_Geotope.docx`
### QGIS Projekt
QGIS-Projektfile: `H:\BJSVW\Agi\Projekte\AFU\Ablösung INGESO VSB ISBoden Anwendungen\AP_Datenumbau_Realisiserung\Geotope\Geotope_Erfassung_Produktionsumgebung.qgz`

QGIS-ini-File: `H:\BJSVW\Agi\Projekte\AFU\Ablösung INGESO VSB ISBoden Anwendungen\AP_Datenumbau_Realisiserung\Geotope\Geotop_Erfassung.ini`

### Spezielles
* Attributbezogene Einschränkungen (DrillDown)
> Drilldown (Kaskadierung): Mit dieser Funktion können Benutzer "Wertbeziehungs" -Ausdrücke basierend auf dem aktuellen Wert eines anderen Felds in derselben Form erstellen. Wenn der Benutzer den Wert eines Felds ändert, werden die in allen zugehörigen Feldern verfügbaren Auswahlmöglichkeiten so gefiltert, dass sie mit dem neuen Wert übereinstimmen. Dies ermöglicht eine hierarchische Filterstrategie innerhalb eines Formulars.

  Beispiel: Attributtabelle Layer `Fundstelle_Grabung`

  Wenn beim Attribut `geologisches system von` eine Auswahl getroffen wird, wird die Auswahl bei den Attributen `geologische Serie von` automatisch auf diese      Auswahl eingeschränkt.

  ![](https://github.com/bjsvwcur/DockTick_rote_Faeden/blob/master/Documents/afu_geologie_drilldown_2.PNG)

  Dafür muss beim Attribut `geologische_serie_von` ein Filter gesetzt werden, welcher sich auf das Attribut `geologisches_system_von` bezieht:

  `"geologisches_system" = current_value('geologisches_system_von')`

  ![](https://github.com/bjsvwcur/DockTick_rote_Faeden/blob/master/Documents/afu_geologie_drilldown_1.PNG)

## Publikation
Zum Filtern von Attributwerten aus der Pub-DB.
### DB Schema
Pub-DB: `afu_geotope_pub`
### Anleitungen Auswertung im QGIS:
`H:\BJSVW\Agi\Projekte\AFU\Ablösung INGESO VSB ISBoden Anwendungen\AP_Datenumbau_Realisiserung\Geotope\Anleitung_Auswertung_Geotope.docx`
### QGIS Projekt
QGIS-Projektfile: `H:\BJSVW\Agi\Projekte\AFU\Ablösung INGESO VSB ISBoden Anwendungen\AP_Datenumbau_Realisiserung\Geotope\Geotope_Auswertung_Produktionsumgebung.qgz`

QGIS-ini-File: `H:\BJSVW\Agi\Projekte\AFU\Ablösung INGESO VSB ISBoden Anwendungen\AP_Datenumbau_Realisiserung\Geotope\Geotop_Auswertung.ini`
### Datenumbau
Die Daten werden mittels einem Gretljob von der Edit-DB in die Pub-DB geschrieben.

**Gretljob ausführen:** https://gretl.so.ch/job/afu_geotope_pub/

**Gretljob konfigurieren:** https://github.com/sogis/gretljobs/tree/master/afu_geotope_pub

### Web GIS Client
Layergruppe: `ch.so.afu.geotope*`

Jasper-Report: Template im AGDI `afu_geotope`





