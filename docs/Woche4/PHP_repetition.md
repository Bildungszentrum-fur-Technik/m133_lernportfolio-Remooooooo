# PHP Repetition

## 0

- Welche Variablen sind gültig? 
  
```php
$preis //- Gültig  
$1preis //- keine Zahl am anfang  
$_preis //- Gültig  
$else //- Gültig  
$gesamtpreis12 //- Gültig  
$gesamt-preis //- unglültig, darf kein - enthalten  
$MeNg //- Gültig  
```

## 1

Was wird ausgegeben?

```php
<?php
$j = "Hallo";
$k = "$j \"Onkel\" ";
echo $k;
?>
```

Die Ausgabe ist Hallo "Onkel". Die \ werden genutzt damit die " dargestellt werden.

## 2

Was ist die Ausgabe von:

```php
<?php
$a = "Hallo ";
$a .= "Welt";
echo
```

Es wird Hallo Welt ausgegeben, da die Variable(String) `$a` erweitert wird.

## 3

Was ist die Ausgabe von:

```php
<?php
$a = "Hallo";
$b = "Welt";
echo $a." ".$b."<br />"
?>
```

Es wird Hallo Welt mit einem Umschlag ausgegeben.

## 4

Was ist die Ausgabe von:

```php
<?php
$preis = 49.90;
echo "Die Variable $preis enthält den Wert: $preis";
?>
```

Die ausgabe ist 49.90.
Mann muss beim ersten `$preis` noch ein `\` machen, damit der Name der Variable ausgegeben wird.

## 5

Was ist die Ausgabe von:

```php
<?php
$preis = 49.90;
echo 'Die Variable $preis enthält den Wert: $preis';
?>
```

Einfache Hochkomma führen keine Variablen aus, nur doppelte. 

## 6

Was ist die Ausgabe von:

```php
<?php
$preis = 49.90;
echo 'Die Variable $preis enthält den Wert:'.$preis;
?>
```

Diese Ausgabe ist Korrekt und es gibt aus:
Die Variable $preis enthält den wert 49.90.

## 7

Was ist die Ausgabe von:

```php
<?php
$familie = array("Vater","Mutter","Tochter","Sohn");
echo "$familie[3]<br />";
echo "$familie[1]<br />";
echo "$familie[0]<br />";
echo "$familie[4]<br />";
echo "$familie[2]<br />";
?>
```

Es wird in der Reihenfolge ausgegeben:

Sohn, Mutter, Vater, ERROR, Tochter

Der Index beginnt bei 0, der Index 4 ist nicht vergeben.

## 8

Was ist die Ausgabe von:

```php
<?php
$n = 5; 
$o = 8;
echo $n + $o;
echo $n - $o;
echo $n * $o; 
echo $n / $o; 
echo $n % $o; 
?>
```

Die ausgabe ist ein wenig unschön, da alles auf einer Linie daher kommt:
`13-3400.6255`    
Linie 1= 13  
Linie 2= -3  
Linie 3= 40  
Linie 4= 0.625  
Linie 5= 5, dies gibt den Rest an

## 9

Was ist der Unterschied zwischen:

```php
$a == $b;
$a === $b;
```

`==` überprüft auf gleichheit, `===` ob es identisch ist. Das heisst es muss auch der Datentyp gleich sein und nicht nur der Inhalt.
Z.B. bei `==` int 0 und string 0 wäre true, bei `===` wäre es false.