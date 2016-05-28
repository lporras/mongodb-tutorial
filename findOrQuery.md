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
{ "_id" : ObjectId("5748c9adc5dd88b97c4a9c69"), "address" : { "building" : "351", "coord" : [ -73.98513559999999, 40.7676919 ], "street" : "West   57 Street", "zipcode" : "10019" }, "borough" : "Manhattan", "cuisine" : "Irish", "grades" : [ { "date" : ISODate("2014-09-06T00:00:00Z"), "grade" : "A", "score" : 2 }, { "date" : ISODate("2013-07-22T00:00:00Z"), "grade" : "A", "score" : 11 }, { "date" : ISODate("2012-07-31T00:00:00Z"), "grade" : "A", "score" : 12 }, { "date" : ISODate("2011-12-29T00:00:00Z"), "grade" : "A", "score" : 12 } ], "name" : "Dj Reynolds Pub And Restaurant", "restaurant_id" : "30191841" }
{ "_id" : ObjectId("5748c9adc5dd88b97c4a9c6a"), "address" : { "building" : "2780", "coord" : [ -73.98241999999999, 40.579505 ], "street" : "Stillwell Avenue", "zipcode" : "11224" }, "borough" : "Brooklyn", "cuisine" : "American ", "grades" : [ { "date" : ISODate("2014-06-10T00:00:00Z"), "grade" : "A", "score" : 5 }, { "date" : ISODate("2013-06-05T00:00:00Z"), "grade" : "A", "score" : 7 }, { "date" : ISODate("2012-04-13T00:00:00Z"), "grade" : "A", "score" : 12 }, { "date" : ISODate("2011-10-12T00:00:00Z"), "grade" : "A", "score" : 12 } ], "name" : "Riviera Caterer", "restaurant_id" : "40356018" }
...
Type "it" for more
```

Escribiendo "it" en la consola nos devuelve los sgtes resultados.
El cursor itera de a 20 registros.
Para más información acerca de cómo iterar con el cursor ver este [link](https://docs.mongodb.com/manual/tutorial/iterate-a-cursor/)

**Nota:** Para imprimir los resultados en una forma legíble pueden agregar al final del find el método pretty, ej:
```
> db.restaurants.find().pretty()
{
	"_id" : ObjectId("5748c9adc5dd88b97c4a9c69"),
	"address" : {
		"building" : "351",
		"coord" : [
			-73.98513559999999,
			40.7676919
		],
		"street" : "West   57 Street",
		"zipcode" : "10019"
	},
	"borough" : "Manhattan",
	"cuisine" : "Irish",
	"grades" : [
		{
			"date" : ISODate("2014-09-06T00:00:00Z"),
			"grade" : "A",
			"score" : 2
		},
		{
			"date" : ISODate("2013-07-22T00:00:00Z"),
			"grade" : "A",
			"score" : 11
		},
		{
			"date" : ISODate("2012-07-31T00:00:00Z"),
			"grade" : "A",
			"score" : 12
		},
		{
			"date" : ISODate("2011-12-29T00:00:00Z"),
			"grade" : "A",
			"score" : 12
		}
	],
	"name" : "Dj Reynolds Pub And Restaurant",
	"restaurant_id" : "30191841"
}
```

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
> db.restaurants.find( { "grades.grade": "B" } ).limit(1).pretty()
{
	"_id" : ObjectId("5748c9adc5dd88b97c4a9c6b"),
	"address" : {
		"building" : "1007",
		"coord" : [
			-73.856077,
			40.848447
		],
		"street" : "Morris Park Ave",
		"zipcode" : "10462"
	},
	"borough" : "Bronx",
	"cuisine" : "Bakery",
	"grades" : [
		{
			"date" : ISODate("2014-03-03T00:00:00Z"),
			"grade" : "A",
			"score" : 2
		},
		{
			"date" : ISODate("2013-09-11T00:00:00Z"),
			"grade" : "A",
			"score" : 6
		},
		{
			"date" : ISODate("2013-01-24T00:00:00Z"),
			"grade" : "A",
			"score" : 10
		},
		{
			"date" : ISODate("2011-11-23T00:00:00Z"),
			"grade" : "A",
			"score" : 9
		},
		{
			"date" : ISODate("2011-03-10T00:00:00Z"),
			"grade" : "B",
			"score" : 14
		}
	],
	"name" : "Morris Park Bake Shop",
	"restaurant_id" : "30075445"
}
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
