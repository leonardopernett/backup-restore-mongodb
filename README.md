

# Backup y Restauracion en Mongodb
#### Lo primero que tenemos que hacer es iniciar el servido de Mongodb a través del comando:
```
mongod
```
#### Para luego poder ejecutar el comando, que inicia un shell de Mongodb, con el comando:

```
mongo
```

#### Una vez inicializado el shell de Mongo, ya podemos crear los backups de todas las bases de datos que tenemos en Mongodb, a través del comando:
```
mongodump
```

#### El cual, por defecto crea una carpeta llamada dump, que contiene todas nuestras bases de datos separadas por carpetas.

#### Ahora vamos a hacer una prueba, en la misma sesión del shell de mongo; es decir en la misma consola que se ejecutó el comando mongo vamos a eliminar las bases de datos que tengamos hasta el momento, para poder restaurarlas a partir de los backups que hemos generado previamente.

#### Para eliminar bases de datos de Mongodb, primero tienes que seleccionarlas a través del comando: use  mibasededatos; en done es el nombre de mibasededatos es la base de datos que quieres eliminar. lo que te permitirá ejecutar el comando db.dropDatabase() que se encargará de eliminar la base de datos que seleccionaste.

#### Una vez la base de datos este eliminada, vamos a usar el backup para restaurarla, y para hacer eso, desde tu consola o terminal necesitas ubicarte en la ruta en donde este almacenado el backup, es decir en donde este la carpeta dump y ejecutar el comando mongorestore. este comando lo hará es leer la carpeta dump y restaurar todas las bases de datos que encuentre ella.

#### Pero mucha veces tan solo vas a necesitar hacer un backup de una sola base de datos, y para eso tan solo necesitas agregar una opción al comando mongodump. indicándole el nombre de la base de datos a la que quieres hacer una copia de seguridad:
```
mongodump --db mibasededatos
```
#### este comando de nuevo creara una carpeta llamada dump, pero esta vez tan solo con la base de datos que hemos seleccionado. 

#### Y para restaurar esta única base de datos, ejecutamos el comando mongorestore pero esta vez con la opción --db y la ruta de la carpeta en donde se encuentra la base de datos que queremos restaurar:
```
mongorestore --db mibasededatos dump/mibasededatos
```

#### Finalmente la otra opción, es que quieras restaurar tan solo una colección, de una base de datos. para esta tarea tan solo le agregamos la opción --collection al comando mongodump:
```
mongodump --db mibasededatos --collection micolección
```
#### Y para restaurar tan solo una colección, tan solo le agregamos la opción --collection al comando mongorestore, además de la ruta de en donde se encuentra tal colección:
```
mongorestore --db mibasededatos --collection micolección dump/mibasededatos/micolección
```
