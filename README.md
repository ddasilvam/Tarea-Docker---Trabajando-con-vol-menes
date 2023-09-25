# Tarea: Docker - Trabajando con volúmenes
## 1. Descarga la imagen 'httpd' y comprueba que está en tu equipo
Comenzamos descargando la imagen httpd utilizando el comando `docker pull httpd`. Al no especificar una versión del paquete, se utilizará por defecto la etiqueta `latest`, por lo que se descargará la última versión.
```console
    asir2@A09equipo14:~/Documentos/SRI/Tarea2$ docker pull httpd
    Using default tag: latest
    latest: Pulling from library/httpd
    Digest: sha256:5123fb6e039b83a4319b668b4fe1ee04c4fbd7c4c8d1d6ef843e8a943a9aed3f
    Status: Image is up to date for httpd:latest
    docker.io/library/httpd:latest
```
Comprobamos que se ha descargado mediante el comando `docker images`.
```console
    asir2@A09equipo14:~/Documentos/SRI/Tarea2$ docker images
    REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
    httpd         latest    359570977af2   5 days ago     168MB
    httpd         2.4       7860e7628717   2 weeks ago    168MB
```
## 2. Crea un contenedor con el nombre 'asir_httpd'
## 3. Mapea el puerto 80 del contenedor con el puerto 8000 de tu máquina
## 4. Utiliza bind mount para que el directorio del apache2 'htdocs' esté montado un directorio que tú elijas
Para crear el contenedor ejecutamos el comando `docker run -dit --name asir_httpd -p 8000:80 -v "$PWD"/htdocs:/usr/local/apache2/htdocs/ httpd:latest`
* `run` especifica que queremos arrancar un contenedor
* `-dit` para que se arranque en segundo plano, manteniendo STDIN abierto y que le adjudique una pseudo-TTY
* `--name` para darle el nombre deseado, en este caso `asir_httpd`
* `-p 8000:80` mapea el puerto 80 del contenedor con el 8000 del host
* `-v "$PWD"/htdocs:/usr/local/apache2/htdocs/` monta la carpeta /usr/local/apache2/htdocs/ del contenedor en la carpeta htdocs dentro del directorio actual
* `httpd:latest` para espeficiar la imagen que queremos utilizar
Comprobamos que se ha creado y se está ejecutando mediante el comando `docker ps`
```console
    asir2@A09equipo14:~/Documentos/SRI/Tarea2$ docker ps
    CONTAINER ID   IMAGE          COMMAND              CREATED          STATUS          PORTS                                   NAMES
    dd5e04b72af2   httpd:latest   "httpd-foreground"   56 seconds ago   Up 55 seconds   0.0.0.0:8000->80/tcp, :::8000->80/tcp   asir_httpd
```
## Commit V1

