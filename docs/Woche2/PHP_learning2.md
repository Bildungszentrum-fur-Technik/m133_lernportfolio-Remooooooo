# PHP learning 2 

Heute wurden folgende Themen abgehandelt:

- Rechnen mit Variablen
- $_GET und $_POST
- Arrays

## Rechnen mit Variablen

Wenn auf eine Variable eine Zahl gespeichert wird, darf kein "" verwendet werden.

```php
<?php
$zahl1 = 10;
$zahl2 = 5;
echo "Zahl1: $zahl1 <br />";
echo "Zahl2: $zahl2";
?>
```


Um zwei Zahlen mitteinander zu verrechnen, einfach opperatoren verwenden. Die zwei Zahlen müssen nicht unbedingt auf Variablen gespeichert sein, es kann auch einfach eine fixe Zahl verrechnet werden (z.B. $Zahl + 5)
Das Ergebnis der zwei Zahlen wird dann auf einer neuen Variablen gespeichert.

```php
<?php
$zahl1 = 10;
$zahl2 = 5;
$ergebnis = $zahl1 + $zahl2;
echo "Ergebnis: $ergebnis";
?>
```

Hier noch weitere Beispiele:

```php
<?php
$zahl1 = 10;
$zahl2 = 5;
echo $zahl1 + $zahl2; //addieren
echo "<br />";
echo $zahl1 - $zahl2; //subtrahieren
echo "<br />";
echo $zahl1 * $zahl2; //multiplizieren
echo "<br />";
echo $zahl1 / $zahl2; //dividieren
echo "<br />";
echo pow($zahl1,$zahl2); //Zahl1 hoch Zahl2 (10^5)
echo "<br />";
echo sqrt(64); // Wurzel von 64
echo "<br />";
echo 2*$zahl1 + 5*$zahl2 - 3; //Berechnet 2*10 + 5*5 - 3
?>
```

### Dekrementieren und Inkrementieren

Wie in anderen Sprachen ist es möglich, eine Zahl zu inkrementieren. 

```php
<?php
$erhoehen = 1;
$erhoehen++;
echo $erhoehen;
?>
```

Das selbe ist auch möglich mit `--` anstelle `++`.(Dekrementieren)

### Kurzschreibweisen

Ebenfalls ist es in PHP möglich, kurzschreibweisen zu verwenden.

```php
<?php
$zahl = 1;
$zahl += 10;
echo $zahl;
?>
```

### Fliesskommazahlen

Bei Fliesskommazahlen muss man beachten, dass die englische Schreibweise benutzt wird.

```php
<?php
$zahl1 = 2.5;
$zahl2 = 5.5;
$ergebnis = $zahl1 * $zahl2;
echo "Ergebnis: $ergebnis";
?>
```


## GET und POST

Get und Post werden in PHP verwendet, um Werte zwischen verschiedenen Seiten zu übertragen.

### Datenübergabe mittels GET

Bei der GET Methode werden die Variablen mittels URL übergeben. Dies sieht dann z.B. so aus. Die Reihenfolge der Variablen spielt keine Rolle.
`get.php?vorname=Max&nachname=Meier`

Im PHP Skript wird es folgenderweise umgesetzt:

```php
<?php
$vorname = $_GET['vorname'];
$nachname = $_GET['nachname'];
echo "Hallo $vorname $nachname";
?>
```

GET sollte nicht verwendet werden, wenn es sich um Vertrauliche Informationen handelt, da diese sichtbar sind und gecached werden können. 
Ausserdem gibt es ein Zeichenlimit für GET requests. Dies hängt davon ab, welcher Browser verwendet wird und auch vom verwendeten Server. Meist sind es 1kB bis 4kB.

GET Variablen werden meist genutzt um Links mit dynamischen Werten auszustatten. Z.B. mit einer ID in einem Shop um jenes Objekt darzustellen.

- GET requests can be cached
- GET requests remain in the browser history
- GET requests can be bookmarked
- GET requests should never be used when dealing with sensitive data
- GET requests have length restrictions
- GET requests is only used to request data (not modify)

### Datenübergabe mittels POST

Im Gegensatz zu GET wird POST im HTML Body übertragen. (Meistens via ein Formular)

Vorteile von POST:
- POST requests are never cached
- POST requests do not remain in the browser history
- POST requests cannot be bookmarked
- POST requests have no restrictions on data length

Dieses könnte so aussehen:

```php
<form action="seite2.php" method="post">
Vorname: <input type="text" name="vorname" /><br />
Namename: <input type="text" name="nachname" /><br />
<input type="Submit" value="Absenden" />
</form>
```

Es ist darauf zu achten, dass alle Felder einen Unique Namen besitzen. Falls dies nicht der Fall ist, wird nur das Letzte Feld übermittelt und überschreibt alle vorherigen Values.

Mit folgendem PHP Skript wird die Eingabe abgerufen:

```php
<?php
$vorname = $_POST["vorname"];
$nachname = $_POST["nachname"];
echo "Hallo $vorname $nachname";
?>
```

### GET und POST kombiniert

Man kann GET und POST kombinieren. Dazu muss im Formular in der Action ein Value mitgegeben werden. In diesem Fall ist es `?wochentag=Sonntag`.

Formular:
```php
<form action="seite2.php?wochentag=Sonntag" method="post">
Vorname: <input type="text" name="vorname" /><br />
Namename: <input type="text" name="nachname" /><br />
<input type="Submit" value="Absenden" />
</form>
```

Und so werden sie wieder abgerufen:
Skript:
```php
<?php
$vorname = $_POST["vorname"];
$nachname = $_POST["nachname"];
$wochentag = $_GET["wochentag"];

echo "Hallo $vorname $nachname. Treffen wir uns am $wochentag?";
?>
```


## Arrays

Ein Array ist eine geordnete Liste welche Zahlen oder Strings beinhalten kann.

### Arrays Definieren

In einer Variable kann nur ein Wert gespeichert werden. In einem Array können beliebig viele Werte gespeichert werden.

```php
<?php
$wochentage = array("Sonntag","Montag","Dienstag",
"Mittwoch","Donnerstag","Freitag","Samstag");
echo $wochentage[1]; //Zugriff auf den Index 1, Start bei 0
?>
```

### Assoziativer Array

Man kann für einen Wert innerhalb eines Arrays einen Key zuweisen, über welchen man den Value aufrufen kann.

```php
<?php
$wochentage = array(
"so" => "Sonntag",
"mo" => "Montag",
"di" => "Dienstag",
"mi" => "Mittwoch",
"do" => "Donnerstag",
"fr" => "Freitag",
"sa" => "Samstag");

echo $wochentage["mo"]; // Ausgabe Montag
$wochentage["mo"] = "Monday"; // Überschreiben von Montag
echo $wochentage["mo"]; // Ausgabe Monday
?>
```

### Werte einem Array hinzufügen

Wenn [] hinter einem vorhanden Array steht, wird ein Wert hinzugefügt. Dies geht auch mit leeren Arrays.

```php
<?php
$mitarbeiter = array("Bob","Peter");
$mitarbeiter[] = "Lisa";

echo $mitarbeiter[2]; //Ausgabe Lisa
?>
```

Man kann auch bei assoziativen PHP arrays Keys angeben.

```php
<?php
$mitarbeiter = array(
   "Bob" => "Bob Meier",
   "Peter" => "Peter Schröder");
$mitarbeiter["Lisa"] = "Lisa Müller";

echo $mitarbeiter["Lisa"];
?>
```


### Arrays in Strings konvertieren

Mit `implode` lassen sich Elemente eines Arrays zu einem String verbinden. So können formatierte Listen schön ausgegeben werden.

```php
<?php
$namen = array("Paul", "Max", "Hans");

echo "Namen per Komma trennen: <br>";
$namenStr = implode(", ", $namen);
echo $namenStr; 

echo "<br><br>";
echo "Ein Name pro Zeile: <br>";
echo implode("<br>", $namen);
```


### Strings in Arrays konvertieren

Mit `explode` kann ein String in einen Array konvertiert werden. Der String wird an allen Trennzeichen getrennt.

```php
<?php
$text = "Paul,Max,Hannes";
$namen = explode(",", $text ); //Konvertierung des Strings in ein Array
echo "<pre>"; var_dump($namen); echo "</pre>"; //Formartierte Ausgabe des Arrays
```


### Mehrdimensionale Arrays

In einem Array kann ein weiterer Array gespeichert werden(Usw.). Jene Arrays werden mehrdimensionale Arrays gennant und mit der Dimension unterschieden. Ein normaler Array ist ein 1-dimensionaler Array.

```php
<?php
$mitarbeiter = array(
  array("Klaus", "Zabel"),
  array("Arnie", "Meier"),
  array("Willi", "Brand")
);

//Daten ausgeben
echo "Vorname: ".$mitarbeiter[0][0]; //Ausgabe Klaus
echo " Nachname: ".$mitarbeiter[0][1]; //Ausgabe Zabel
?>
```
Es werden nun beim Aufruf 2 Indexe angegeben. 


### Kombination Normale Arrays und assoziativer Array

```php
<?php
$mitarbeiter = array();
$mitarbeiter[] = array("Vorname"=>"Klaus",
                       "Nachname"=>"Zabel");

$mitarbeiter[] = array("Vorname"=>"Arnie",
                       "Nachname"=>"Meier");

$mitarbeiter[] = array("Vorname"=>"Willi",
                       "Nachname"=>"Brand");

//Daten ausgeben
echo "Vorname: ".$mitarbeiter[0]["Vorname"];
echo " Nachname: ".$mitarbeiter[0]["Nachname"];
?>
```

In diesem Beispiel ist in einem Normalen Array ein assoziativer Array gespeichert. Also muss auch der Key im echo angegeben werden.

Noch ein Beispiel mit mehreren Dimensionen:
```php
<?php
$mitarbeiter = array();
$mitarbeiter["Klaus"]["Vorname"] = "Klaus";
$mitarbeiter["Klaus"]["Nachname"] = "Zabel";
$mitarbeiter["Klaus"]["Kinder"][] = "Klaus-Junior";
$mitarbeiter["Klaus"]["Kinder"][] = "Kind2";

//Daten ausgeben
echo "Vorname: ".$mitarbeiter["Klaus"]["Vorname"];
echo " Nachname: ".$mitarbeiter["Klaus"]["Nachname"];
echo "<br> Er hat ";
echo count($mitarbeiter["Klaus"]["Kinder"])." Kinder";

//Ausgabe von Kind1:
//$mitarbeiter["Klaus"]["Kinder"][0];

echo "<br> Kinder: <br>";
foreach($mitarbeiter["Klaus"]["Kinder"] AS $name) {
   echo $name."<br>";
}
?>
```

Bei diesem Beispiel haben wir den Array mit dem Mitarbeiter Klaus. Für Ihn wird ein Vor und Nachname gespeichert. Unter dem Key Kinder wird ein weiterer Array hinzugefügt und jedes bekommt gleich einen Namen.


### Arrays durchsuchen

Mit der Funktion `in_array` lässt sich überprüfen, ob ein Wert in einem Array vorkommt.

```php
<?php
$mitarbeiter = array("Bob","Peter","Lisa");
$name = "Bob";
if(in_array($name,$mitarbeiter)) {
   echo "Der Name $name ist in dem Array enthalten";
}
?>
```

Bei assoziativen Arrays gibt es die Funktion `array_key_exists`.

```php
<?php
$mitarbeiter = array("Bob" => "Baumeister", "Klaus" => "Muster");
$key = "Bob";

if(array_key_exists($key, $mitarbeiter)) {
  echo "Das Element $key hat den Wert: ".$mitarbeiter[$key];
} else {
  echo "Das Array hat keinen Schlüssel $key";
}
?>
```


### Elemente eines Arrays iterieren

Die Funktion count zählt die Elemente eines Arrays. Dazu verwenden wir eine for Schöleife um alle Elemente durchzuzählen.

```php
<?php
$namen = array("Klaus", "Anna", "Dieter");

echo "<br> Durchlaufen des Arrays mittels for-Schleife: ";
for($i=0; $i<count($namen); $i++) {
  echo $namen[$i].", ";
}

echo "<br> Durchlaufen des Arrays mittels foreach-Schleife: ";
foreach($namen AS $name) {
  echo $name.", ";
}
?>
```


### Arrays Sortieren

Die Funktionen sort() sortiert aufsteigend und die Funktion rsort() absteigend. Die Funktion ist Case sensitive und Sortiert erst Gross und dann Kleinbuchstaben.

```php
<?php
$namen = array("Klaus", "Dieter", "Anna", "Melissa", "arne");

sort($namen);
echo implode(", ", $namen);
?>
```

### Weitere Array Funktionen


| Funktion            | Beschreibung                   |
| ----------------- |:------------------------------:|
|```array_key_exists($key, $array)```       | Überprüft, ob der Schlüssel $key im $array existiert.     | 
| ```count($array)```  | Gibt die Anzahl der Elemente im Array zurück |
| ```in_array($suchwert, $array)```  | Überprüft, ob der Wert $suchwert im $array existiert. | 
| ```sort($array)```  | Sortiert ein Array aufsteigend, vom kleinsten zum größten Wert (A -> Z). | 
| ```rsort($array)```  | Sortiert ein Array absteigend, vom größten zum kleinsten Wert (Z -> A). | 
| ```shuffle($array)```  | Mischt zufällig die Elemente des Arrays. | 