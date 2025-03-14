# Erste Schritte

## Account anlegen

## Voraussetzung

* Python3, Pip3
* Venv
* PostgreSQL muss installiert sein
* git


## Erstes Projekt

### Git-Repo vorbereiten
falls git create keine git-struktur erzeugt hat

```
mkdir  heroku_tutorial
cd heroku_tutorial
python3 -m venv ./venv
source ./venv/bin/activate
```

```
git init
```

`.gitignore`mit dem Inhalt von https://gist.github.com/santoshpurbey/6f982faf1eacdac153ffd86a3a694239 befüllen (.gitignore für Django und Python)

```
git add .
git commit -m "first commit"
```

### xxx


bzw. das entsprechende Skript je nach Shell, z.B. `source ./venv/bin/activate.fish`bei Fish

```
heroku login
heroku create
```
prüfen, ob Remote-Git exisitert: `git remote -v`

```
heroku	https://git.heroku.com/secret-savannah-xxx.git (fetch)
heroku	https://git.heroku.com/secret-savannah-xxx.git (push)
```


könnte man auch mit Namen machen, wenn man keinen angibt, erhält man einen Zufallsnamen, z.B.
```
https://hidden-castle-36xxx.herokuapp.com/ | https://git.heroku.com/hidden-castle-36xxx.git
```



`requirements.txt`mit folgendem Inhalt anlegen
```
django
gunicorn
django-heroku
requests
```

`runtime.txt`mit folgendem Inhalt anlegen
```
python-3.7.9
```

`Procfile`mit folgendem Inhalt anlegen
```
web: gunicorn hello_heroku.wsgi --log-file -
```
Requirements mit pip installieren: `pip install -r requirements.txt`

### Projekt mit Djano einrichten

`django-admin startproject hello_heroku .`

ergibt manage.py und ein Verzeichnis hello_heroku mit diversen Dateien

```
python manage.py startapp hello
```
erzeugt Verzeichnis `hello ` mit diversen Dateien

hello_heroku/settings.py um import `django_heroku` und am Ende `django_heroku.settings(locals())`ergänzen

 hello/views.py um folgendes ergänzen
```

from django.http import HttpResponse


def index(request):
    return HttpResponse("Hello, world.")
```
hello_heroku/urls.py um folgendes ergänzen


```
from django.contrib import admin
from django.urls import path

import hello.views

urlpatterns = [
    path('admin/', admin.site.urls),
    path("", hello.views.index, name="index"),
]
```



Start mit gunicorn testen

```
gunicorn hello_heroku.wsgi --log-file -
```

`heroku config:set DISABLE_COLLECTSTATIC=1`(da wir kein static files haben)


```
git add .
git commit -m "first functional commit"
git push heroku master
```

### Templates Statische Seiten ausliefern

```
cd hello
mkdir templates
cd templates
touch index.html
```

index.html mit
```
<html>
<head>
<title>Template Demo</title>
</head>
<body>
<p>Yeeee haaa!</p>
</body>
</html>
```

hello/views.py anpassen
```
def index(request):
    #return HttpResponse("Hello, world.")
    return render(request, "index.html")
```

### Um spezielle Packages erweitern

Beispiel OpenCV

`Aptfile`mit folgendem Inhalt im Basisverzeichnis anlegen
```
libsm6
libxrender1
libfontconfig1
libice6
```
in `requirements.txt`ergänzen:

```
opencv-python-headless
```
mit pip installieren `pip install -r requirements.txt`

Buildpack einbinden
```
heroku config:add BUILDPACK_URL=https://github.com/ddollar/heroku-buildpack-multi.git
```

 hello/views.py um folgendes ergänzen
```
from django.shortcuts import render

# Create your views here.

from django.http import HttpResponse
import cv2

def index(request):
    return HttpResponse("Hello, world.")

def db(request):
    return HttpResponse(""2nd request with OpenCV "+cv2.__version__)
```

 hello_heroku/views.py um folgendes ergänzen
```
path("db/", hello.views.db, name="db"),
```