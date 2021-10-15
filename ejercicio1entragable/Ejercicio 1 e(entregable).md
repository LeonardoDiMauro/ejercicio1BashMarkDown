![title](imagenes/logobash.png?style=centerme)

# Ejercicio 1 e(entregable)
Crea una carpeta para este ejercicio llamada ejercicio1 y dentro crear un archivo bash (ejecutable) llamado crearWeb.sh, este debe crear una nueva carpeta cuyo nombre se pasará como parámetro al ejecutar ese archivo. Si no se pasa un parámetro, el programa debe indicar error. Dentro de esa nueva carpeta se tiene que descargar automaticamente el siguiente repositorio github:

- https://github.com/dhg/Skeleton/releases/download/2.0.4/Skeleton-2.0.4.zip

Una vez descargado, se debe descomprimir y mostramos su contenido automáticamente.

### Pasos:

Abrir terminal en linux.

Crear carpeta **ejercicio1** con el comando:
```sh
mkdir ejercicio1
```

Entramos en la carpeta con el comando:
```sh
cd ejercicio1
```

Creamos un nuevo archivo de texto con extensión **.sh** con gedit con el comando:
```sh
gedit crearWeb.sh
```
Copiamos el siguiente código y guardamos con Cntr+S:
```
#!/bin/bash
if [ "$1" ]
then
   mkdir $1
   echo "Carpeta $1 creada correctamente."
   cd $1
   echo "Accediendo a carpeta $1"
   wget https://github.com/dhg/Skeleton/releases/download/2.0.4/Skeleton-2.0.4.zip
   echo "Archivos descargados:"
   unzip Skeleton-2.0.4
   echo "Archivos zip descomprimidos:"
   ls -al
 
else
   echo "Error -> No se indica nombre de la carpeta."
fi
```
Antes de ejecutar el archivo **crearWeb.sh** sera necesario darle permisos de ejecución, podemos hacerlo con el comando:
```
chmod +x crearWeb.sh
```
Ahora ya podemos ejecutar, pasando como parámetro **web1**, con el comando:
```
./crearWeb.sh web1
```
Deberá aparecer algo similar a esto por la terminal:
```
user88@server88:~/Escritorio/ejercicio1$ ./crearWeb.sh web1
Carpeta web1 creada correctamente.
Accediendo a carpeta web1
--2021-10-13 16:38:54--  https://github.com/dhg/Skeleton/releases/download/2.0.4/Skeleton-2.0.4.zip
Resolviendo github.com (github.com)... 140.82.121.4
Conectando con github.com (github.com)[140.82.121.4]:443... conectado.
Petición HTTP enviada, esperando respuesta... 302 Found
Ubicación: https://github-releases.githubusercontent.com/1685764/c41b0730-8f46-11e4-8916-ef3f41ca9e8c?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20211013%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20211013T143716Z&X-Amz-Expires=300&X-Amz-Signature=42bb4f1aec42e090f00895b8297ad50bf1826454e636427b7969eef9fe12bb95&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=1685764&response-content-disposition=attachment%3B%20filename%3DSkeleton-2.0.4.zip&response-content-type=application%2Foctet-stream [siguiente]
--2021-10-13 16:38:54--  https://github-releases.githubusercontent.com/1685764/c41b0730-8f46-11e4-8916-ef3f41ca9e8c?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20211013%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20211013T143716Z&X-Amz-Expires=300&X-Amz-Signature=42bb4f1aec42e090f00895b8297ad50bf1826454e636427b7969eef9fe12bb95&X-Amz-SignedHeaders=host&actor_id=0&key_id=0&repo_id=1685764&response-content-disposition=attachment%3B%20filename%3DSkeleton-2.0.4.zip&response-content-type=application%2Foctet-stream
Resolviendo github-releases.githubusercontent.com (github-releases.githubusercontent.com)... 185.199.109.154, 185.199.110.154, 185.199.111.154, ...
Conectando con github-releases.githubusercontent.com (github-releases.githubusercontent.com)[185.199.109.154]:443... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 8308 (8,1K) [application/octet-stream]
Guardando como: “Skeleton-2.0.4.zip”

Skeleton-2.0.4.zip                                          100%[=========================================================================================================================================>]   8,11K  --.-KB/s    en 0s      

2021-10-13 16:38:54 (18,2 MB/s) - “Skeleton-2.0.4.zip” guardado [8308/8308]

Archivos descargados:
Archive:  Skeleton-2.0.4.zip
   creating: Skeleton-2.0.4/
   creating: Skeleton-2.0.4/css/
  inflating: Skeleton-2.0.4/css/normalize.css  
  inflating: Skeleton-2.0.4/css/skeleton.css  
   creating: Skeleton-2.0.4/images/
 extracting: Skeleton-2.0.4/images/favicon.png  
  inflating: Skeleton-2.0.4/index.html  
Archivos zip descomprimidos:
total 24
drwxrwxr-x 3 leo leo 4096 oct 13 16:38 .
drwx------ 3 leo leo 4096 oct 13 16:38 ..
drwxr-xr-x 4 leo leo 4096 dic 29  2014 Skeleton-2.0.4
-rw-rw-r-- 1 leo leo 8308 may 21  2017 Skeleton-2.0.4.zip
```
Resultado:

![title](imagenes/img1.jpg)

![title](imagenes/img2.jpg)

![title](imagenes/img3.jpg)


### Explicación del codigo:
```
#!/bin/bash
```
Siempre que creemos un archivo con extensión **.sh** debemos incluir esta línea tal cual.
```
if [ "$1" ]
then
   mkdir $1
   echo "Carpeta $1 creada correctamente."
   cd $1
   echo "Accediendo a carpeta $1"
   wget https://github.com/dhg/Skeleton/releases/download/2.0.4/Skeleton-2.0.4.zip
   echo "Archivos descargados:"
   unzip Skeleton-2.0.4
   echo "Archivos zip descomprimidos:"
   ls -al
```
Después nos encontramos una **condición**, si el parámetro introducido al ejecutar **crearWeb.sh** existe, es decir, es igual a **true**, el programa continúa y se crea una nueva carpeta cuyo nombre será el parámetro indicado.

Luego, accederemos a esa nueva carpeta con el comando:
```
cd $1
```
una vez dentro, descargamos el repositorio de github que se indica al principio con el comando:
```
wget https://github.com/dhg/Skeleton/releases/download/2.0.4/Skeleton-2.0.4.zip
```

**Nota:** el comando wget está considerado como un descargador (downloader) muy potente. **Soporta http, https y ftp**.

Una vez descargado el archivo, este estará en formato **.zip**, lo podemos descomprimir con el comando:
```
unzip Skeleton-2.0.4
```
Después mostraremos por pantalla la información que contiene la carpeta con el comando:
```
ls -al
````
El comando **ls -al** muestra los archivos y carpetas que contiene la carpeta donde nos encontramos e información de esos archivos, tales como fecha de creación, permisos y número del proceso.
```
else
   echo "Error -> No se indica nombre de la carpeta."
```
Finalmente tenemos un **else**, para mostrar por pantalla un mensaje de error, en caso de que no se haya introducido un parametro al ejecutar **crearWeb.sh**.











# Dillinger
## _The Last Markdown Editor, Ever_

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Dillinger is a cloud-enabled, mobile-ready, offline-storage compatible,
AngularJS-powered HTML5 Markdown editor.

- Type some Markdown on the left
- See HTML in the right
- ✨Magic ✨

## Features

- Import a HTML file and watch it magically convert to Markdown
- Drag and drop images (requires your Dropbox account be linked)
- Import and save files from GitHub, Dropbox, Google Drive and One Drive
- Drag and drop markdown and HTML files into Dillinger
- Export documents as Markdown, HTML and PDF

Markdown is a lightweight markup language based on the formatting conventions
that people naturally use in email.
As [John Gruber] writes on the [Markdown site][df1]

> The overriding design goal for Markdown's
> formatting syntax is to make it as readable
> as possible. The idea is that a
> Markdown-formatted document should be
> publishable as-is, as plain text, without
> looking like it's been marked up with tags
> or formatting instructions.

This text you see here is *actually- written in Markdown! To get a feel
for Markdown's syntax, type some text into the left window and
watch the results in the right.

## Tech

Dillinger uses a number of open source projects to work properly:

- [AngularJS] - HTML enhanced for web apps!
- [Ace Editor] - awesome web-based text editor
- [markdown-it] - Markdown parser done right. Fast and easy to extend.
- [Twitter Bootstrap] - great UI boilerplate for modern web apps
- [node.js] - evented I/O for the backend
- [Express] - fast node.js network app framework [@tjholowaychuk]
- [Gulp] - the streaming build system
- [Breakdance](https://breakdance.github.io/breakdance/) - HTML
to Markdown converter
- [jQuery] - duh

And of course Dillinger itself is open source with a [public repository][dill]
 on GitHub.

## Installation

Dillinger requires [Node.js](https://nodejs.org/) v10+ to run.

Install the dependencies and devDependencies and start the server.

```sh
cd dillinger
npm i
node app
```

For production environments...

```sh
npm install --production
NODE_ENV=production node app
```

## Plugins

Dillinger is currently extended with the following plugins.
Instructions on how to use them in your own application are linked below.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Development

Want to contribute? Great!

Dillinger uses Gulp + Webpack for fast developing.
Make a change in your file and instantaneously see your updates!

Open your favorite Terminal and run these commands.

First Tab:

```sh
node app
```

Second Tab:

```sh
gulp watch
```

(optional) Third:

```sh
karma test
```

#### Building for source

For production release:

```sh
gulp build --prod
```

Generating pre-built zip archives for distribution:

```sh
gulp build dist --prod
```

## Docker

Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 8080, so change this within the
Dockerfile if necessary. When ready, simply use the Dockerfile to
build the image.

```sh
cd dillinger
docker build -t <youruser>/dillinger:${package.json.version} .
```

This will create the dillinger image and pull in the necessary dependencies.
Be sure to swap out `${package.json.version}` with the actual
version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on
your host. In this example, we simply map port 8000 of the host to
port 8080 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart=always --cap-add=SYS_ADMIN --name=dillinger <youruser>/dillinger:${package.json.version}
```

> Note: `--capt-add=SYS-ADMIN` is required for PDF rendering.

Verify the deployment by navigating to your server address in
your preferred browser.

```sh
127.0.0.1:8000
```

## License

MIT

**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>


