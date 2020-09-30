# AV-Datenabgabe
Verantwortlicher: Stefan Ziegler

## Beschreibung 
_AV-Datenabgabe_ ist eine simple Liste im Browser, um Daten der amtlichen Vermessung gemeindeweise in verschiedenen Formaten herunterzuladen. Ein Link auf die Gemeinde im Web GIS Client wird auch bereitgestellt, damit der Endanwender ein Auszug aus dem Plan für das Grundbuch erstellen kann (nicht beglaubigt).

Wünschenswert wäre, wenn die Anwendung mit der neuen Datenabgabe obsolet werden würde.

## Komponenten
![Komponentendiagramm](https://www.planttext.com/api/plantuml/img/NP2x3i8m34LtVuLLHjG5DWRK8k07mcC01hUu9Q9rgZP5GeX_9-6bWBtasiUvSPBEKclxkWAWt9eMetN7ROJKOUyE00tbPoePesKlPwkDKCMuq79YRIEy0Rh8JTqOOR6uIpVnd2mBPILbFDcBQbej9SwCiJZ4rUbQSyLK7Bn3GC8TN0GNkHwXUy55v_o1wQrnK8nyXdowLR4QFqar_WBWby0udlvuGI1SqmzC_Bh_zT3o1K32SlI_zG00)

Repository: [https://github.com/sogis/av_datenabgabe_ng](https://github.com/sogis/av_datenabgabe_ng)

## Benutzung
Der Anwender kann im Browser gemeindeweise verschiedene Formate der Daten der amtlichen Vermessung herunterladen. Die Shapefiles gibt es nicht gemeindenweise, sondern nur als ganzen Kanton.

## Konfigurieren und starten
```
docker run -p 8080:8080 sogis/cadastral-data-disposal
```

Die Konfiguration wird mittels `application.properties`-Datei gesteuert. Die Parameter können mit ENV-Variablen überschrieben werden.

## Externe Abhängigkeiten
[Beschreibt, welche externen Abhängigkeiten für die funktionale Einheit / die Komponenten bestehen]

Um an die notwendigen Information zu gelangen, verwendet die Anwendung einerseits den _Data service_ (`ch.so.agi.av.nachfuehrungsgemeinden.data`) und andererseits Metainformationen aus dem S3-Bucket, wo fast alle Dateien gespeichert sind. Die Shapefiles werden von [geodienste.ch](https://geodienste.ch) verwendet. 

## Konfiguration und Betrieb in der GDI
* Template Openshift: [https://github.com/sogis/openshift-templates/tree/master/av-datenabgabe](https://github.com/sogis/openshift-templates/tree/master/av-datenabgabe)

## Interne Struktur
Für das Rendering der Webseite wird _Thymeleaf_ verwendet. 

In Tomcat wird ein Servercontext gesetzt (`/av_datenabgabe`).

