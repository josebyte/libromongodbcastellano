#Mongo Shell

En la carpeta donde tenemos instalado MongoDB hay una carpeta "bin", en ella encontraremos todos los ejecutables de MongoDB. 
Los más usados son:
- mongod: es el demonio de base de datos, debemos ejecutarlo y dejarlo en ejecución para poder lanzar consultas y trabajar.
- mongo: es el shell desde el cual  lanzaremos las consultas.
- mongos: es un servicio de routing de MongoDB Shard.

Por lo que si no tienes ya iniciado mongod lo primero es iniciarlo con:
```
mongod
```

Ahora vamos a empezar a lanzar consultas contra nuestro mongod, para ello accedemos a nuestro shell escribiendo:
```
mongo
```

Por defecto intentaremos conectarnos al mongod de localhost en el puerto 27017. Si deseamos conectarnos a otro demonio de MongoDB debemos especificar el puerto y el host mediante: --port y --host.

Mongo shell es parte de MongoDB y proporciona un entorno completo de Javascript además de una interfaz para MongoDB.

Desde el shell estos son los comandos más básicos y utilizados, no hace falta que los probeis, de momento esta lista es para que os vayan sonando ya que los iremos utilizando a lo largo del libro:

Mostrar la base de datos actual:
```
db
```

Muestra la lista de bases de datos:
```
show dbs
```

Seleccionaremos la base de datos "midb":
```
use midb
```

Si realizamos una búsqueda en una colección de la base de datos elegida:
```
db.usuarios.find()
```

El shell de MongoDB devolverá un cursor con los primeros 20 resultados, si queremos mostrar más usaremos la palabra "it" para iterar el cursor.

Un cursor se cerrará pasados 10 minutos o cuando iteramos todos sus resultados. Podemos modificar el tiempo que permanecerá abierto el cursor. Podemos establecer el tiempo máximo del cursor con el siguiente comando:
```
var micursor = db.usuarios.find()
micursor.maxTimeMS(1200000)
```

El comando anterior ampliará el tiempo máximo de "micursor" a 20 mininutos (el parametro que recibe es milisegundos, 1200000==20min), aunque si es iterado completamente se cerrará antes de ese tiempo máximo.


Para imprimir un documento JSON de forma más "bonita" tenemos las siguientes opciones:
- .pretty() Al final de una consulta
- printjson() == print(tojson()) Para imprimir variables.

Si queremos almacenar un array en una variable:
```
var users = db.usuarios.find()
```
Para obtener el indice 4 o la posición 4 del cursor almacenado en la variable users creada en la linea anterior:
```
printjson( users [ 4 ] )
```
Mongo devolverá el usuario en esa posición:
```
{ "_id" : ObjectId("51a7dc7b2cacf40b79990bea"), "nombre" : "Joseba", "surname" : "Madrigal" }
```

Cuando accedes a un cursor por un índice, internamente mongo llama a "cursor.toArray()" para convertir el cursor en un array donde poder manejar índices y almacena TODOS los documentos que devuelve el cursor en la memoria RAM.
Para resultados muy grandes de documentos es posible que mongo devuelva: "out of available memory" ya que no cabe todo en la RAM.
