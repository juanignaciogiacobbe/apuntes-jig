# Esquema de Procesamiento de una Consulta

![](Base%20de%20Datos/img/Pasted%20image%2020241205085221.png)

- El Parser & Translator se encarga de rechazar consultas inválidas.
- El Optimizador se encarga de convertir la consulta de [SQL](Base%20de%20Datos/SQL.md) a una equivalente en [Álgebra Relacional](Base%20de%20Datos/Álgebra%20Relacional.md).
- El Evaluation Engine se encarga de evaluar el plan de ejecución, y devuelve el resultado en base a los datos.

## Planes de Consulta y de Ejecución
1. La optimización de una consulta inicia con una expresión de álgebra relacional equivalente a la consulta SQL.
2. Mediante heurísticas, la expresión se convierte en una expresión equivalente, obteniéndose un plan de consulta.
3. En base a los metadatos que se encuentran en el catálogo, se elige cómo resolver cada operador de álgebra relacional, obteniéndose el plan de ejecución(Estructuras de Datos, Índices y algoritmos a usar).


> [!WARNING] Reglas de Equivalencia
- Al convertir una consulta de SQL a AR, se pasa de un lenguaje declarativo a uno procedural.
- Si existen varias expresiones de AR equivalentes a la consultas SQL, es probable que sus costos no sean iguales. -> Nos interesa poder encontrar consultas equivalentes pero que nos den la mejor performance.
	- Se usan heurísticas que suelen funcionar bien en la mayoría de los casos.
	- El objetivo general es reducir el tamaño de relaciones intermedias -> Para aprovechar **pipelining** se prefieren árboles "left deep" en el que los hijos derechos siempre son accesos a tablas.

![](Base%20de%20Datos/img/Pasted%20image%2020241205090606.png)


> [!WARNING] Reglas Generales
- Realizar las selecciones lo antes posible.
- Reemplazar productos cartesianos por juntas cuando se pueda.
- Proyectar para descartar atributos no utilizados lo antes posible.
	- Priorizar selección antes que selección.
	- Tener cuidado si el árbol no queda left deep(evaluar pipelining).
- Realizar las juntas más restrictivas primero.


---

## Estimación del Costo
- Para poder elegir un método sobre otro, el [DBMS](Base%20de%20Datos/02-Database%20Management%20System(DBMS).md) estima cuánto le costará resolver la consulta con cada método y elige el de menor costo estimado.
	- La estimación tiene un costo mucho menor a ejecutar la consulta.
- Para esto se tiene la información sobre los datos de las tablas.

### Catálogo - Información Disponible
- `n(R)`: Cantidad de filas de la tabla R.
- `B(R)`: Cantidad de bloques que ocupa la tabla R.
- `F(R)`(factor de bloque): Cantidad de filas por bloque en la tabla R. Se puede calcular como:
$$
	n(R)/B(R)
$$
- `V(A, R)`(Variabilidad de A en R): Cantidad de distintos valores que tiene el atributo A en la tabla R.
- `Height(I(A, R))`: Altura del índice, para índices de tipo árbol.


> [!IMPORTANT] Índices
> Son estructuras de búsqueda almacenadas y actualizadas en el DBMS, que agilizan la búsqueda de registros a partir del valor de un atributo o conjunto de atributos.
> - Indican en qué bloques están las filas con un cierto valor en una o más columnas.
> - Se pueden indexar los datos de una tabla por una o más expresiones.
> - El Índice, generalmente implementado como un Árbol B+, guardará para cada valor posible de las expresiones, en qué bloque o bloques hay filas con ese valor.
> - Esto agiliza la búsqueda por esas expresiones.
