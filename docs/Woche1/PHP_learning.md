# PHP Learning Woche 1

Diese Woche stehen folgende Schritte auf dem Programm:

    - Erste Schritte
    - Text ausgeben per echo
    - Kommentare
    - Variablen

PHP wird grundsätzlich von oben nach unten gelesen und ausgeführt, da es eine Skriptsprache ist.
Damit PHP funktioniert, muss es auf dem Client oder Server installiert sein. (XAMPP oder Docker)


## Erste Schritte

### PHP Info

Gibt Infos über PHP aus und man sieht ob PHP überhaupt installiert ist.

```php
<?php
phpinfo();
?>
```


### PHP Code Einbinden


In einer PHP-Datei können PHP und HTML Code enthalten sein. Die HTML-Befehle schreibt man wie gewohnt in die .php-Datei.

Für den Codeteil von PHP kommt am Anfang ```<?php"``` und zum SChluss ```?>``` hin. 

Beispiel:

```php
<!DOCTYPE html>
<html> 
<head>
	<meta charset="UTF-8" />
	<title>Mein erstes PHP-Script</title> 
</head>
 
<body>
<h1>Herzlich Willkommen</h1>

<p>Dies ist mein erstes PHP-Datei. Eine Scriptumgebung könnt ihr wie folgt starten: 
<?php
echo "Mittels echo können Daten ausgegeben werden";
?></p>

<p>Später könnt ihr in PHP dynamische Inhalte erzeugen. Ein einfaches Beispiel ist das aktuelle Datum auszugeben: 
<?php
echo date("d.m.Y H:i:s");
?></p>
 
</body>
</html>

```

Sobald z.B. http://localhost/test.php aufgerufen wird, wird der PHP Interpreter aktiv und wertet Alle PHP Skriptumgebungen aus und fügt sie in die Website ein.


## Text ausgabe per Echo

Ein Text kann in PHP mittels ```echo``` ausgegeben werden. Wie bereits erwähnt erhält der User nur die Ausgabe des Skripts und nicht das Skript selber. Dieses wird nur auf dem Server ausgeführt.

```php
<?php
echo "Hello World";
?>
```
### Maskierungszeichen
Falls man in einer Echo Ausgabe "" benutzen will, muss man Maskierungszeichen verwenden, da der Interpreter die Zeichen sonst falsch deutet.

```php
<?php
echo "Hello \"World\"";
?>
```

Das selbe tritt auch auf mit /. Dafür ebenfalls ein Maskierungszeichen verwenden.

```php
<?php
echo "D:\\xampp";
?>
```

### HTML Befehle

PHP wird häufig mit HTML verwendet. Man kann darum auch HTML Befehle für die Darstellung des Textes verwenden.
So zum Beispiel wird der Text fett geschrieben.

```php
<?php
echo "<b>Hello World</b>";
?>
```


## Kommentare in PHP

Kommentare werden in PHP nicht vom Interpreter gelesen sondern von diesem Ignoriert.

### Kommentare Definieren

Alles was nach dem doppeltem Slash oder nach der Raute steht wird ignoriert.

```php
<?php
echo "Hallo Welt! <br>";
//Dies ist ein Kommentar

#Ein weiterer Kommentar - Ausgabe des Text
echo "Wie ihr feststellt, sind die Kommentare bei der Ausgabe nicht sichtbar.";
?>
```

### Mehrzeilige Kommentare

Ähnlich wie in anderen Sprachen(z.B. Java) werden mehrzeilige Kommentare mit Slash und Stern markiert.

```php
<?php
/* Die erste Zeile des Kommentars
Zweite Zeile des Kommentars
Die letzte Zeile des Kommentars */
echo "Hallo Welt. Wie ihr feststellt, wird nur dieser Text angezeigt. Die Kommentare vor sind nicht sichtbar.";
?>
```


## Variablen

Variablen können verschiedene Werte enthalten, z.B. einfach Zeilen oder Texte, aber auch komplexere Strukturen wie Beispielsweise Listen.

In PHP werden jene Werte in ```PHP Variablen``` gespeichert und später mit Hilfe von ```echo``` ausgegeben.

Variablen in PHP beginnen immer mit einem `$`, danach der `Variablen-Namen`.

Dies sieht dann so aus:

```php
<?php
$name = "Remo Stark";
?>
```

Variablen Namen sind Case sensitiv.

### Variablen-Typen

PHP ist zwar eine typlose Programmiersprache, ermittelt jedoch selbst den Wert der Variable und legt selbst fest um was es sich handelt.

 Folgende Typen gibt es in PHP:

- Integer: Eine Integer-Variable enthält nur Ganzzahlen, d.h. Zahlen ohne Komma.
- String: Dies ist eine Variable, die einen Text/Satz/Wort enthält.
- Float: Eine Fließkommazahl, d.h. eine Zahl mit Komma. Man verwendet aber die englische Schreibweise und somit einen Punkt statt dem deutschen Komma.
- Double: In PHP das gleiche wie float.
- bool: true oder false 

Beispiel:


```php
<?php
$integer = 15; //Ein Integer
$string = "Ganz viel Text"; //Ein String
$float = 15.5; //Eine Fliesszahl
$bool = true;
?>
```

### Variable ausgeben

Mittels echo Befehl die Variable über den Variablennamen aufrufen.

```php
<?php
$name = "Nils Reimers";
echo "Mein Name ist $name";
?>
```

### Variablen überschreiben

Der Variable wird einfach ein neuer Wert zugewiesen.

```php
<?php
$name = "Paul Meier";
echo "Zuerst heiße ich $name <br />";

$name = "Stefan Müller";
echo "Dann ist mein Name $name";
?>
```


### Text anhängen

Mit einem . vor dem = wird ein Wert an die Variable angehängt.

```php
<?php
$name = "Nils ";
$name .= "Reimers";
echo $name;
?>
```

Theoretisch würde dies auch mit einem echo funktionieren.

```php
<?php
$name = "Nils";
echo "Mein Name ist ".$name." Reimers";
?>
```