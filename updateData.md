# Actualizar Información en MongoDB

Para actualizar la información de un documento de una colección se utiliza el método updateOne() y
para actualizar varios documentos se utiliza el método updateMany()
éste método acepta como parametros:

* Un documento de filtro para encontrar el/los documento(s) a actualizar.
* Un documento de actualización para especificar la modificación a realizar y
* unas opciones como parámetros (opcional).

## Actualizar Campos Top-Level

La siguiente operación actualiza solo el primer documento que encuentre con "name" == "Juni" y modifica el campo "cuisine" con "American (New)"
y actualiza el campo "lastModified" utilizando el operador [$currentDate](https://www.mongodb.com/docs/manual/reference/operator/update/currentDate/#up._S_currentDate)
```
db.restaurants.updateOne(
    { "name" : "Juni" },
    {
      $set: { "cuisine": "American (New)" },
      $currentDate: { "lastModified": true }
    }
)
```

## Actualizar un SubDocumento

Se utiliza la notación de punto para actualizar el campo "street" del sub documento "address", del restaurante con "restaurant_id" == "41156888":
```
db.restaurants.updateOne(
  { "restaurant_id" : "41156888" },
  { $set: { "address.street": "East 31st Street" } }
)
```

## Actualizar multiples documentos

Para actualizar más de 1 documento se debe utilzar el método updateMany().

```
db.restaurants.updateMany(
  { "address.zipcode": "10016", cuisine: "Other" },
  {
    $set: { cuisine: "Category To Be Determined" },
    $currentDate: { "lastModified": true }
  }
)
```

## Reemplazar un documento completo

Para reemplazar un documento completo se utiliza el método replaceOne(), el cual no tiene operador $set
recibe un documento de condición y un segundo documento con la info a reemplazar

```
db.restaurants.replaceOne(
   { "restaurant_id" : "41704620" },
   {
     "name" : "Vella 2",
     "address" : {
              "coord" : [ -73.9557413, 40.7720266 ],
              "building" : "1480",
              "street" : "2 Avenue",
              "zipcode" : "10075"
     }
   }
)
```

Si buscamos los documentos con `{ "restaurant_id" : "41704620" }` no vamos a encontrar el documento que
acabamos de actualizar, pero si lo buscamos con `{name: "Vella 2"}` lo vamos a encontrar:

```
test> db.restaurants.find({name: "Vella 2"})
[
  {
    _id: ObjectId("635aaaa66562e5c56e82bd17"),
    name: 'Vella 2',
    address: {
      coord: [ -73.9557413, 40.7720266 ],
      building: '1480',
      street: '2 Avenue',
      zipcode: '10075'
    }
  }
]
```

**Nota:** Esto es peligroso, el documento ahora solo contendrá los campos especificados.

Siguente:
* [Eliminar los documentos de la Base de Datos](/removeData.md)