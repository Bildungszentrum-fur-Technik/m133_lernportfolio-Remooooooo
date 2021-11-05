# Datenmodell erstellen

## Auftrag

Erweitern Sie die Vorlage um ein weiteres Datenmodell.

## Twig

Diesesmal findet das Ganze wieder in MVC statt, jedoch diesesmal mit Twig.

Es müssen wieder Files erstellt werden:

- /controllers/cat.php
- /models/CatModel.php
- /views/cat/index.twig.html

## Controller

Neu dazu kommt der Render Befehl, welcher das Index Twig file mit den Daten der Cat rendert.

```php
class Cat extends Controller
{
    // Neue Instanz der Klasse
    public function index($name = '', $rasse = '')
    {
        $cat = $this->model('CatModel');
        $cat->name = $name;
        $cat->rasse = $rasse;

        // Rendert das Twig file mit den Dalten cat
        echo $this->twig->render('cat/index.twig.html', ['cat' => $cat] );                
    }
}
```

## Model

Das Model ist gleichbleibend.

```php
<?php

class CatModel
{
    public $name;
    public $rasse;
    
}
```

## View

Die View ist ein Extend des Base Layout und der Syntax ist nun gemäss Twig.

```php
{% extends "base/layout.twig.html" %}

{% block content %}
<!-- Wir überschreiben den Content-Block -->

<h1 class="mt-5">KATZE</h1>


Name : {{cat.name}}, Rasse : {{cat.rasse}}

{% endblock %}
```

## Ausgabe

Der Aufruf lautet:
`http://localhost:8000/cat/Nidalee/Leopard`

So hat das Ganze ausgesehen:
![Cat](/Cat.png)