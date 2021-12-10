# Gaestezaehler

## Aufgabe

Für eine Homepage sollen Sie einen Gäste-Zähler erstellen, welche die Anzahl Aufrufe der Seite jeweils ausgibt.
Dabei soll aber verhindert werden, dass jemand durch Aktualisieren des Browserfensters den Zähler erhöhen
kann.
Folgende Vorgaben sind einzuhalten:
Arbeiten Sie mit Sessions
Der Zählerstand soll in ein File geschrieben werden
Erst durch Schliessen des Browsers darf beim nächsten Zugriff der Zähler erhöht werden
Zugabe
Auch durch das Schliessen des Browsers darf der Zähler beim nächsten Zugriff nicht erhöht werden.

## Code

```php
<?PHP
session_start();
?>
<html>
    <head>
      <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
      <title>Gaestezaehler</title>
    </head>
    <body>
        <?PHP
            if (isset($_SESSION["zaehler"])){
                echo "Die Seite wurde bereits geladen";
            }
            else{
                $data = fopen("Gaestezaehler.txt", "r+");
                $zaehler = fgets($data);
                echo "$zaehler";
                if($zaehler != ""){
                    $zaehler += 1;
                }
                else{
                    $zaehler = 1;
                }
                    
                fclose($data);
                $data = fopen("zaehler.txt", "w");
                fwrite($data, "$zaehler");

                $_SESSION["zaehler"] = 1;
                fclose($data);
            }
        ?>
    </body>
</html>
```
