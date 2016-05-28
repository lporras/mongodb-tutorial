# Actualizar Información en MongoDB

Para actualizar la información de uno o más documentos de una colección se utiliza el método update()
éste método acepta como parametros:

* Un documento de filtro para encontrar los documentos a actualizar.
* Un documento de actualización para especificar la modificación a realizar y
* unas opciones como parámetros (opcional).

## Actualizar Campos Top-Level 

La siguiente operación actualiza solo el primer documento que encuentr con "name" == "Juni" y modifica el campo "cuisine" con "American (New)"
y actualiza el campo "lastModified" utilizando el operador [$currentDate](https://docs.mongodb.com/manual/reference/operator/update/currentDate/#up._S_currentDate)
```
db.restaurants.update(
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
db.restaurants.update(
  { "restaurant_id" : "41156888" },
  { $set: { "address.street": "East 31st Street" } }
)
```

## Actualizar multiples documentos

Para actualizar más de 1 documento se debe especificar un 3er documento que indica la opción "multi".

```db.restaurants.update(
  { "address.zipcode": "10016", cuisine: "Other" },
  {
    $set: { cuisine: "Category To Be Determined" },
    $currentDate: { "lastModified": true }
  },
  { multi: true}
)
```

## Reemplazar un documento completo

Para reemplazar un documento completo se utiliza el update() sin el operador $set

```
db.restaurants.update(
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

**Nota:** Esto es peligroso, el documento ahora solo contendrá los campos especificados.
