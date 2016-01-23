#DBA

##Store engine

El store engine es una capa entre la Base de datos y el hardware.
El store engine define:
-Como se guardan los datos en disco.
-Como se borra la información de disco.
-Como se lee la información de disco.
-Las estructuras que se usan para almecenar los daots.

Existe dos storage engines actualmente:
- MMAP v1
- WiredTiger


The storage engine directly determines:
Format of indexes
The data file format
