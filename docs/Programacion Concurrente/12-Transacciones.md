# Transacciones
## Modelo de Transacciones
- El sistema está conformado por un conjunto de procesos independientes -> Cada uno puede fallar aleatoriamente.
- Los errores en la comunicación son manejados transparentemente por la capa de comunicación.
- Storage estable:
	- Se implementa con discos.
	- La probabilidad de perder los datos es extremadamente pequeña.


### Primitivas
- `BEGIN TRANSACTION`: Marca el inicio de la transacción.
- `END TRANSACTION`: Finaliza la transacción e intenta hacer commit.
- `ABORT TRANSACTION`: Finaliza forzadamente la transacción y restaura los valores anteriores.
- `READ`: Lee datos de un archivo u otro objeto.
- `WRITE`: Escribe datos a un archivo u otro objeto.

## Propiedades ACID
- Atómicas: La transacción no puede ser dividida.
- Consistentes: La transacción cumple con todos los invariantes del sistema.
- Aisladas o serializadas: Las transacciones concurrentes no interfieren con ellas mismas.
- Durables: Una vez que se commitean los cambios, son permanentes.

## Implementación

### Private Workspace
- Al iniciar una transacción, el proceso recibe una copia de todos los archivos a los cuales tiene acceso.
- Hasta que hace commit, el proceso trabaja con la copia.
- Al hacer commit, se persisten los cambios.
- Es extremadamente costoso salvo por optimizaciones.

### Writeahead Log
- Los archivos se modifican in place, pero se mantiene una lista de los cambios aplicados(primero se escribe la lista y luego se modifica el archivo).
- Al commitear la transacción, se escribe un registro commit en el log.
- Si la transacción se aborta, se lee el log de atrás hacia adelante para deshacer los cambios(rollback).

### Commit en Dos Fases
- El coordinador es aquel proceso que ejecuta la transacción.
- Fase 1:
	1. El coordinador escribe `prepare` en su log y envía el mensaje `prepare` al resto de los procesos.
	2. Los procesos reciben el mensaje, escriben `ready` en el log y envían `ready` al coordinador.
- Fase 2:
	1. El coordinador hace los cambios y envía el mensaje `commit` al resto de los procesos.
	2. Los procesos que reciben el mensaje, escriben `commit` en el log y envían `finished` al coordinador.


## Control de Concurrencia
- Lockeo: Two-phase locking
	- Fase de expansión: Se toman todos los locks a usar.
	- Fase de contracción: Se liberan todos los locks(no se pueden tomar nuevos locks).
	- Garantiza propiedad serializable para las transacciones.
	- Pueden ocurrir deadlocks.
	- Strict two-phase locking: La contracción ocurre después del commit.
- Concurrencia Optimista
	- El proceso modifica los archivos sin ningún control, esperando que no haya conflictos.
	- Al commitear, se verifica si el resto de las transacciones modificó los mismos archivos -> Si es así, se aborta la transacción.
	- Ventajas: Libre de deadlocks y favorece el paralelismo.
	- Desventajas: Rehacer todo puede ser costoso en condiciones de alta carga.
- Timestamps
	- Existen timestamps únicos globales para garantizar orden.
	- Cada archivo tiene dos timestamps: Lectura y escritura y qué transacción hizo la última operación en cada caso.
	- Cada transacción al iniciarse recibe un timestamp.
	- Se compara el timestamp de la transacción con los timestamps del archivo:
		- Si es mayor, la transacción está en orden y se procede con la operación.
		- Si es menor, la transacción se aborta.
	- Al commitear se actualizan los timestamps del archivo.
