# Prepared Statements

Prepared Statements sind Datenbankfunktionen, welche mit Übergabeparametern befüllt wird. Am Anfang werden für die Parameter keine Werte angegeben, sonder sie sind mit Platzhaltern gefüllt.
Der Vorteil von den Prepared Statements ist, dass so kontrolliert werden kann, was für Daten sich in den Strings befinden. So können SQL Injections verhindert werden.

Der Aspekt der Sicherheit ist nicht der einzige Vorteil. Ausserdem sind Prepared Statements schneller und benötigen weniger Ressourcen als eine normale Datenbankabfrage, wenn es um Aufgaben geht, welche wiederholt werden.

Die Umsetzung eines Prepared Statments erfolgt in 3 Schritten. Erst muss es vorbereitet werden, dann Verarbeitet und zum schluss ausgeführt.

## SQL Injection

SQL Injection bedeutet, wenn in einen String ein SQL Befehl mitgegeben wird. Jener kann verschiedenen Schaden anrichten wie z.B. alle Daten löschen oder dem Angreifer Adminrechte vergeben.
Das ganze kann mit einer sauberen Inputvalidierung, kombiniert mit Sanitizen und der Funktion "MySQLrealescapestring" abgefangen werden.

## Vergleich Prepared Statements und normaler Zugriff

Bei der Manuellen eingabe werden die Werte bereits zum Zeitpunkt der Ausführung einem Befehl zugeordnet. So lässt sich nicht überprüfen, ob der eingegebene String schadhaften Code enthaltet oder doch nur den Namen des Haustieres.

## PDO Verbindung

PDO ist die Schnittstelle des Programmes und der Datenbank. Jene verwenden wir in der LB.
Sie ist rein OOP, die Verbreitung ist daher eingeschränkt. Sie bietet eine hohe performance und ist eine einheitliche Schnittstelle für viele Datenbanken. Die Performence ist ähnliche wie bei mysqli.
Die PDO Verbindung bei unserem Projekt wird im `database.php` gesteuert und konfiguriert.

### MySQL Verbindung

Die MySQL Verbindung ist die ursprüngliche Schnittstelle zwischen Programm und Datenbank gewesen, jene wird seit PHP Version 7 nicht mehr unterstützt.
Die Performance ist sehr niedrig und ist nicht OOP gestaltet.

## MySQLi Verbindung

MySQLi ist die verbesserte Variante von mySQL.
Sie ist prozedural und OOP, was viele Möglichkeiten bietet, was ein Nachteil ist, da viele Wege zum Ziel führen und keine klare Struktur herrscht.
MySQLi bietet eine hohe performance hat eine hohe Verbreitung, da einfach umzusetzen ist.
