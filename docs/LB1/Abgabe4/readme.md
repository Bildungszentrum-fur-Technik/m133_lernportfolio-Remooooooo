# Abgabe 4

Die Abgabe 4 der LB1 besteht aus:

- 10% Umsetzung funktionale Anforderungen (mit Sessions/Cookies/Auth. etc.)
  - Implementierung von Sessions auf MVC gemacht
  - Benutzer-DB und Klassen sind implementiert
  - Routen sind authorisiert geschützt
  - Redirects sind sinnvoll umgesetzt

- 5% Testfälle sind formuliert und Testergebnisse festgehalten
  - Testfälle in der Dokumentationen angepasst
  - Testfälle durchgegangen und Ergebnisse festgehalten

## Implementierung Sessions und Benutzer

## Redirects

Falls ein Benutzer zu wenig rechte für einen Seitenaufruf hat, wird der User auf die Home Seite redirected.
Falls noch kein Benutzer angemeldet ist, wird er zur Login seite redirected.

## Routen geschützt

Jede Methode wurde durch einen If Else überprüft. In der Überprüfung wird erst geschaut, ob der User angemeldet ist und in der zweiten Überprüfung wird geschaut, ob die user roles übereinstimmen (Rechte).
Dies sieht wie folgt aus:

```php
        // Dürfen wir überhaupt diese Funktion nutzen? 
        if (!isset($_SESSION['user_id'])) {
            // Kein Login, Keine Bestellungen -> möglich wäre auch eine Weiterleitung auf Login
            redirect('');
        } else {

            if (!in_array("vorgesetzter", $_SESSION['user_roles'])) {
                redirect('');
            }
```

## Benutzer DB und Klassen

Folgende Benutzer sind Verfügbar:

| Benutzer          | Rechte |
| ----------------- | :----------------------------- |
| Users             | Mitarbeiter, kann Formular ausfüllen& eigene anzeigen.                  |
| Vorgesetzter      | Vorgesetzter kann Formular ausfüllen& alle anzeigen& Formular genehmigen |
| Administrator     | Zugriff auf User DB |
