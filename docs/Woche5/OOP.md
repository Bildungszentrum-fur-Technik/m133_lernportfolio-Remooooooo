# Objekt Orientiertes Programmieren

## 1 Wie wird PHP instanziert

In PHP werden mit `new` Objekte einer Klasse instanziert.

Die Objekte sind unabhängig voneinander instanziert und können selber befüllt werden.

```php
<?php
class User {
   //...
}
 
$remo = new User();
$franz = new User();
```

## 2 Was bedeutet der Pfeil

Durch den Pfeil kann man auf Eigenschaften von Objekten zugreiffen wie zum Beispiel Variablen. Ebenso ruft man auch Methoden von Klassen mittels Pfeil auf.

```php
<?php
class User { 
   // ...
}
 
$remo = new User(); //Neues Objekt
$remo->name = "Max Mustermann"; //Setzen der Variable
echo "Hallo $max->name"; //Abruf der Variable
 
$remo->setEmail("max@muster.de"); //Aufruf der Methode setEmail
```

## 3 Was bedeutet `this`

Wenn man Eigenschaften oder Methoden innerhalb einer Klasse aufruft, verwendet man `$this`

```php

$this->email("überschreiben@dervariable.de")

```

## 4 Zugriffsmodifizierer in PHP

| Begriff          | Beschreibung        |
| -------------------- | -------------------:|
| public	|  Public bedeutet Voller Zugriff, jeder kann auf jene Variable oder Methode zugreifen.	|
| private| Nur innerhalb der Klasse kann auf die Variablen und Methoden zugegriffen werden. |
| protected	| Auf die Variable oder Methode kann nur innerhalb der Klasse und in vererbten Klassen zugegriffen werden.|

Falls Methoden aufgerufen werden, welche z.B. Protected sind(von ausserhalb), erscheint ein Fatal Error. Ausserdem sind die Eigenschaften nicht sichtbar.

Wie bereits gelernt, sollten wir den Modifizierer public nur verwenden, wenn wir wirklich wollen dass von aussen darauf zugegriffen wird, ansonsten mit private oder protected arbeiten.

## 5 Beispiele zu Konstruktoren, Methoden, Klassen

### Methoden

Methoden können mit Sichtbarkeitsmodifikatoren ergenzt werden. Falls keiner angegeben wird ist die Methode Public.
Ausserdem wird bei der Methode direkt die Übergabeparameter mitgegeben.

Wichtig:
`Der Return Datentyp darf nicht angegeben werden wie in Java.`

```php
<?php
class User {
 function methode1() { //Public Methode ohne Parameter 
 }
 
 public function methode2($parmater) { //Public Methode mit Paramter
 }
 
 protected function methode2($parmater1, $parameter2) { //Protected Methode mit zwei Paramtern
 }
 
 private function methode3() { //Private Methode ohne Paramter
 }
}
?>
```

Beim Aufrufen einer Methode innerhalb der Klasse verwenden wir also `$this`. Dann wäre es in dem Beispiel:
`$this->Methode1()`.

### Konstruktor

In PHP gibt es bereits eine Methode, welche aufgerufen wird wenn ein Objekt einer Klasse erzeugt wird. Nämlich `__construct()`.

Dem Konstruktor kann wie Java bereits eine Methode angegeben werde, welche beim erstellen ausgeführt wird. Ebenso können Parameter und Variablen direkt gesetzt werden.
Wenn Parameter mitgegeben werden, müssen jene Analog Java auch direkt beim erstellen mitgegeben werden. Im Bepsiel ist es z.B.
`new User("Name,"Email")`.

```php
<?php
class User {
	public $erstellungsdatum;
	public $name;
	public $email;
	
	public function __construct($name, $email = "") {
		$this->name = $name;
		$this->email = $email;
		$this->erstellungsdatum = date("d.m.Y H:i:s");
	}
}

$max = new User("Max Mustermann", "max@muster.de");
echo "Das Objekt von $max->name wurde erstellt am $max->erstellungsdatum";
?>
```

## 6 Vererbung in PHP

Mit der Vererbung ist es möglich, eine Hierarchie zwischen den Klassen zu erzeugen. Es wird mittels `extends` vererbt. Vererben ist dann Praktisch, wenn es unterklassen gibt, welche identische Variablen oder Methoden benötigen, damit man jene nicht einzeln ausprogrammieren muss.

Wenn man die selbe Methode der Oberklasse aufrufen will, funktioniert das mit:
`parent::Funktion()`

Anderenfalls können funktionen der Oberklasse auch überschrieben werden.

```php
class Produkt {
	public $titel;
	public $preis;
	
	function gesamtpreis($stueckzahl) {
		$gesamtpreis = $this->preis*$stueckzahl;
		
		if($stueckzahl >= 10) {
			$gesamtpreis = $gesamtpreis*0.8;
		}
		return $gesamtpreis;
	}
}

class Buch extends Produkt {
	public $autor;
}

class Film extends Produkt {
	public $regisseur;
}

class CD extends Produkt {
	public $band;
}
```
