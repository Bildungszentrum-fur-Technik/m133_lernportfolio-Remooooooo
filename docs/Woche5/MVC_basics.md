# Model View Controller (MVC)

Dieser Teil der Doku ist zeigt die einzelnen Komponenten von MVC. Beispiele werden [hier](../Woche6/MVC.md) genauer behandelt.

MVC dient als Handlungsempfehlung. Diese ist nicht fix und man kann viel selber konfigurieren, da es nur eine Anleitung ist. Der Hauptvorteil ist, dass die Komponenten getrennt sind. So können auch mehrere Programmierer gut zusammenarbeiten und der Code bleibt leserlich.

## Funktionsweise

Jeder der Komponenten hat eine eigene Aufgabe. Dies dient zur einfacherer Übersichtlichkeit und besserer Zusammenarbeit. Das Model ist für die Datenbankzugriffe zuständig und deren Entitäten. Die View ist für das Frontend zuständig und der Controller verbintet das Model mit dem View.

## Model

Wie bereits angetönt ist das Model die Datenbank, für welche entsprechende Methoden erstellt werden. Jene Klasse schreiben Daten in die Datenbank hinein.

- Repräsentiert eine logische Einheit
- Enthält Plausibilitätskontrollen
- Enthält logik

## View

Das Frontend wird über den View konfiguriert. Vor allem ist der View für die Darstellung der benötigten Daten aus dem Model und die Entgegennahme von Benutzerinteraktionen zuständig.

- Darstellung der Informationen
- Stellt Model dar
- Keine Logik
- Speichert keine Daten

## Controller

Der Controller wird für die Kommunikation zwischen den Klassen im Model und im View verwendet. Er verwaltet eine oder mehrere Views, nimmt Benutzeraktionen entgegen, wertet diese aus und handelt entsprechend.

- Verbindet Model und View
- Enthält Logik
- Kann Datenbankverbindungen enthalten
  