![title](imagenes/logobash.png?style=centerme)

# Ejercicio 1 (entregable)
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
**Resultado:**

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













