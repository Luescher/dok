# ilivalidator-web-service

Verantwortlicher: Stefan Ziegler

## Beschreibung 
Der _ilivalidator-web-service_ ist eine [Spring-Boot-Anwendung](https://spring.io/projects/spring-boot) und verwendet [_ilivalidator_](https://github.com/claeis/ilivalidator) für die Validierung der INTERLIS-Transferdatei.

Der _ilivalidator-web-service_ stellt eine einfache Art dar INTERLIS-Daten gegenüber einem INTERLIS-Modell zu prüfen (= Modellkonformität). Die zu prüfenden INTERLIS-Daten werden mittels Webformular auf einen Server hochgeladen, wo sie anschliessend automatisch geprüft werden. Das Prüfresultat wird direkt im Browser angezeigt.
Für die Nutzungsplanung wurden spezielle Validierungsfunktionen implementiert. 

Die Programmbibliothek _ilivalidator_ selbst ist nicht Bestandteil dieser funktionalen Einheit. 

## Komponenten
![Komponentendiagramm](https://www.planttext.com/api/plantuml/img/SoWkIImgAStDuU9AJ2x9Br9G2YrEBL9II2nMA0Kok9BpSmloyrBpIXIYCtCoon9pCbCIWSfqorEJT87oPPd9gLOnUS45HPbvwGfE-Vab2jeAo0fZGIQ13E7Y0fcdeAjh1-KwfEQb0Eq50000)

* ilivalidator-web-service: [https://github.com/sogis/ilivalidator-web-service-websocket](https://github.com/sogis/ilivalidator-web-service-websocket)
* ilivalidator-custom-functions [https://github.com/sogis/ilivalidator-custom-functions](https://github.com/sogis/ilivalidator-custom-functions)

## Benutzung
Aufruf des _ilivalidator-web-service_:

Produktion: https://geo.so.ch/ilivalidator

Integration: https://geo-i.so.ch/ilivalidator

Test: https://geo-t.so.ch/ilivalidator

### Anleitungen
Benutzerhandbuch zur Bedienung der Anwendung: [https://github.com/sogis/ilivalidator-web-service-websocket/blob/master/docs/user-manual-de.rst](https://github.com/sogis/ilivalidator-web-service-websocket/blob/master/docs/user-manual-de.rst)

Informationen zu speziellen Nutzungsplanungstests: [https://github.com/sogis/ilivalidator-web-service-websocket/blob/master/docs/user-manual-de-nplso.md](https://github.com/sogis/ilivalidator-web-service-websocket/blob/master/docs/user-manual-de-nplso.md)

## Konfigurieren und starten
```
docker run -p 8080:8080 sogis/ilivalidator-web-service
```

Die Konfiguration der Anwendung wird in einer `application.properties`-Datei gemacht.

## Externe Abhängigkeiten
Siehe [`build.gradle`](https://github.com/sogis/ilivalidator-web-service-websocket/blob/master/build.gradle). 

## Konfiguration und Betrieb in der GDI
* Template Openshift: [https://github.com/sogis/openshift-templates/tree/master/ilivalidator](https://github.com/sogis/openshift-templates/tree/master/ilivalidator)
* nginx.conf: [https://github.com/sogis/pipelines/blob/master/api_webgisclient/api-gateway/resources.yaml](https://github.com/sogis/pipelines/blob/master/api_webgisclient/api-gateway/resources.yaml) Die `nginx.conf`-Datei wird noch als ConfigMap in Openshift verwendet. Wird sie zukünftig auch in das Image gebrannt, wandert sie in das qwcservices-Repository.

## Interne Struktur
Die Kommunikation zwischen Client (Browser) und Server basiert auf Websocket. Damit können auch lang dauernde Validierungen vorgenommen werden ohne dass es zu Timeouts (Client oder Firewall/SES) kommt. Absprachen mit AIO und GDI waren notwendig, damit Websocket geöffnet ist und zusammenspielt.

Im `index.html` sind einige Zeilen Javascript vorhanden. Vor allem wegen des Einsatzes von Websocket.

Informationen zu den zusätzlichen Validierungen und programmtechnisch damit umgegangen wird, sind im [README](https://github.com/sogis/ilivalidator-web-service-websocket/blob/master/README.md) nachzulesen.

Das Dockerimage wird mit Gradle-Tasks gebuilded und auch getestet.

In Tomcat wird ein Servercontext gesetzt (`/ilivalidator`).
