# Woche 12

In dieser Woche haben wir uns mit den Datenbanken beschäftigt. Es gab einen grösseren Theorieblock zu neuen Themen.

## SQL Injection

SQL Injection bedeutet, wenn in einen String ein SQL Befehl mitgegeben wird. Jener kann verschiedenen Schaden anrichten wie z.B. alle Daten löschen oder dem Angreifer Adminrechte vergeben.
Das ganze kann mit einer sauberen Inputvalidierung, kombiniert mit Sanitizen und der Funktion "MySQLrealescapestring".

## Prepared Statements

Ist eine Datenbankfunktion, welche mit übergabeparametern befüllt wird.
Der Vorteil von den Prepared Statements ist, dass so kontrolliert werden kann, was für Daten sich in den Strings befinden. So können SQL Injections verhindert werden.

## WrapperFunktionen

Wrapper Funktionen sind Methoden welche sich im Core befinden und diverse PHP(und andere)einfache aufgaben übernehmen können, wie zum Beispiel Querys, Bindings oder Executes.

## PDO Verbindung

Wird von uns in der LB vewendet.
Rein OOP, Verbreitung daher eingeschränkt.
Hohe performance, einheitliche Schnittstelle für viele Datenbanken. Ähnliche Performance wie mysqli.

## Initscripts

Die Initscripts werden automatisch ausgeführt, wenn MySQL data leer ist. Die Scripts werden beim Start vom Docker Compose up ausgeführt. 
Die Initscripts sind dazu da, automatische Testdaten via SQL Befehle zu generieren.

## Adminer

Der Zugriff auf den Adminer erfolgt über localhost:8080. Die Logindaten müssen mit der Konfiguration des Docker-Container übereinstimmen. Als Server ist "mysql" anzugeben.
