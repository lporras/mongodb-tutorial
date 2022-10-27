# Ingresar Información usando la consola de Mongo

## Seleccionar Base de Datos TEST

Dentro de la consola de mongo ejecutar:

```use test```

## Insertar un Documento

Copia y Pega este código:

```
db.restaurants.insertOne(
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
{
  acknowledged: true,
  insertedId: ObjectId("635ab15229cfc61642b5cf40")
}
```

Más información del método InsertOne se puede ver en este [link](https://www.mongodb.com/docs/mongodb-shell/crud/insert/)

Para ver más ejemplos de insert pueden revisar el tutorial de insert de este [link]
(https://www.mongodb.com/docs/manual/tutorial/insert-documents/)
**Nota:** Al leer la documentación hay un selector en la parte superior derecha que te permite elegir el lenguaje,
se debe elegir la opción MongoDB Shell

Siguente:
* [Encontrar documentos en la Base de Datos](/findOrQuery.md)
