# Datenobjekt erstellen

## Auftrag

- Neues "Datenobjekt" erstellen (Controller, Model, View)

## Umsetzung in MVC

Da das ganze in MVC erstellt wird, benötige ich erst einige neue Dateien:

- /controllers/dogcontroller.php
- /models/Dog.php
- /views/dog/index.php

## Controller

Der Controller ist eine Unterklasse des Controller mit der Funktion Index, welche eine neue Instanz der Klasse Dog erstellt mit den angegebenen Parametern.

Ausserdem befindet sich der View Aufruf in dieser Klasse.

```php
<?php

class Dogcontroller extends Controller
{
    public function index($name = '', $age = 0, $sex = 'male')
    {
        // Erstellt neue Instanz der Klasse Dog
        $dog = $this->model('Dog');
        $dog->name = $name;
        $dog->age = $age;
        $dog->sex = $sex;

        // Welche View wird aufgerufen und die Daten werden mitgegeben
        $this->view('dog/index', ['dog' => $dog]);
    } 
}
```

## Model

Im Model wird die Klasse Dog erstellt mit den gewünschten Eigenschaften des Objektes.

```php
<?php

class Dog
{
    public $name;
    public $age;
    public $sex;
    
}
```

## View

Im View wird die Ausgabe definiert und die Parameter aufgerufen.

```php
My dog is called <?=$data['dog']->name?>, is <?=$data['dog']->age?>  and a <?=$data['dog']->sex?>
```

## Ausgabe

So hat das ganze ausgesehen:
![Dog](/Dog.png)
