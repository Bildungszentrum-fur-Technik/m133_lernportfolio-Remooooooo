# Woche 14

In dieser Woche gab es einen Theorieblock über Sessions, Cookies und Regex.

## Cookies

Mit Cookies kann man bestimmte Daten beim erneuten Aufrufen einwer Website festhalten. Dies bedeutet, diese Cookies werden auf dem PC des Users gespeichert und bleiben eine gewisse Zeit aktiv. Der User hat die möglichkeit, alle oder gewisse Cookies zu blockieren (Vorallem Tracking Cookies, Session Cookies sind gerne gesehen).

Weiter ist zu beachten, dass Cookies gefälscht werden können. Somit sollte man den COokies nicht trauen und nicht für sicherheitsrelevante Dinge benutzen. Meist werden Cookies für Funktionen wie "angemeldet bleiben" verwendet.

### Cookie Setzen

Man kann einen Cookie setzen mit folgendem Code:

```php
<?php
setcookie("username","Remo",0);
?>
```

`Username` ist in diesem Fall der Name des Cookies. Darüber ist der Cookie erreichbar. Die zweite Angabe ist der Value welcher im Cookie gespeichert wird. Die letzte Angabe ist die Gültigkeit des Cookies. Wenn 0 verwendet wird, ist der Cookie nur bis zum ende der Sitzung vorhanden.

Um die Zeit zu setzen benutzt man die Aktuelle Datetime und rechnet dann die Lebensspanne hinzu. Folgender Cookie hält für 24 Stunden.

```php
<?php
setcookie("username","Remo",,time()+(3600*24));
?>
```

### Cookies auslesen

Cookies können mit folgendem Code ausgelesen werden. Jedoch ist wichtig zu erwähnen, dass Cookies nur im selben Verzeichnis ausgelesen werden können.

```php
<?php 
$cookie = $_COOKIE["username"]; 
echo "Der Inhalt des Cookies: $cookie"; 
?>
```

### Cookies löschen

Es wird ein Zeitpunkt in der Vergangenheit angegeben, damit wird erkannt dass der Cookie abgelaufen ist und wird gelöscht

```php
<?php
setcookie("username","",,time() - 3600));
?>
```

## Sessions

Da HTTP ein zustandloses Protokoll ist, werden keine Informationen gespeichert. Da wir aber Informationen speichern wollen, verwenden wir PHP Sessions.

Der Vorteil von Sessions gegenüber Cookies ist, dass der User keine Möglichkeit hat, die Variablen der Session zu sehen oder zu bearbeiten.

### Session ID

Jeder Benutzer bekommt beim aufrufen einer Website eine Session-ID zugewiesen. Bei jedem erneuten aufruf wird diese ID überprüft und so kann der User identifiziert werden und vorherige Seitenaufrufe erneut laden.

Die Session ID wird vom Browser entweder als GET(oder POST) in der URL angehängt oder in einem lokalen Cookie gespeichert. Der Vorteil des Cookies ist es, da er nicht direkt ersichtlich ist.

Für jede Session ID ist ein Speicher im Server vorhanden, wo gewisse Variablen wie Name und Passwort oder Warenkörbe abgelegt sind.

Das Sessionhandling ist bereits in PHP eingebaut. Die Sessio ID wird mittels einem Hash erstellt, mit zusätzlichen Teilen wie der IP Adresse, Zeit und random generierte Werten.

### Sicherheit

Jedoch könnte sich ein Angreiffer die Session ID von jemand anderem besorgen und sich als jener ausgeben. Dies kann vorallem vorkommen, falls die Session ID in der URL abgelegt wird und ein Link von jemand fremden benutzt wird. Falls die ID jedoch in einem Cookie gespeichert wird, funktioniert es nur mit einem Trojaner oder mit Tracking vom Network traffic.

Ebenfalls könnte durch bruteforcing die POST Session ID's erraten.

### Anwendung

```php
<?php
session_start();
?>
```

## Regex

Reguläre Ausdrücke sind Muster um Daten zu filtern oder zu beschreiben. Jene können gut genutzt werden falls Inputs gewisse Ansprüche haben, zum Beispiel ein Passwort eine gewisse Länge, Sonderzeichen etc.. (Für E-Mail, Passwörter gibt es auch bereits fertige Regex Filter, die verwendet werden können)

In meinem Projekt habe ich Regex eingesetzt, da ich überprüfen muss ob die Personalnummer 6 Stellig ist und nur Zahlen enthält. (Ich kann keinen INT verwenden, da die Personalnummer führende Nullen zulassen muss.)

Regex ist nicht Programmiersprachenabhähnig, es kann auch in Powershell genutzt werden, um z.B. nach Servernamen zu suchen.

### Regex IP Adressen

Regex expression for validating IPv4

```php
    "/(([0-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5])\\.){3}([0-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5])/"
```

  Regex expression for validating IPv6

```php
    "/((([0-9a-fA-F]){1,4})\\:){7}([0-9a-fA-F]){1,4}/"
 ```

### Regex Mac Adressen

Regex expression for validating Mac adresses

```php
"/([0-9a-fA-F][0-9a-fA-F]:){5}([0-9a-fA-F][0-9a-fA-F])/"
```

### Regex Public IP Range

Regex expression for public IP range

```php
"/(^10\.)|(^172\.1[6-9]\.)|(^172\.2[0-9]\.)|(^172\.3[0-1]\.)|(^192\.168\.)|(^127\.0\.0\.1)/"
```
