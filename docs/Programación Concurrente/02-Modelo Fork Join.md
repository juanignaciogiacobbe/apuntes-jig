
!!! note "Fork-Join"
> Es un modelo de paralelización donde el cómputo(task) es partido en sub-cómputos menores(sub-tasks). Los resultados de estos se unen(join) para construir la solución al cómputo inicial.
> Partir la task se realiza en general de forma recursiva:
> - Los sub-cómputos son independientes(NO dependen de nada) -> El cómputo se puede realizar en paralelo. 
> - Las sub-tareas se pueden crear en cualquier momento de la ejecución de la tarea.
> - Las tareas no deben bloquearse, excepto para esperar el final de las sub-tareas.

![[Programación Concurrente/img concu/Pasted image 20241002165245.png]]


!!! warning "Caracteristicas del Fork-Join"
- Es un modelo de Concurrencia sin condiciones de carrera.
- Los programas son *determinísticos*, y los threads están aislados. El programa produce el mismo resultado independientemente de las diferencias de velocidad de los threads.
- **Performance**: En el caso ideal es $t_{secuencial}/N_{threads}$ -> Puede variar por diferencias en el tamaño de una tarea, y porque se debe realizar procesamiento para hacer la combinación de los resultados individuales.


![[Programación Concurrente/img concu/Pasted image 20241002165751.png]]



!!! quote "MapReduce"
> Is a programming model and an associated implementation for processing and generating large data sets. Users specify a map function that processes a key/value pair to generate a set of intermediate key/value pairs, and a reduce function that merges all intermediate values associated with the same intermediate key.

## Work Stealing
- Es un algoritmo utilizado para hacer scheduling de tareas entre threads.
- Los worker threads inactivos roban trabajo a otros threads ocupados, para realizar balanceo de carga.
	- Cada thread mantiene su propia cola de dos extremos donde almacena las tareas listas por ejecutar.
	- Cuando un thread termina la ejecución de una tarea, coloca las sub-tareas creadas al final de la cola.
	- Toma la siguiente tarea para ser ejecutada del final de la cola.
	- Si la cola esta vacía, y el thread no tiene mas trabajo, trata de roba tareas del inicio de una cola de otro thread(random).
- Los worker threads se comunican solamente cuando lo necesitan -> Menor necesidad de sincronización.
- La implementación de la cola deque agrega bajo overhead de sincronización.

## Rayon
> Implementa el modelo de Fork-Join de dos formas:
1. Realizar dos tareas en paralelo:
``` 
	let (v1, v2) = rayon::join(fn1, fn2);
```

- Invoca a `fn1` y `fn2`, y retorna una tupla con ambos resultados.

2. Realizar N tareas en paralelo:

```
	giant_vector.par_iter().for_each(|value| {
		do_thing_with_value(value);
	})
```

- El método `par_iter()` crea un iterador `ParallelIterator` similar a los iteradores de Rust. Rayon maneja los threads y distribuye el trabajo.

![[Programación Concurrente/img concu/Pasted image 20241002170744.png]]


- Desde afuera, Rayon parece crear una tarea por elemento del vector, pero internamente, crea un worker thread por núcleo de CPU, e implementa Work Stealing.
- Los métodos `reduce()` y `reduce_with()` se usan para combinar los resultados.


## Crossbeam
- Provee estructuras de datos y funciones para concurrencia y paralelismo.
- `crossbeam::scope` crea un nuevo entorno de thread que garantiza que los threads terminan antes de retornar el closure que se le pasa como argumento a esta funcion.
- Todos los threads que no fueron manualmente esperados(join), son esperados antes de que finalice la invocación de la función.
- Si todos terminan exitosamente, se retorna `Ok`, y si alguno ejecuto `panic`, se retorna `Err`.