# SQL Scripts

Die Initscripts werden automatisch ausgeführt, wenn der Ordner MySQL Data leer ist. Die Scripts werden beim Start vom Docker Compose up ausgeführt.
Die Initscripts sind dazu da, automatische Testdaten via SQL Befehle zu generieren.

## Namensgebung

Die Scripts werden von einer Führenden Zahl im Namen benannt. Dies wird gemacht, damit die Scripts in der richtigen Reihenfolge ausgeführt werden und somit gesteuert werden kann, dass erst die Datenbank erstellt wird und erst dann die Values befüllt werden.

## Aufteilung

Ich habe 2 Scripts erstellt. Das erste erstellt die Datenbank und das zweite inserted die Testdaten in die Datenbank.

- Datenbank erstellen Skript:
  
```php
DROP TABLE IF EXISTS `SpesenFormular`;
CREATE TABLE `SpesenFormular` (
  `ID` int NOT NULL AUTO_INCREMENT PRIMARY KEY,
  `Personalnummer` varchar(255) NOT NULL,
  `UserID` int NOT NULL,
  `Datum` datetime NOT NULL,
  `Reiseziel` varchar(255) NOT NULL,
  `Essenskosten` int DEFAULT NULL,
  `Fahrtkosten` int DEFAULT NULL,
  `KM_Anzahl` int DEFAULT NULL,
  `Uebernachtung` int DEFAULT NULL,
  `Verkehrsmittel` varchar(255) NOT NULL,
  `Unterschrift` tinyint NOT NULL DEFAULT '0'
);
```

- Daten befüllen Skript
  
```php
INSERT INTO `SpesenFormular` (`ID`, `Personalnummer`,`UserID`, `Datum`, `Reiseziel`, `Essenskosten`, `Fahrtkosten`, `KM_Anzahl`, `Uebernachtung`, `Verkehrsmittel`, `Unterschrift`) VALUES
(1,'100000',2,'2021-11-29 13:42:47','Jowa Gossau',20,25,0,30,'Zug',0),
(2,'100001',2,'2021-11-29 13:44:18','Graenichen Jowa',10,15,0,40,'Zug',1),
(3,'100002',1,'2021-11-29 13:47:16','Bischofszell BINA',0,0,10,0,'Auto',1);
```

## Speicherort

Die Scripts liegen im mysql Container im initscripts Ordner. `../Projekt/mysql/initscripts/..`

## Problembehandlung

Falls es zu Fehlern kommt, ist es hilfreich den Ordner "mysqldata" zu löschen, da sich dort automatisch generierte tempdaten befinden.
Der Befehl muss zwingend mit sudo ausgeführt werden. `sudo rm -rf /mysql/mysqldata/*`.

## Adminer

Der Zugriff auf den Adminer erfolgt über `localhost:8080`. Die Logindaten müssen mit der Konfiguration des Docker-Container übereinstimmen. Als Server ist "mysql" anzugeben. Über den Adminer lassen sich bequem änderungen an der Datenbank und an den Daten vornehmen. Ausserdem kann über den Adminer ein Export generiert werden, welcher dann in den Initscripts verwendet werden kann.
