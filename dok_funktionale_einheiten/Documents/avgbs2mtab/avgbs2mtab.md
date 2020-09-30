# avgbs2mtab
Verantwortlicher: Daniel Rudin

## Beschreibung 
Webservice zum Konvertieren von Mutationen in einer AVGBS-Datei in eine Exceldatei. Dem Benutzer steht ein sehr einfache Frontend zur Verfügung.

## Komponenten
![Komponentendiagramm](https://www.planttext.com/api/plantuml/img/SoWkIImgAStDuU9AJ2x9Br9G2YrEBL9II2nMA0Kok9BpSmloyrBpIXIY4ylIaugDSaiIatJBKvDqWR9bcScfLZ5vmGL5cNdf2axv-IKAsWe8PR4WKq06S761p5BGrRM3SXrIyr90TW80)

Repository: [https://github.com/sogis/avgbs2mtab-web-service](https://github.com/sogis/avgbs2mtab-web-service)

## Benutzung
Dem Endbenutzer steht eine sehr einfaches Formular im Browserfenster zum Übermitteln der AVGBS-Datei zur Verfügung. Die resultierende Exceldatei wird automatisch heruntergeladen. Bei einem Fehler wird der Output von _ilivalidator_ im Browserfenster angezeigt.

Produktion: https://geo.so.ch/avgbs2mtab

Integration: https://geo-i.so.ch/avgbs2mtab

Test: https://geo-t.so.ch/avgbs2mtab

## Konfigurieren und starten
```
docker run -p 8080:8878 sogis/avgbs2mtab-web-service
```

Die Konfiguration der Anwendung wird in einer `application.properties`-Datei gemacht.

## Externe Abhängigkeiten
Siehe [`build.gradle`](https://github.com/sogis/avgbs2mtab-web-service/blob/master/library/build.gradle).

## Konfiguration und Betrieb in der GDI
- Template Openshift: [https://github.com/sogis/openshift-templates/tree/master/avgbs2mtab](https://github.com/sogis/openshift-templates/tree/master/avgbs2mtab) 

## Interne Struktur
Für das Lesen der AVGBS-Datei wird [_iox-ili_](https://github.com/claeis/iox-ili) verwendet. Es bedarf zudem auch gewisses Verständnis für das Datenmodell (`GB2AV`) und ein genügendes Mass an Frustrationstoleranz...

Das Herstellen der Exceldatei übernimmt _Apache POI_.

Es handelt sich um einen Gradle Multiprojekt Build, d.h. ein Subprojekt für die eigentliche Bibliothek und ein weiteres Subprojekt für den Webservice (Spring Boot).

In Tomcat wird ein Servercontext gesetzt (`/avgbs2mtab`).
