# Architekturkonzept

## Beschreibung des MVC

Die einzelnen Komponenten von MVC ist [hier](/Woche5/MVC_basics.md) dokumentiert und ausführlicher mit Beispiel findet man [hier](Woche6/MVC.md)

## Beinhaltet Beschreibung von Template-Engine-Twig

Die Funktionsweise von Twig ist [hier](Woche7/Twig.md) aufgeführt.

## Beschreibung von SSR

SSR wurde [hier](/Woche4/SSR_CSR.md) abgehandelt.

## Beschreibung der Aufgabenstellung / inkl. Darstellung des Formulars

### Aufgabenstellung

Meine Aufgabe ist es, das von unserer Firma verwendete Spesenformular interaktiv zu erstellen. Da relativ viele Kosten aufgeführt sind, werden jene weggelassen, damit sich auf das wesentliche konzentriert werden kann.
Das ausgefüllte Formular muss anschliessend vom Vorgesetzten signiert werden. Anschliessend ist es dem Vorgesetzten möglich, alle signierten Formulare anzuzeigen.

### Darstellung des Formulars

Das Formular, welches ich ablöse sieht wie folgt aus:

![Spesen](/Spesen.png)

Ich werde versuchen, das Formular relativ Tabelarisch darzustellen, damit die Übersichtlichkeit der Kosten und dem Endresultat gegeben ist.

## Konkreter Vorschlag Anwendung von MVC auf Formular (welche Controller/Views/Models)

User sendendet Formular ab an den Spesen Controller. Im Controller wird ein Spesenmodel erstellt und die Angaben werden validiert. Bei erflogreicher Validierung wird eine Bestätigungsview angezeigt, dass die Übermittlung erfolgreich war. Bei einem Fehler wird eine Fehlermeldung angezeigt, jedoch bleiben die ausgefüllten Werte bestehen.

### Controller

Spesencontroller

### Model

Spesenmodel

### View

Formularview
Bestätigungsview

## Konkreter Vorschlag Anwendung Twig auf Formular (Footer/Header/etc.)

### Header

Im Header befindet sich der Titel. Ausserdem wird eine Navbar erstellt, in welcher der Mitarbeiter oder der Vorgesetzte verschiedene Möglichkeiten hat (MA: Neues Formular ausfüllen, Vorgesetzter: Formulare anzeigen)

### Body

Im Body befindet sich das Formular, entweder zum ausfüllen oder zum Unterschreiben(als Vorgesetzter)

### Footer

Remo Stark © 2021. Alle Rechte vorbehalten.
