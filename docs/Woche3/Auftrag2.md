# PHP Auftrag 2:

## Auftrag

Erstellen Sie Formular Bier:  
Für die Firma Brauerei Locher müssen Sie ein Interessen-Formular erstellen, welches folgenden Inhalt abdeckt:
- Anrede (Radiobutton: Mann, Frau, undefiniert)
- Name, Adresse
- Mailadresse
- Auswahl der Interessen an Produkten:
    - Nicht alkoholische Getränke
    - Schnäpse
    - Bier
- Freitextfeld für Bemerkungen


## Umsetzung Formular

Beim  bin ich Schritt für Schritt der Anleitung (Und Teils auch aus dem Internet) gefolgt und habe die benötigten Inhalte mit Checkboxe, Radiobutton und Freitextfeldern gelöst.

```php
<?php
$background = "https://images5.alphacoders.com/356/thumbbig-356350.jpg";
?>
<html>

<head>
    <style type="text/css">
        body {
            background-image: url('<?php echo $background; ?>');
            background-size:  1500px;
        }
    </style>

    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
</head>

<body>
</body>

</html>

<form action="index.php" method="post">

<h1>Brauerei Locher</h1>
    <div class="form-group">
        <h2>Anrede</h2>
        <input type="radio" name="anrede" id="male"/>
        <label for="h">Männlich</label>
        <br>
        <input type="radio" name="anrede" id="female"/>
        <label for="w">Weiblich</label>
        <br>
        <input type="radio" name="anrede" id="divers"/>
        <label for="d">Divers</label>
        <br>
    </div>

    <br>

    <div class="form-group">
        <label for="name">Name</label>
        <br>
        <input type="text"  name="name" id="name" placeholder="Bitte Namen eingeben">
    </div>

    <br>

    <div class="form-group">
        <label for="adresse">Adresse</label>
        <br>
        <input type="text"  name="strasse" id="strasse" placeholder="Bitte Strasse eingeben"> <br><br>
        <input type="text"  name="plz" id="plz" placeholder="Bitte Postleitzahl eingeben"><br><br>
        <input type="text"  name="ort" id="ort" placeholder="Bitte Ort eingeben"><br><br>
    </div>

    <br>

    <div class="form-group">
        <label for="email">E-Mail</label><br>
        <input type="email" name="email" id="email"  placeholder="Bitte E-Mail eingeben">

    </div>
    <div class="form-check">
        <h2>Interessen</h2>
        <label for="nichtalkoholisch">Nicht alkoholische Getränke</label>
        <input type="checkbox" name="nichtalkoholisch" id="nichtalkoholisch" ><br><br>
        <label for="schnaps">Schnaps</label>
        <input type="checkbox" name="schnaps" id="schnaps" ><br><br>
        <label for="bier">Bier</label>
        <input type="checkbox" name="bier" id="bier" ><br>

    </div>

    <br>

    <div class="form-group">
        <label for="bemerkung"><h2>Bemerkungen</h2></label><br>
        <textarea name="bemerkung" id="bemerkung" style="width: 700px"></textarea>
    </div>
    <input type="submit" class="btn btn-primary" value="Absenden">
</form>
```

## Umsetzung PHP Skript

Das ganze soll dann mit dem Submit Button übergeben werden und auf einer neuen Seite dargestellt werden.

Leider hat bei mir das darstellen der Interessen nicht geklappt, was ich im Unterricht nachfragen werde.
Nachtrag: -> Ich habe nun mit einem If abgefragt, ob die Checkbox true oder false zurückgibt.

Der Rest ist wieder 1 zu 1 aus dem Skript. Die Values werden mittels Post übergeben und die Variablen werden dann mit einem Echo mehr oder weniger schön ausgegeben. (Evt wäre eine Tabelle gut gewesen für die Darstellung.)

```php
<?php

$background = "https://images5.alphacoders.com/356/thumbbig-356350.jpg";


$anrede = $_POST["anrede"];
$name = $_POST["name"];
$strasse = $_POST["strasse"];
$ort = $_POST["ort"];
$plz = $_POST["plz"];
$mail = $_POST["email"];
$nichtalkoholisch = $_POST["nichtalkoholisch"];
$schnaps = $_POST["schnaps"];
$bier = $_POST["bier"];
$bemerkung = $_POST["bemerkung"];



echo "<div>";
echo "Ihre Informationen wurden übermittelt.
<br>
<br>  <b>Name</b>
<br>$name
<br>
<br>  <b>Adresse</b>
<br>$strasse
<br>$plz
<br>$ort
<br>
<br>  <b>Mail</b>
<br>$mail
<br>
<br>  <b>Bemerkung</b>
<br>$bemerkung";
echo "</div>";
echo "<br>";
echo "<b>Interessen</b>" ;
echo "<br>";

if( $_POST["bier"])
{
    echo "bier" ;
}
echo "<br>";

if( $_POST["schnaps"])
{
    echo "Schnaps" ;
}
echo "<br>";

if( $_POST["nichtalkoholisch"])
{
    echo "nichtalkoholisch" ;
}

?>

<html>

<head>
    <style type="text/css">
        body {
            background-image: url('<?php echo $background; ?>');
            background-size: 1000px;
        }
    </style>

    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
</head>

<body>
</body>

</html>
```