# Ingresar Información usando la consola de Mongo

## Seleccionar Base de Datos TEST

Dentro de la consola de mongo ejecutar:

```use test```

## Insertar un Documento

Copia y Pega este código:

```
db.restaurants.insert(
   {
      "address" : {
         "street" : "2 Avenue",
         "zipcode" : "10075",
         "building" : "1480",
         "coord" : [ -73.9557413, 40.7720266 ]
      },
      "borough" : "Manhattan",
      "cuisine" : "Italian",
      "grades" : [
         {
            "date" : ISODate("2014-10-01T00:00:00Z"),
            "grade" : "A",
            "score" : 11
         },
         {
            "date" : ISODate("2014-01-16T00:00:00Z"),
            "grade" : "B",
            "score" : 17
         }
      ],
      "name" : "Vella",
      "restaurant_id" : "41704620"
   }
)
```

Este método retorna objecto de resultado de escritura que indica el estado de la operación:

```
WriteResult({ "nInserted" : 1 })
```

Más información del método Insert se puede ver en este [link](https://docs.mongodb.com/manual/reference/method/db.collection.insert/#db.collection.insert)

Para ver más ejemplos de insert pueden revisar el tutorial de insert de este [link]
(https://docs.mongodb.com/manual/tutorial/insert-documents/)

