# mongodb-tutorial
Tutorial MongoDB para PROIN CHILE

## pasos

* Instalar MongoDB Seguir las instrucciones de: https://www.mongodb.com/download-center?jmp=nav#community
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
