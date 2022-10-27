# Remover los datos de una colección

Para remover información de MongoDB se utiliza los métodos deleteOne() y deleteMany(), este recibe un documento el cual especifíca
las condiciones para encontrar los documentos a remover.

## Remover todos los documentos que coinciden con una condicion

```
db.restaurants.deleteMany( { "borough": "Manhattan" } )
```

## Remover solo 1

```
db.restaurants.deleteOne( { "borough": "Queens" } )
```

## Remover todos los documentos

**Nota:** No ejecute esta instrucción ya que se quedará sin datos.

```
db.restaurants.deleteMany({})
```

## Eliminar la colección

El método deleteMany solo borra los documentos de una colección, para borrar la colección completa y los índices de la colección
hay que utilizar el método drop()

```
db.restaurants.drop()
```
