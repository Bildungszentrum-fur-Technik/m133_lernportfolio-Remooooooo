# Concept Map Abgabe 2

## Zu verwendende Begriffe

- if-Funktion bei Twig
- Mocking von Daten
- Rendern von View
- empty()-Funktion
- santizen von Daten

## Concept Map

```plantuml
@startuml
(if-Funktion bei Twig) as (IfTwig)
note right of (IfTwig) 
Wird gleich angewendet wie bei anderen Programmiersprachen um dynamische Websiten zu erstellen
end note
(Mocking von Daten) as (Mocking)
note right of (Mocking)
Das simulieren von Daten, wenn keine Datenbank vorhanden ist
end note
(Rendern von View) as (rendern)
note right of (rendern)
Generieren der View mit Daten aus dem Controller
end note
(empty-Funktion) as (empty)
note right of (empty)
Überprüft, ob eine Variable leer ist oder nicht
end note
(sanitizen von Dlaten) as (sanitizen)
note right of (sanitizen)
Entfernen aller nicht passenden Zeichen des Datentyps
end note

note "Kann benutzt werden als Überprüfung für das ausführen der Verzweigung" as NoteIf
(empty) --> NoteIf 
NoteIf --> (IfTwig)

note "Gemockte Daten werden in der View dargestellt" as NoteMock
(Mocking) --> NoteMock
NoteMock --> (rendern)

note "If Funktionen beeinflussen das Rendern der View" as NoteView
(IfTwig) --> NoteView
NoteView --> (rendern)

note "Kann benutzt werden, um zu überprüfen ob nach dem sanitizen der Daten noch Daten vorhanden sind" as NoteSani
(empty) --> NoteSani
NoteSani --> (sanitizen)

note "Daten können das Ergebniss des If beinflussen" as NoteIfMock
(Mocking) --> NoteIfMock
NoteIfMock --> (IfTwig)

@enduml
```
