# Model View Controller (MVC)

Dies erreichen wir unter anderem mit einer einheitlichen URL.

`http://http://hostname:8000/home/index/param1/param2`

Home steht für den Controller und Index ist die Methode.

Bedingungen:

- Saubere Ablagestruktur
- Controller gemäss URL
- Methode gemäss URL
- URL muss richtige Infos herausholen
- Rendering der View wird vom richtigen Model über den Controller ausgelöst
  
## Sequenzdiagramm

Sequenzdiagramm eines Websitenaufrufes.

```plantuml
@startuml

actor User 

activate .htaccess

User -> .htaccess: http://localhost:8000/public/home/index/Name

.htaccess -> .htaccess : Rewrite public/$1

deactivate .htaccess

.htaccess -> "public/index.php" : index.php?url=$1

activate "public/index.php"

"public/index.php" -> "app/init.php" : require once

activate "app/init.php"

"public/index.php" -> "app/core/App.php" : new App()

deactivate "public/index.php"
deactivate "app/init.php"

"app/core/App.php" -> "app/core/App.php" : __construct()

activate "app/controllers/controller.php"

"app/core/App.php" -> "app/controllers/controller.php" : new Controller

"app/core/App.php" -> "app/controllers/controller.php" : Methode ausführen (call_user_func_array([$this->controller, $this->method], $this->params);)

"app/controllers/controller.php" -> "app/views/view.php" : include_once

deactivate "app/controllers/controller.php"

"app/views/view.php" -> User
@enduml
```

## Klassendiagramm

Klassendiagramm des Frameworkes:

```plantuml
@startuml

class contact extends Controller 
{
    + index()
    + test($param1, $param2)
}

class home extends Controller 
{
    + index($name)
}

class App 
{
    # $controller
    # $methode
    # $params

    + __construct()
    # parseUrl()
}

class Controller 
{
    # model($model)
    # view($view, $data)
}

class User 
{
    + $name
}

class index
{

}

@enduml
```
