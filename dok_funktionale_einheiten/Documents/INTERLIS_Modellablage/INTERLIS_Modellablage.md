# INTERLIS-Modellablage
Verantwortlicher: Stefan Ziegler

## Beschreibung 
Die _INTERLIS-Modellablage_ stellt sämtliche INTERLIS-Modelle der kantonalen Verwaltung nach bekanntem [Muster](http://models.interlis.ch/ModelRepository.pdf) bereit.

Die Modelle können von allen Mitarbeitern des AGI selbständig nachgeführt werden.

## Komponenten
![Komponentendiagramm](https://www.planttext.com/api/plantuml/img/PL0zRm8n3DtzAwph0aCMHeOA2Hqd9AWgFgR2uDwvDC8ufoGt8CH_RqABT1HdUSxpUtdE94JoiJi90DNHUIosWNs15B1B0A2b-aW7ncBMwJ5QfoICfTLljh702s2gsfrQfwmHF-PlctArcA_DqZKiGf-InFjirx_uhx8QsOiDndFhWaqvpgRsJ0diT51vQeJDktG7gyERsVINHBW2z7ogLRbPt0Ogpr7mvMkK3q3U1OrvVKm1_IxHVwfnNls9kpyvnePRrYQWKu19GldtVW00)

Repositories:

- INTERLIS-Modellablage: [https://github.com/sogis/sogis-interlis-repository](https://github.com/sogis/sogis-interlis-repository)
- INTERLIS-Repository-Creator: [https://github.com/sogis/interlis-repository-creator](https://github.com/sogis/interlis-repository-creator)

## Benutzung
Siehe [Dokumentation](https://github.com/sogis/sogis-interlis-repository/blob/master/docs/betriebs-_und_nachfuehrungshandbuch.md).

## Konfigurieren und starten

```
docker run -p 8080:8080 sogis/interlis-repository
```

Siehe [`nginx.conf`](https://github.com/sogis/sogis-interlis-repository/blob/master/nginx.conf).

## Externe Abhängigkeiten
Keine.

## Konfiguration und Betrieb in der GDI
- Template Openshift: [https://github.com/sogis/openshift-templates/tree/master/interlis-repository](https://github.com/sogis/openshift-templates/tree/master/interlis-repository)

## Interne Struktur
Die Herstellung der INTERLIS-Modellablage ist ein Gradle Build. Während des Buildprozesses wird das Dockerimage erstellt und auch gleich geprüft.

Die `ilimodels.xml`-Datei wird mittels speziellem Gradle-Task hergestellt. Dazu muss das Gradle-Plugin _ch.so.agi.interlis-repository-creator_ verwendet werden.

Die Modelle müssen einige Metaattribute aufweisen, damit die `ilimodels.xml`-Datei erstellt werden. Siehe dazu auch die Kommentare im Code.

