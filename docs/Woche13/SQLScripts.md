# SQL Scripts

Die Initscripts werden automatisch ausgeführt, wenn der Ordner MySQL Data leer ist. Die Scripts werden beim Start vom Docker Compose up ausgeführt.
Die Initscripts sind dazu da, automatische Testdaten via SQL Befehle zu generieren.

## Namensgebung

Die Scripts werden von einer Führenden Zahl im Namen benannt. Dies wird gemacht, damit die Scripts in der richtigen Reihenfolge ausgeführt werden und somit gesteuert werden kann, dass erst die Datenbank erstellt wird und erst dann die Values befüllt werden.

## Aufteilung

Ich habe 2 Scripts erstellt. Das erste erstellt die Datenbank und das zweite inserted die Testdaten in die Datenbank.

## Speicherort

Die Scripts liegen im mysql Container im initscripts Ordner. `../Projekt/mysql/initscripts/..`

## Problembehandlung

Falls es zu Fehlern kommt, ist es hilfreich den Ordner "mysqldata" zu löschen, da sich dort automatisch generierte tempdaten befinden.
Der Befehl muss zwingend mit sudo ausgeführt werden. `sudo rm -rf /mysql/mysqldata/*`.

## Adminer

Der Zugriff auf den Adminer erfolgt über `localhost:8080`. Die Logindaten müssen mit der Konfiguration des Docker-Container übereinstimmen. Als Server ist "mysql" anzugeben. Über den Adminer lassen sich bequem änderungen an der Datenbank und an den Daten vornehmen. Ausserdem kann über den Adminer ein Export generiert werden, welcher dann in den Initscripts verwendet werden kann.
