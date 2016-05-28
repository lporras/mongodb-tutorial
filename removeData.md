# Remover los datos de una colección

Para remover información de MongoDB se utiliza el método remove(), este recibe un documento el cual especifíca
las condiciones para encontrar los documentos a remover.

## Remover todos los documentos que coinciden con una condicion

```
db.restaurants.remove( { "borough": "Manhattan" } )
```

## Remover solo 1

```
db.restaurants.remove( { "borough": "Queens" }, { justOne: true } )
```

## Remover todos los documentos

**Nota:** No ejecute esta instrucción ya que se quedará sin datos.

```
db.restaurants.remove({})
```

## Eliminar la colección

El método remove solo borra los documentos de una colección, para borrar la colección completa y los índices de la colección
hay que utilizar el método drop()

```
db.restaurants.drop()
```
