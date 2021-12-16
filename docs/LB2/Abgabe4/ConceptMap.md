# Concept Map Abgabe 4

## Zu verwendende Begriffe

- Sessions
- Cookies
- \$_COOKIE
- \$_SESSION
- session_helper.php
- Authorisierung (Routen schützen)
- JSON (in Datenbank)

### Zusätzliche Begriffe

- Regex
- Mysql



## Concept Map

```plantuml
(Sessions) as (Sessions) 
note right of (Sessions) 
Da HTML ein zustandloses Protokoll ist, werden keine Infos gespeichert. Um Infos zu speichern, verwenden wir PHP Sessions.
Der Vorteil von Sessions ist, dass der User kene Möglichkeit hat, die Session Variablen zu sehen oder zu bearbeiten.
endnote

(Cookies) as (Cookies) 
note right of (Cookies)
Cookies sind dazu da, bestimmte Daten des Users zu speichern 
und beim erneuten Aufruf der Seite jene zu laden.
endnote

($_COOKIE) as (Cookie_Variable)
note right of (Cookie_Variable)
Dies ist ein assoziatives Array der Cookie Variable. 
Diese Variable wird dem aktuellen Skript via HTTP übergeben.
endnote

($_SESSION) as (Session_Variable)
note right of (Session_Variable)
Dies ist ein assoziatives Array, welches die Session Variable enthält.
endnote

(session_helper.php) as (SessionHelper)
note right of (SessionHelper)
Der SessionHelper ist eine Klasse mit mehreren Methoden, 
wie zum Beispiel Check, Error, Read, Valid.
Diese Methoden werden genutzt, ob Sessions Errors vorweisen 
oder überhaupt gültig sind etc.
endnote

(Authorisierung Routen schützen) as (Authorisierung)
note right of (Authorisierung)
Dient dazu, gewisse Aktionen (Bzw. Routen, Controller) 
nur für gewisse Authenzifizierung zugänglich zu machen.
Ansonsten ist die Route geschlossen.
endnote

(JSON in Datenbank) as (JSON)
note right of (JSON)
JSON wird zur Speicherung von strukturierten Daten verwendet. 
Wird häufig zum Übertragen von Daten zwischen Client Server genutzt.
endnote

(Regex) as (Regex)
note right of (Regex)
Regex ist ein Muster, um Daten zu filtern oder zu beschreiben,
um sie auf gültigkeit zu überprüfen.
endnote

(MySQL) as (MySQL)

note "Sind beides Möglichkeiten um Userdaten zu speichern" as NoteDaten
(Cookies) <--> NoteDaten
NoteDaten <--> (Sessions) 

note "Die Session ID kann auf einem Cookie gespeichert werden" as SessionSpeichern
(Sessions) <--> SessionSpeichern
SessionSpeichern <--> (Cookies) 

note "In dem Array werden die Daten des Cookie gespeichert" as NoteCookie
(Cookies) --> NoteCookie
NoteCookie --> (Cookie_Variable)

note "In dem Array werden die Daten der Session gespeichert" as NoteSession
(Sessions) --> NoteSession
NoteSession --> (Session_Variable)

note "Besitzt Methoden um Sessions zu verwalten" as NoteSessionHelper
(SessionHelper)--> NoteSessionHelper
NoteSessionHelper --> (Sessions) 

note "Authorisierung wird in Sessions gespeichert" as SessionAuth
(Authorisierung)--> SessionAuth
SessionAuth --> (Sessions) 

note "Die Rollen der Authentifizierung werden als JSON gespeichert" as JSONAuth
(JSON)--> JSONAuth
JSONAuth --> (Authorisierung) 

note "Regex kann verwendet um zu speichernde Daten zu überprüfen" as RegexJSON
(Regex)--> RegexJSON
RegexJSON --> (JSON) 
RegexJSON --> (MySQL) 

note "JSON wird in unserem Projekt als nosql feature auf der Datenbank gespeichert" as JSONSQL
(JSON)--> JSONSQL
JSONSQL --> (MySQL) 
```
