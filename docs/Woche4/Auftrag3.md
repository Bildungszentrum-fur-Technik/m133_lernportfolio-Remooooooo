# Auftrag 3

## Aufgabenstellung

Erweitern Sie das CSR-Projekt um die Funktion, dass die dargestellten Elemente aus einer Datei
lesen kann.

## Umsetzung in PHP

Im PHP wird die Funktion response angepasst. Die Hardcoded Elemente werden entfernt und durch file_get_contents ersetzt.
Ausserdem muss die ausgelesene Datei dekodiert werden, da es in JSON geschrieben ist.

```php
function response($response_code,$response_desc)
{
    # File wird ausgelesen
    $json = file_get_contents("../data/name.json");

    // Dekodiert eine JSON Zeichenkette
    $response['data'] = json_decode($json);
    $response['response_code'] = $response_code;
    $response['response_desc'] = $response_desc;

    // Liefert eine JSON Zeichenkette
    $json_response = json_encode($response);
    echo $json_response;
}
```

## Umsetzung im Javascript

Im Javascript habe ich die Funktion generateTableFromJSON mit einem forEach erweitert, welcher für jedes Element 1x durchläuft und alle Namen und vornamen in die Tabelle schreibt.

```js
function generateTableFromJSON(data) 
{
    var tblData = "";

    // For each element in name.js 
    data["data"].forEach(element => 
    {
        tblData += "<tr>";
        tblData += '<td>' + element["firstname"] + '</td>';
        tblData += '<td>' + element["lastname"] + '</td>';
        tblData += "</tr>";   
    });

    return tblData;
}
```

## Ausgelesene Datei

Die Datei, welche ausgelesen wird muss im JSON Format geschrieben sein.

```json
[
    {
        "firstname" : "Name1",
        "lastname": "Nachname1"
    },  
    {
        
        "firstname" : "Name2",
        "lastname": "Nachname2"  
    }
]
```

## Abschluss

Das ganze hat relativ selbständig funktioniert. Beim foreach hatte ich ein wenig Probleme, welche ich dann aber mit Hilfe von Klassenkameraden beheben konnte.

![CSR](/CSR_Auftrag1.png)