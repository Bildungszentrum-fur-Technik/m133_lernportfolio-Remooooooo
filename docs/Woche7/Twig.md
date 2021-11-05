# Twig

Template Engine für PHP mit dem Ziel, die View zu vereinfachen und zu vereinheitlichen. Twig ist nun in der Version 3.x und benötigt mindestens PHP 7.2.5 um Lauffähig zu sein. Falls Twig nicht installiert ist, kann man es einfach über Composer herunterladen. `composer require "twig/twig:^3.0"`

Twig wird für Django, Drupal, und viele weitere Frameworks eingesetzt. Ausserdem gibt es Twig als Front und Backend, also kann es von Devs und Designern eingesetzt werden.

## Funktionsweise

Code Example:

```php
require_once '/path/to/vendor/autoload.php';

$loader = new \Twig\Loader\ArrayLoader([
    'index' => 'Hello {{ name }}!',
]);
$twig = new \Twig\Environment($loader);

echo $twig->render('index', ['name' => 'Remo']);
```

In Twig gibt es einen `loader` (\Twig\Loader\ArrayLoader), welcher Templates ortet und die Umgebung `environemnt`, wo die Konfiguration gespeichert wird.
Der `render` Methode werden 2 Argumente angegeben. Die erste ist das Template und das zweite die Variable.

## Features

Twig bitet viele Vorteile wie das Vererben von Vorlagen, variable Filter, Makros, Erweiterbarkeit und viele mehr.

Ausserdem gibt es in Twig einen Sandbox mode um unbekannten Template code auszuführen.

## Syntax

Twig arbeitet mit drei Arten von Bezeichnern:

`{{ ... }}`
Um den Inhalt einer Variable oder das Ergebnis eines Ausdrucks auszugeben.

Beispiel:

```php
<td>{{ product.name }}</td>
```

___

`{# ... #}`
Für Kommentare, welche nicht weiter verarbeitet werden

___

`{% ... %}`
Für Kommandos und Kontrollstrukturen durch (z.B. loops oder if else)

Beispiel:

```php
<tbody>
    {% for product in products %}
        {% if product.value > 500 %}
                <tr>
                    <td>{{ product.name }}</td>
                    <td>{{ product.description }}</td>

                </tr>
        {% endif %}
    {% endfor %}
</tbody>
```

## Filter

Folgende Filter gibt es in Twig:

|Filter|Beschreibung|
|---|---|
|capitalize| ändert das erste Zeichen einer Zeichenfolge in einen Großbuchstaben.|
|upper| ändert alle Zeichen einer Zeichenfolge in Großbuchstaben.|
|first| zeigt die erste Zeile eines Datenfeldes an.|
|length| gibt die Größe des Variablenwertes zurück.|

## Aufruf

Der Aufruf erfolgt so:

```php
// Welches Twig-Template mit welchen Model grendert werden soll
echo $twig->render('index.html', ['products' => $products] );
```
