# WMTS
Verantwortlicher: Andreas Schmid

## Beschreibung 
Die funktionale Einheit _WMTS_ umfasst sowohl das eigentliche Bereitstellen eines WMTS-Dienstes in der GDI wie auch das Herstellen (lokal für statische Daten und in Openshift für sich täglich ändernde Daten) der Kacheln.

...

## Komponenten
- Mapcache
- "Paket für lokale Herstellung"?
- QGIS (separat für Mapcache?)
- ...

Stefan: Einfaches Komponentendiagramm mit Plantuml. (siehe ilivalidator). Plus Erläuterungen.

## Benutzung
[Erläutert dem Endbenutzer, wie die funktionale Einheit genutzt wird (GUI, bei API wie die API-Aufrufe aussehen)]

Stefan: Minimal. Wohl nur wie man den WMTS als wirklicher Endkunde verwendet?

## Konfigurieren und starten
[Beschreibt, wie die funktionale Einheit / die Komponenten konfiguriert und gestartet werden kann/können]

Stefan: Fokus sollte hier auf das Herstellen gelegt werden.

## Externe Abhängigkeiten
[Beschreibt, welche externen Abhängigkeiten für die funktionale Einheit / die Komponenten bestehen]

## Konfiguration und Betrieb in der GDI
[Beschreibt, wo die funktionale Einheit / die Komponenten wie in der GDI in Betrieb ist/sind]

Stefan: Wie wird das Teil in der GDI betrieben. Schon auch mit Prosa und nicht nur Verlinkung auf Templates o.ä.

## Interne Struktur
[Beschreibt den grundsätzlichen internen Aufbau der funktionalen Einheit / der Komponenten zwecks Verständnis für die Weiterentwicklung]
