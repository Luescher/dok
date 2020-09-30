# ÖREB-Kataster
Verantwortliche: Andrea Lüscher

## Beschreibung 
Bla bla blanig...

TODO: Andrea

## Komponenten
![Komponentendiagramm](https://www.planttext.com/api/plantuml/img/TL91JiCm4BplArRXd0lYL25KXIHL4LMhjgX8Y8EJRC5gQaUnmm7KlxEsqwOg9JbaPpsUzKmyDbQqjjlN0AAqkiNenL0ReJ3OSG7GY78dFWYZl5CxAxKIDM4crIT96-4F83-btZTQaRBuDi-MMH9lgE3DNxAaTwSqfytgajXKspjDBHMUiM0qTmZ-4PojZagpFr8y3IVJ5JxMah7dXJA8LSAAGXYs4BHIOKaLGksYe9WcddPzy6IPhP_Z9rqOhpjfoTQNJ6yZbgLMyfjQpvls000E0CC9iahQE4tyP5Ud2TviRzqBi9MSxEiwTsivrsPOAclTLJviJrgaUH_QYN900FV3C8uVJkvTxhxXJVPeo1f7M553gZBWSnse41Jw1cyRkTjmqPrTQRCsW0y9xtbKi85ddM3Q7OsjkqP8j6SmFYPtTZWOyuUlw2y0)

Der _Web GIS Client_ ist nicht komplett ein Bestandteil des ÖREB-Katasters, sondern nur das Werkzeug "Grundstücksinformation".

Eine detaillierte Auflistung sämtlicher Komponenten ist dem [ÖREB-Handbuch](https://sogis.github.io/oereb-handbuch/master.html) zu entnehmen.

## Benutzung
[Erläutert dem Endbenutzer, wie die funktionale Einheit genutzt wird (GUI, bei API wie die API-Aufrufe aussehen)]

TODO: Andrea. Verlinkung auf Typo3 reicht wohl (?).

## Konfigurieren und starten
[Beschreibt, wie die funktionale Einheit / die Komponenten konfiguriert und gestartet werden kann/können]

Der _ÖREB-Kataster_ als Gesamtanwendung kann (noch) nicht einfach lokal gestartet werden. Mit `docker-compose` wäre dies problemlos möglich. Die Abrenzung müsste trotzdem geklärt werden, d.h. gehören die Datenumbauprozesse dazu oder "nur" der Betrieb des eigentlichen ÖREB-Katasters. Was ist mit dem Web GIS Client? Wie werden die Daten in die lokale Datenbank importiert.

Insbesondere für die ÖREB-GRETL-Jobs steht eine lokale Entwicklungsmöglichkeit (mit lokalen Datenbanken) zur Verfügung. Siehe [https://github.com/sogis/oereb-gretljobs](https://github.com/sogis/oereb-gretljobs).

Für die anderen Komponenten sei ebenfalls auf das Git-Repository verwiesen (siehe ÖREB-Handbuch).

## Externe Abhängigkeiten
Die Kapitel [Integrationsprozesse](https://sogis.github.io/oereb-handbuch/master.html#_integrationsprozesse) des ÖREB-Handbuchs.

## Konfiguration und Betrieb in der GDI
[Beschreibt, wo die funktionale Einheit / die Komponenten wie in der GDI in Betrieb ist/sind]

TODO: Michael. Z.B. auch was zur DB (kein spezieller DB-Server etc.)

## Interne Struktur

### Pdf4oereb
Die Umwandlung des XML-Auszuges in ein PDF wird mit _XSLT_ und _XSL-FO_ gemacht. Für die XSLT-Transformation mussten zusätzlich einige Java-Funktionen geschrieben werden.

### Oereb-Iconizer
Siehe Erläuterungen im [README](https://github.com/openoereb/oereb-iconizer/blob/master/README.md).

### Oereb-web-service
Spring Boot Anwendung, welche die Daten aus der Datenbank mit _JdbcTemplates_ zusammensucht und anschliessend mit _Jaxb_ in eine XML-Datei serialisiert. Für die Umwandlung nach PDF wird _pdf4oereb_ als Bibliothek verwendet.
