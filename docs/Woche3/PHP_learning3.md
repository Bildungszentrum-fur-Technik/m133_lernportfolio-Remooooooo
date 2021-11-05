# PHP Learning 3

Heute wurden Folgende Themen behandelt:

- if-Anweisungen
- Vergleichsoperatoren
- Logische Operatoren
- While-Schleifen
- For-Schleifen


## If Anweisung

Mit if wird überprüft, ob eine Bedingung erfüllt oder nicht erfüllt ist. (Analog Java)

Die Funktion gibt einen Boolschen Wert zurück.

Wenn der Wert true ist, wird das if ausgeführt, bei false else.

```php
<?php
$user = "Nils";

if($user == "Nils") 
   {
   echo "Hallo Nils";
   }
else 
   {
   echo "Du bist nicht Nils!";
   }
?>
```


### If verschachteln

Auch in PHP ist eine verschachtelung von if Befehlen möglich.

```php
<?php
$vorname = "Nils";
$nachname = "Reimers";


if($vorname=="Nils")
   {
   echo "Hallo Nils ";

   if($nachname=="Reimers")
      {
      echo "Reimers";
      }
   }
else
   {
   echo "Du bist nicht Nils";
   }
?>
```


Des weiteren kann auch mit else if gearbeitet werden oder mit != überprüfen, ob ein Wert ungleich ist.


## Vergleichsoperatoren in PHP


| Operator          | Name                           | Beschreibung        |
| -------------------- |:------------------------------:| -------------------:|
| $a == $b	| Gleich	|Dieser Vergleich ist erfüllt, falls $a und $b den selben Wert beinhaltet. Sind die Typen der Variablen verschieden, so werden die konvertiert.| 
| $a === $b	| Identisch |Dieser Vergleich ist erfüllt, falls $a und $b den selben Typ und den Inhalt besitzen. Wäre ein Wert vom Typ int und der andere from Typ String, so würde false zurück gegeben werden.| 
| $a != $b	| Ungleich	|Dieser Vergleich ist erfüllt, falls $a und $b nicht den selben Wert beinhaltet. Sind die Typen der Variablen verschieden, so werden die konvertiert.| 
| $a !== $b	| Nicht identisch	|Dieser Vergleich ist erfüllt, falls $a und $b einen unterschiedlichen Typ haben oder einen unterschiedlichen Wert.| 
| $a < $b	| Kleiner	|a muss kleiner als b sein.| 
| $a <= $b	| Kleiner Gleich |a muss kleiner oder gleich b sein.| 
| $a > $b	| Größer	| a muss größer als b sein.| 
| $a >= $b	| Größer Gleich	| a muss größer oder gleich b sein.| 


### Vergleichen von Werten

Das Ergebnis eines Vergleiches ist stets true oder false. Es lässt sich in einer Variable speichern oder direkt für if Anweisungen nutzen.

Beispiel zu Vergleichsoperatoren:

```php
<?php
$int1 = 15;
$int2 = 20;

if($int1 < $int2) { //Vergleich von zwei Variablen
  echo "Int1 ist kleiner als int2 <br />";
}

if($int1 <= 100) { //Vergleich von Variable und Wert
  echo "Int1 ist kleiner oder gleich 100 <br />";
}

//Abspeicherung des Vergleichs in einer Variable
$tier = "Katze";
$string_vergleich = ($tier == "Katze");

echo 'Der Wert der Variable $string_vergleich ist: ';
var_dump($string_vergleich); //Ausgabe welchen Wert die Variable hat

if($string_vergleich) {
   echo " --- Der String Vergleich hatte den true Wert --";
}
?>
```


## Logische Operatoren

- AND:
    Schreibweise: &&
    Beide Bedingungen müssen erfüllt sein.

- OR
    Schreibweise: ||
    Nur eine Bedingung muss erfüllt sein

- !
    Bedingung wird negiert

- ()
    Operatoren können miteinander kombiniert werden

Logische operatoren funktionieren gleich wie in Java und können bei If else Abfragen genutzt werden.

Beispiel Kombination:

```php
<?php
$username = "Nils";
$passwort = "php-einfach";

if( ($username == "Nils" AND $passwort == "php-einfach") OR ($username == "Paul" AND $passwort == "geheim") ) {
  echo "Benutzername und Passwort passten zusammen. <br />";
}

if( $username == "Nils" AND ($passwort == "php-einfach" OR $passwort == "geheim") ) {
  echo "Der Benutzername war Nils, und das Passwort entweder php-einfach oder geheim.";
}
```

Beispiel für Passwortabfrage:

Formualr:

```php
<form action="seite2.php" method="post">
Username:<br>
<input type="Text" name="username" /><br />
Passwort:<br />
<input type="Password" name="passwort" /><br />
<input type="Submit" value="Absenden" /><br />
</form>
```

PHP Skript:

```php
<?php
$username = $_POST["username"];
$passwort = $_POST["passwort"];

if($username=="Nils" AND $passwort=="php-einfach")
   {
   echo "Zugriff erlaubt";
   }
else
   {
   echo "Zugriff fehlgeschlagen";
   }
?>
```

Anstelle der einfachen Nachricht kann auch eine Geheime Nachricht im true versteckt werden.


## While Schleife

Die Anweisung läuft so lange weiter, bis der Return Wert nicht mehr true ist.

Es gibt auch die do-While Schleife, bei der zuerst die Aktion ausgeführt wird und dann erst die Bedingung überprüft wird.

Beispiel mit mehreren überprüfungen:

```php
<?php
$zaehler1 = 0;
$zaehler2 = 0;

$min = -20;
$max = 30;

while($zaehler1 < $max AND $zaehler2 > $min)  {
   echo "Zaehler1: $zaehler1 ; Zaehler2: $zaehler2 <br>";
   $zaehler1 += 2; 
   $zaehler2 -= 3; 
}
?>
```

### Abläufe beeinflussen

Mit den commands `break` und `continue` können Schleifen gestoppt und fortgeführt werden.

#### Beispiel zu Break:

```php
<?php
$max = 30;
$zaehler = 0;
$increment = 2;

while($zaehler < $max) {
   if($zaehler == 10) {
      echo "Bei der Zahl 10 hören wir auf";
      break;
   }
   echo "$zaehler , ";
   $zaehler += $increment; //Erhöht den $zaehler um den Wert $increment
}
?>
```

#### Beispiel zu Continue:
```php
<?php
$max = 30;
$zaehler = 0;
$increment = 2;

while($zaehler < $max) {
   $zaehler += $increment; //Erhöht den $zahler um den Wert $increment
   if($zaehler >= 10 AND $zaehler <= 15) {
      echo "Eine Zahl zwischen 10 und 15 <br>";
      continue;
   }
   echo "$zaehler <br>"; 
}
?>
```


## For Schleife

Die For Schleife ist wie die While Schleife dazu da, eine Anweisung solange auszufüghren, bis die Bedingung true ist.

Wie bei der While Schleife kann mit `break` und `continue` gearbeitet werden.

Syntax:

```php
<?php
for($i=0; $i < 10; $i++) { //i wird auf 0 initialisiert
   echo "$i, ";
}
?>
```

### Unterschiede While - If

Bei der If Schleife befinden sich alle Informationen in der Selben Zeile. Darum wird sie beim hochzählen eher verwendet.

Die While Schleife wird verwendet, wenn unklar ist, wieviele Durchgänge benötigt werden. (Wenn etwas gesucht wird z.B.)