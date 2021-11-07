# Testszenarien

## Szenario 1 - Mitarbeiter füllt Formular aus

| Szenario 1           | Mitarbeiter füllt Formular aus |
| -------------------- | :----------------------------- |
| Akteure              | Mitarbeiter                    |
| Trigger              | Mitarbeiter ruft das Spesenformular auf |
| Erwartetes Ergebnis  | Formular wird an den Vorgesetzten übermittelt |
| Falls Fehler         | Fehlermeldung und die Übermittlung startet nicht |

Mitarbieter loggt sich ein.
Mitarbeiter wählt das Spesenformular aus.
Mitarbeiter füllt das Formular aus.
Mitarbeiter schickt das Formular ab.

## Szenario 2 - Vorgesetzter signiert Formular

| Szenario 2           | Vorgesetzter signiert Formular |
| -------------------- | :----------------------------- |
| Akteure              | Vorgesetzter                    |
| Trigger              | Vorgesetzter ruft das zu signierende Spesenformular auf |
| Erwartetes Ergebnis  | Spesenabrechnung wird unterzeichnet und bestätigt. |
| Falls Fehler         | Fehlermeldung und die Bestätigung findet nicht statt. |

Vorgesetzer loggt sich ein.
Vorgesetzer wählt zu signierendes Spesenformular aus.
Vorgesetzter signiert das Formular.
Vorgesetzter schickt das Formular ab.

## Szenario 3 - Vorgesetzter zeigt Formulare an

| Szenario 3           | Vorgesetzter zeigt Formulare an |
| -------------------- | :----------------------------- |
| Akteure              | Vorgesetzter                    |
| Trigger              | Vorgesetzter ruft View aller Formulare auf |
| Erwartetes Ergebnis  | Formulare werden angezeigt |
| Falls Fehler         | - |

Vorgesetzer loggt sich ein.
Vorgesetzer wählt anzeige der Formulare aus
Formulare werden angezeigt.
