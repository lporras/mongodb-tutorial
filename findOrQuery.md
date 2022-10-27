## Consultar Información en la consola de Mongo

Podemos usar el método find() para realizar una consulta y obtener información de una coleccion de MongoDB.
Todas las consultas o queires en MongoDB tienen alcance en una sola colección.

Las consultas pueden retornar todos los documentos en una colección o solo los que cumplan con una condición o filtro especifico.
Podemos especificar un filtro o condición en un documento y pasarlo como parametro al método find().

El método find() retorna los resultados de una consulta en un cursor, el cual es un objeto iterable que contiene los documentos.

Escogemos la base de datos Test

```
use test
```

## Consultar todos los documentos de una colección

```
db.restaurants.find()
```

les devolverá algo como esto:

```
> db.restaurants.find()
[
  {
    _id: ObjectId("635aaaa56562e5c56e82782b"),
    address: {
      building: '2206',
      coord: [ -74.1377286, 40.6119572 ],
      street: 'Victory Boulevard',
      zipcode: '10314'
    },
    borough: 'Staten Island',
    cuisine: 'Jewish/Kosher',
    grades: [
      {
        date: ISODate("2014-10-06T00:00:00.000Z"),
        grade: 'A',
        score: 9
      },
      {
        date: ISODate("2014-05-20T00:00:00.000Z"),
        grade: 'A',
        score: 12
      },
      {
        date: ISODate("2013-04-04T00:00:00.000Z"),
        grade: 'A',
        score: 12
      },
      {
        date: ISODate("2012-01-24T00:00:00.000Z"),
        grade: 'A',
        score: 9
      }
    ],
    name: 'Kosher Island',
    restaurant_id: '40356442'
  },
	...
]
Type "it" for more
```

Escribiendo "it" en la consola nos devuelve los sgtes resultados.
El cursor itera de a 20 registros.
Para más información acerca de cómo iterar con el cursor ver este [link](https://docs.mongodb.com/manual/tutorial/iterate-a-cursor/)

## Especificar condiciones de Igualdad

Para consultar por un valor exacto de un campo utilizamos el sgte formato:
```
{ <field1>: <value1>, <field2>: <value2>, ... }
```

Si el campo es un top-level field entonces no es necesario usar comillas,
ejemplo:

```
db.restaurants.find( { "borough": "Manhattan" } )
```

Pero si el campo está dentro de un sub documento es necesario usar las comillas y la notación de punto para indicar el sub campo

```
db.restaurants.find( { "address.zipcode": "10075" } )
```

## Buscar por un campo dentro de un Array

El campo grades contiene un array de documentos, los cuales tienen un campo "grade".
Si queremos buscar por ese campo debemos usar la notación de punto.
ejemplo:

```
> db.restaurants.find( { "grades.grade": "B" } ).limit(1)
[
  {
    _id: ObjectId("635aaaa56562e5c56e827830"),
    address: {
      building: '97-22',
      coord: [ -73.8601152, 40.7311739 ],
      street: '63 Road',
      zipcode: '11374'
    },
    borough: 'Queens',
    cuisine: 'Jewish/Kosher',
    grades: [
      {
        date: ISODate("2014-11-24T00:00:00.000Z"),
        grade: 'Z',
        score: 20
      },
      {
        date: ISODate("2013-01-17T00:00:00.000Z"),
        grade: 'A',
        score: 13
      },
      {
        date: ISODate("2012-08-02T00:00:00.000Z"),
        grade: 'A',
        score: 13
      },
      {
        date: ISODate("2011-12-15T00:00:00.000Z"),
        grade: 'B',
        score: 25
      }
    ],
    name: 'Tov Kosher Kitchen',
    restaurant_id: '40356068'
  }
]
```

## Especificar condiciones con Operadores

MongoDB viene con operadores para especificar condiciones en una consulta, como operadores de comparacion.
Aunque hay excepciones, como los operadores de condición $or y $and, los operadores de condicion cumplen el siguente formato:

```
{ <field1>: { <operator1>: <value1> } }
```

Para ver la lista completa de operadores, ver [link](https://docs.mongodb.com/manual/reference/operator/query-comparison/)

## Mayor que ($gt)

Para buscar los restaurantes cuyos precio de "grades" sea mayor a 30:

```
db.restaurants.find( { "grades.score": { $gt: 30 } } )
```

## Menor que ($lt)

Para buscar los restaurantes cuyos precio de "grades" sea menor a 30:
```
db.restaurants.find( { "grades.score": { $lt: 30 } } )
```

**Nota:** Para Mayor igual y menor igual se utilzan los operadores **$gte** y **$lte**

## Operador Lógico AND

Puedes especificar una conjunción para una lista de condiciones se separan con cóma en un documento de condicion:

```
db.restaurants.find( { "cuisine": "Italian", "address.zipcode": "10075" } )
```

## Operador Lógico OR

Puedes especificar una disjunción (OR) para una lista de condiciones utilizando el operador $or de la sgte forma:

```
db.restaurants.find(
   { $or: [ { "cuisine": "Italian" }, { "address.zipcode": "10075" } ] }
)
```

## Ordenar los resultados

Para obtener los resultados ordenados por un o más campos se utiliza el método sort anidado al final del fin(),
dentro del método sort se especifica un documento que sirve para determinar el o los campos con los cuales ordenar
y si se trata de ascendente o descendente.  1 es ascendente y -1 es descendente.

```
db.restaurants.find().sort( { "borough": 1 } )
```

Siguente:
* [Actualizar los documentos de la Base de Datos](/updateData.md)