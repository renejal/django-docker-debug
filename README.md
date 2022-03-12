# proyect debug config with docker and django and vscode

 #### config the project for debugin

    1. Crete realme
    2. .gitingore
    3. create folder /app

 #### Dowload images django, execute command in console
    docker run -v ${PWD}/app:/app -w /app python:3.9-alpine sh -c "pip install Django==3.2 && django-admin startproject app ."

#### add file docker automatic
    - ctrl + p  "vscode"
    - add docker
    - select folder app
    - select python-django
    - yes  o si
#### for linx o Mac recomendation change format file CRLF BY LF
    - la configuracio se encuentr en la parte inferior derecha del archivo

#### config requirements versiosn
    "add version for is update in parchers"
    django>=4.0,<4.1
    gunicorn>=20.1.0,<20.2.0

#### config version contenedor 
    FROM python:3.9.10-alpine3.14 

#### config path folder la barra inclinada lo que hace es copiar la informacion que hay dentro de nuetra aplicacion dentro de nuestro proyecto a la ubicaion que se defina
    "COPY . /app" change for 
    COPY ./app /app  

#### update path app.wsgi if not update automatic
    CMD ["gunicorn", "--bind", "0.0.0.0:8000", "app.wsgi"]
#### updte path in app\manage.py by manage.py
    command: ["sh", "-c", "pip install debugpy -t /tmp && python /tmp/debugpy --wait-for-client --listen 0.0.0.0:5678 app\manage.py runserver 0.0.0.0:8000 --nothreading --noreload"]
    "change"
    command: ["sh", "-c", "pip install debugpy -t /tmp && python /tmp/debugpy --wait-for-client --listen 0.0.0.0:5678 manage.py runserver 0.0.0.0:8000 --nothreading --noreload"]

#### if error with docker scan 
1. go documentation recomend install docker-desktop version > 4.3.1
    docker scan --accept-license --version "run comnd for validate verson of docker"

#### update file lauch.json
    - go .vscode/lauch.json and update line "localRoot": "${workspaceFolder}"
    - ${workspaceFolder/app}
#### update file tasks.json
    -go .vscode/tasks.sjon and update "file":"app/manage.py" for "file":"manage.py"
    
