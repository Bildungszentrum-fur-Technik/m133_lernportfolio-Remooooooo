# PHP Auftrag 1:

## Auftrag
Gegeben ist der Array aus den Werten 3,7,5,1,8,13,2.
Erstellen Sie ein PHP-Script welches die Werte aus dem Array in einer HTML-Tabelle ausgibt.

## Umsetzung

Meine Idee war es, erst den Array als Variable zu speichern und dann für jede Zahl im Array einen foreach auszuführen.

```php
<?php
//Array initialisieren
$zahlen = array(3,7,5,1,8,13,2.);

// Tabelle erstellen
echo 
"<table><th>Zahlen</th> ";

//Für jede Zahl foreach durchführen
foreach ($zahlen as $z) 
{
    echo "<tr><td>$z</td></tr>"; // Zahl
}

echo "</table>";
?>
```