# Concept Map Abgabe 1

## Zu verwendende Begriffe

- SSR/ CSR
- MVC
- Template-Engine
- Use-Case
- Aktoren
- Funktionale Anforderung
- Testszenario
- Testfall

### Zusätzliche Begriffe

- Twig
- LB1

## Concept Map

```plantuml
@startuml
(SSR)
(CSR)
(MVC)
(Template-Engine) as (TemplateEngine)
(Use-Case) as (UseCase)
(Aktoren)
(Funktionale Anforderung) as (FunktionaleAnforderung)
(Testszenario)
(Testfall)
(Twig)
(LB1)

note "Methoden um Views darzustellen" as NoteSSR
(SSR) <--> NoteSSR
NoteSSR <--> (CSR)

note "Wird genutzt um das Script zu laden" as NoteMVC
(MVC) --> NoteMVC 
NoteMVC --> (SSR)
NoteMVC --> (CSR)

note "Gehören zu einem Projekt" as NoteProjekt
(MVC) .. NoteProjekt
(TemplateEngine) .. NoteProjekt
(CSR) .. NoteProjekt
(SSR) .. NoteProjekt

note "Twig ist eine Template-Engine für PHP, um das View zu vereinfachen" as NoteTwig
(TemplateEngine) --> NoteTwig
NoteTwig --> (Twig)

note "SSR nutzt eine Template Engine, um Daten darzustellen" as NoteEngine
(SSR) --> NoteEngine
NoteEngine --> (TemplateEngine)

note "Aus den Use-Cases werden die Funktionalen Anforderungen abgeleitet" as NoteAnforderungen
(UseCase) --> NoteAnforderungen
NoteAnforderungen --> FunktionaleAnforderung

note "UseCases werden von Aktoren ausgelöst" as NoteAktoren
(Aktoren) --> NoteAktoren
NoteAktoren --> (UseCase)

note "Auswahl der Engine durch Anforderungen an die Website " as NoteWebsite
(FunktionaleAnforderung) --> NoteWebsite
NoteWebsite --> (TemplateEngine)

note "Testszenarien werden durch die Anforderungen gebildet" as NoteSzenario
(FunktionaleAnforderung) --> NoteSzenario
NoteSzenario --> (Testszenario)

note "Exakte ausführung eines Testfalles" as NoteFall
(Testszenario) --> NoteFall
NoteFall --> (Testfall)

note "Gehören zum Strukturierten Aufbau eines Projektes" as NoteAufbau
(Aktoren) .. NoteAufbau
(Testfall) .. NoteAufbau
(Testszenario) .. NoteAufbau
(FunktionaleAnforderung) .. NoteAufbau
(UseCase) .. NoteAufbau

note "Bauen auf den Handlungen der Aktoren auf" as NoteAktor
(Testfall) --> NoteAktor
(Testszenario) --> NoteAktor
NoteAktor --> (Aktoren)

note "Verbindung von allem in der LB1" as NoteLB1
NoteAufbau .. NoteLB1
NoteLB1 .. NoteProjekt

note "Twig wird in der LB1 als Template verwendet" as NoteTwigLB
(LB1) --> NoteTwigLB
NoteTwigLB --> (Twig)

note "Je nach Anforderungen der Website wird SSR/CSR oder eine Hybridlösung verwendet" as NoteAnforderung
(FunktionaleAnforderung) --> NoteAnforderung
NoteAnforderung --> (SSR)
NoteAnforderung --> (CSR)

note "In meinem Projekt wird SSR verwendet" as NoteSSRLB
(LB1) --> NoteSSRLB
NoteSSRLB --> (SSR)
@enduml
```
