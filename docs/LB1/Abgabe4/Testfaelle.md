# Testfälle

## Definition Testfälle

Folgende Testfälle wurden in der Zielsetzung definiert:
Ausserdem habe ich für mehr Testmöglichkeiten meine Initscripts erweitert, damit mehr Testdaten verfügbar sind.

### Szenario 1 - Mitarbeiter füllt Formular aus

| Szenario 1           | Mitarbeiter füllt Formular aus |
| -------------------- | :----------------------------- |
| Akteure              | Mitarbeiter                    |
| Trigger              | Mitarbeiter ruft das Spesenformular auf |
| Erwartetes Ergebnis  | Formular wird an den Vorgesetzten übermittelt |
| Falls Fehler         | Fehlermeldung und die Übermittlung startet nicht |

### Szenario 2 - Vorgesetzter signiert Formular

| Szenario 2           | Vorgesetzter signiert Formular |
| -------------------- | :----------------------------- |
| Akteure              | Vorgesetzter                    |
| Trigger              | Vorgesetzter ruft das zu signierende Spesenformular auf |
| Erwartetes Ergebnis  | Spesenabrechnung wird unterzeichnet und bestätigt. |
| Falls Fehler         | Fehlermeldung und die Bestätigung findet nicht statt. |

### Szenario 3 - Vorgesetzter zeigt Formulare an

| Szenario 3           | Vorgesetzter zeigt Formulare an |
| -------------------- | :----------------------------- |
| Akteure              | Vorgesetzter                    |
| Trigger              | Vorgesetzter ruft View aller Formulare auf |
| Erwartetes Ergebnis  | Formulare werden angezeigt |
| Falls Fehler         | - |

## Test der Testszenarien

### Ausführung Szenario 1 - Mitarbeiter füllt Formular aus

Mitarbieter loggt sich ein.  
Mitarbeiter wählt das Spesenformular aus.  
Mitarbeiter füllt das Formular aus.  
Mitarbeiter schickt das Formular ab.  

#### Ergebnis 1

Alle Aktionen erfolgreich, keine Massnahmen notwendig.  
Formular wird erfolgreich in der DB angelegt.

### Ausführung Szenario 2 - Vorgesetzter signiert Formular

Vorgesetzer loggt sich ein.  
Vorgesetzer wählt zu signierendes Spesenformular aus.  
Vorgesetzter signiert das Formular.  
Vorgesetzter schickt das Formular ab.  

#### Ergebnis 2

Alle Aktionen erfolgreich, keine Massnahmen notwendig.  
Das Formular wird bei genehmigung auf true gesetzt und beim ablehnen gelöscht.

### Ausführung Szenario 3 - Vorgesetzter zeigt Formulare an

Vorgesetzer loggt sich ein.  
Vorgesetzer wählt anzeige der Formulare aus  
Formulare werden angezeigt.

#### Ergebnis 3

Alle Aktionen erfolgreich, keine Massnahmen notwendig.  
Formulare werden angezeigt.

## Weitere Zugriffstest

Die Login(Beinhaltet anmelden und abmelden Funktion) konnte mit wenigen Anpassungen von Herr Inauen übernommen werden.  
Jene funktionierte Problemlos.

Mitarbeiter:  
    - Zugriff auf Formular ausfüllen: Erfolgreich  
    - Zugriff auf eigene Formulare anzeigen: Erfolgreich  
    - Zugriff auf UserDB: Kein Zugriff gewährt -> Erfolgreich  
    - Zugriff auf Vorgesetzten Ansicht:  Kein Zugriff gewährt -> Erfolgreich

Vorgesetzter  
    - Zugriff auf Formular ausfüllen: Erfolgreich  
    - Zugriff auf eigene Formulare anzeigen: Erfolgreich  
    - Zugriff auf UserDB: Kein Zugriff gewährt -> Erfolgreich  
    - Zugriff auf Vorgesetzten Ansicht: Erfolgreich

Admin (inkl. User rechte)  
    - Zugriff auf Formular ausfüllen: Erfolgreich  
    - Zugriff auf eigene Formulare anzeigen: Erfolgreich  
    - Zugriff auf UserDB: Erfolgreich  
    - Zugriff auf Vorgesetzten Ansicht:  Kein Zugriff gewährt -> Erfolgreich
