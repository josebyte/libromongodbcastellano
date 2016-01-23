#Instalación

MongoDB está disponible para:
- Windows
- Mac
- Linux

En la documentación oficial de MongoDB se indica como instalar MongoDB en cada sistema operativo, a modo de resumen es de la siguiente forma:

##Instalación en Windows

Debemos descargarnos la versión correcta (64 o 32 bits) de la [web oficial](http://www.mongodb.org/downloads) de MongoDB.

La extensión del archivo descargado es ".msi" y haciendo doble click comenzará la instalación.

Para configurar el entorno es necesario definir el directorio donde guardará MongoDB los datos. Por defecto es "c:\data\db"`

```
md \data\db
```

Es posible especificar otra ruta mediante el siguiente comando:

```
C:\mongodb\bin\mongod.exe --dbpath "d:\test\mongodb\data"
```

Ahora debemos definir las variables de entorno en el sistema operativo:

1. Panel de control
2. Sistema
3. Configuración avanzada
4. Variables de entorno
5. Bajo "Variables de sistema" busca "Path" y haz doble click en el.
6. En el valor "Variable" de esa fila seleccionada debemos añadir al final ; si no existe y añadir la ruta de instalacion de MongoDb:
Por ejemplo yo he añadido al final:

```
;C:\mongodb\bin
```

##Instalación en MAC

Existen dos formas de instalar en OSX MongoDB:
- Instalar en OSX con Homebrew
- Instalar en OSX manualmente

###Instalar en OSX con Homebrew

```
brew update
brew install mongodb
```

###Instalar en OSX manualmente

Debemos descargarnos los binarios desde [web oficial](http://www.mongodb.org/downloads) .

Descomprimimos el paquete descargado:
```
tar -zxvf mongodb-osx-x86_64-3.0.2.tgz
```
Copiamos la carpeta descomprimida a la localización desde la que lanzaremos MongoDB:
```
mkdir -p mongodb
cp -R -n mongodb-osx-x86_64-3.0.2/ mongodb
```
Los archivos binarios de MongoDB se encuentran en el directorio bin/
Para agregar los binarios al PATH:
```
export PATH=<mongodb-install-directory>/bin:$PATH
```
Reemplazar <mongodb-install-directory> con la ruta de nuestra carpeta de Mongodb recientemente descomprimida y copiada.


##Instalación en Linux

Debemos descargarnos los binarios desde [web oficial](http://www.mongodb.org/downloads) .

Descomprimimos el paquete descargado:
```
tar -zxvf mongodb-linux-x86_64-3.0.2.tgz
```

Copiamos la carpeta descomprimida a la localización desde la que lanzaremos MongoDB:
```
mkdir -p mongodb
cp -R -n mongodb-linux-x86_64-3.0.2/ mongodb
```

Los archivos binarios de MongoDB se encuentran en el directorio bin/
Para agregar los binarios al PATH:
```
export PATH=<mongodb-install-directory>/bin:$PATH
```

Reemplazar <mongodb-install-directory> con la ruta de nuestra carpeta de Mongodb recientemente descomprimida y copiada.

Antes de iniciar mongod creamos la carpeta donde se encontrarán las bases de datos:
```
mkdir -p /data/db
```
