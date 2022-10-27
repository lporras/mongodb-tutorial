# mongodb-tutorial
Tutorial MongoDB

## pasos

* Instalar MongoDB Seguir las instrucciones de: [link] (https://www.mongodb.com/docs/manual/installation/)
	Para Windows usar este [link](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-windows/)
	Para Mac usar este [link](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-os-x/)
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

Escribe en la terminal: ```mongosh```

En windows añade un .exe al final:  ```mongo.exe```

el cliente mongo por defecto se conecta a localhost y al puerto 27017, para ejecutarte a un host y puerto diferente y utilizar
diferentes opciones revisa: [link](https://www.mongodb.com/docs/mongodb-shell/)

### Help

Escribe en la consola de Mongo el comando help, este lista todos los comandos disponibles y sus respectivas descripciones:

```
Current Mongosh Log ID:	635aab65667bca84c8eb8222
Connecting to:		mongodb://127.0.0.1:27017/?directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+1.6.0
Using MongoDB:		6.0.1
Using Mongosh:		1.6.0

For mongosh info see: https://docs.mongodb.com/mongodb-shell/
> help
  Shell Help:

    use                                        Set current database
    show                                       'show databases'/'show dbs': Print a list of all available databases.
                                               'show collections'/'show tables': Print a list of all collections for current database.
                                               'show profile': Prints system.profile information.
                                               'show users': Print a list of all users for current database.
                                               'show roles': Print a list of all roles for current database.
                                               'show log <type>': log for current connection, if type is not set uses 'global'
                                               'show logs': Print all logs.

    exit                                       Quit the MongoDB shell with exit/exit()/.exit
    quit                                       Quit the MongoDB shell with quit/quit()
    Mongo                                      Create a new connection and return the Mongo object. Usage: new Mongo(URI, options [optional])
    connect                                    Create a new connection and return the Database object. Usage: connect(URI, username [optional], password [optional])
    it                                         result of the last line evaluated; use to further iterate
    version                                    Shell version
    load                                       Loads and runs a JavaScript file into the current shell environment
    enableTelemetry                            Enables collection of anonymous usage data to improve the mongosh CLI
    disableTelemetry                           Disables collection of anonymous usage data to improve the mongosh CLI
    passwordPrompt                             Prompts the user for a password
    sleep                                      Sleep for the specified number of milliseconds
    print                                      Prints the contents of an object to the output
    printjson                                  Alias for print()
    cls                                        Clears the screen like console.clear()
    isInteractive                              Returns whether the shell will enter or has entered interactive mode
```

* [Insertar documentos en la Base de Datos] (/InsertData.md)
* [Encontrar documentos en la Base de Datos](/findOrQuery.md)
* [Actualizar los documentos de la Base de Datos](/updateData.md)
* [Eliminar los documentos de la Base de Datos](/removeData.md)
* [Aggregate tutorial] (https://www.mongodb.com/docs/manual/aggregation/)
* [Drivers](https://www.mongodb.com/docs/drivers/drivers/)
