# Docker 

Docker wird für unsere Übungsumgebung in PHP genutzt. Ebenfalls benutzen wir Docsify, welches ein Docker-Compose Projekt ist.


## Verwendung von Docker

Docker hat gegenüber VM's viele Vorteile. Die Beschreibung von einem Container(Konfiguration etc.) wird bei Docker in Text Dateien geschrieben und können so einfach verwaltet werden.

Die Images welche erzeugt werden, sind meist nur einige hundert MB gross und können so leicht heruntergeladen werden.

Für uns eignet sich Docker speziell, damit die Struktur und die Fehlersuche recht einfach geschehen kann, da man über Github das Projekt teilen kann und so 1 zu 1 die selbe Infrastruktur erzeugt werden kann.


## Funktionsweise

Erst wird ein ```Dockerfile``` geschrieben. Dieses Dockerfile ist die Anleitung wie ein ```Docker-Image``` gebaut wird.
Mit diesen Images wird dann der Container laufen gelassen.

Es gibt auf ```Docker hub``` tausende vorgefertigte Images mit kompletten Infrastrukturen, welche den eigenen Bedürfnissen angepasst werden können.


## Wichtige Befehle in Docker

| Befehl            | Beschreibung                   | Options  |
| ----------------- |:------------------------------:| -----:|
|```docker version```       | Gibt die Docker Version aus      |    - |
|``` docker images ```      | Alle vorhandenen Images anzeigen | - |
|``` docker ps```           | Alle laufenden Container anzeigen     |   -a |
|``` docker build ```       |Image wird auf ein Dockerfile erstellt| -t . |
|``` docker run ```         |Image wird ausgeführt| -i |
|``` docker stop name```  |Container wird angehalten| -|
|``` docker-compose up```   |Docker Container mit einem docker-compose File erstellen(starten)| -|


## Container Virtualisierung

Mit Container-Virtualisierung erreicht man, dass mehrere eigenständige Services auf dem selben Hostsystem laufen. Der Vorteil von Containern gegenüber Virtuellen Maschinen ist, dass die Hardware besser ausgelastet wird und man besser Backups erstellen kann, da die Dienste getrennt voneinander laufen gelassen werden.

Docker nutzt die System-Level-Virtualisierung unter Linux.

Weiter kann man mit Docker Compose innerhalb von einer Datei mehrere Container erstellen und gleich ihre Beziehungen definieren. (docker-compose.yml) Alle Container können danach mit einem einzigen Befehl gestartet werden. (docker-compose up)


## Hello world


Befehl:
```
docker run hello-world
``` 

Ausgabe:
```
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
b8dfde127a29: Pull complete 
Digest: sha256:7d91b69e04a9029b99f3585aaaccae2baa80bcf318f4a5d2165a9898cd2dc0a1
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.
```

Mit ```docker run``` wollen wir das Image ```hello-world``` laufen lassen. Docker überprüft, ob das Image lokal zu finden ist, was dann aber auf der erstel Linie scheitert.
Also pullt er es vom Repository. Sobald der Download abgeschlossen ist, sehen wir das wir die "latest" Version vom Image hello-world haben. Zum Schluss wird das Hello World ausgeführt.
(Man sieht jetzt, dass das Image vom Hello-world mit dem Befehl ```Docker Images``` und beim nächsten mal wenn man diesen Befehl ausführt, wird es direkt auf diesem ausgeführt.)