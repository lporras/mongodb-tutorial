# mongodb-tutorial
Tutorial MongoDB para PROIN CHILE

## pasos

* Instalar MongoDB Seguir las instrucciones de: [link] (https://www.mongodb.com/download-center?jmp=nav#community)
* Asegurarse de correr mongod daemon
* Importar la base de datos de prueba que esta en dataset/primer-dataset.json
* ejecutar MongoImport:

```mongoimport --db test --collection restaurants --drop --file dataset/primer-dataset.json```

mongoimport se conecta a la instancia de mongod que está corriendo en localhost y en el puerto 27017
si tu base de datos está corriendo en un host y puerto diferente puedes utilizar las opciones:
--host y --port

## MongoShell

El MongoShell es una consola de Javascript interactiva para MongoDB y viene incluido con MongoDB.
Podemos usar mongo shell para consultar y actualizar información, como tambien realizar operaciones administrativas

## Ejecutar el cliente mongo

Escribe en la terminal: ```mongo```

En windows añade un .exe al final:  ```mongo.exe```

el cliente mongo por defecto se conecta a localhost y al puerto 27017, para ejecutarte a un host y puerto diferente y utilizar
diferentes opciones revisa: [link](https://docs.mongodb.com/manual/reference/program/mongo/)

### Help

Escribe en la consola de Mongo el comando help, este lista todos los comandos disponibles y sus respectivas descripciones:

```
MongoDB shell version: 3.2.0
connecting to: test
> help
	db.help()                    help on db methods
	db.mycoll.help()             help on collection methods
	sh.help()                    sharding helpers
	rs.help()                    replica set helpers
	help admin                   administrative help
	help connect                 connecting to a db help
	help keys                    key shortcuts
	help misc                    misc things to know
	help mr                      mapreduce

	show dbs                     show database names
	show collections             show collections in current database
	show users                   show users in current database
	show profile                 show most recent system.profile entries with time >= 1ms
	show logs                    show the accessible logger names
	show log [name]              prints out the last segment of log in memory, 'global' is default
	use <db_name>                set current database
	db.foo.find()                list objects in collection foo
	db.foo.find( { a : 1 } )     list objects in foo where a == 1
	it                           result of the last line evaluated; use to further iterate
	DBQuery.shellBatchSize = x   set default number of items to display on shell
	exit                         quit the mongo shell
```

* [Insertar documentos en la Base de Datos] (/InsertData.md)
