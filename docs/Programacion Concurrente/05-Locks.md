# Locks
- Sirven para realizar **exclusión mutua** entre procesos.
- Se implementa mediante variables del tipo *lock*, que contienen el estado del mismo.
	- `lock()`: El proceso se bloquea hasta poder obtener el lock.
	- `unlock()`: El proceso libera el lock que tomo previamente.
- Para la implementación se necesita soporte tanto del hardware como del sistema operativo.

## Locks en UNIX
- Mecanismo de sincronismo de acceso a un archivo(o de cualquier otro recurso).
- Son *advisory* -> Los procesos pueden ignorarlos.
	- Locks de lectura o `shared locks`: Mas de un proceso a la vez puede tener el lock.
	- Locks de escritura o `exclusive locks`: Solo un proceso a la vez puede tener cualquier tipo de lock.


!!! warning "Condiciones para poder tomar un lock"
> - Para un *shared lock*, el proceso debe esperar hasta que sean liberados todos los *exclusive locks*.
> - Para poder tomar un *exclusive lock*, el proceso debe esperar hasta que sean liberados todos los locks(de ambos tipos).


!!! warning "Pasos para establecer un lock"
> 1. Abrir el archivo a lockear,
> 2. Aplicar el lock.
> 	1. Mediante `fcntl()` -> Se completan los campos del `struct flock`.
> 	2. Mediante `flock()`.
> 	3. Mediante `lockf()`: Interface construida sobre `fcntl()`.


## Locks en Rust

### Obtención de un lock de lectura
- `T` debe ser `Send` para ser compartido entre threads y `Sync` para permitir acceso concurrente entre lectores.
```
fn read(&self) -> LockResult<RwLockReadGuard<T>>
```

- Bloquea al thread hasta que se pueda obtener el lock con acceso compartido. Puede haber otros threads con el lock compartido.

```
fn write(&self) -> LockResult<RwLockWriteGuard<T>>
```

- Bloquea al thread hasta que se pueda obtener el lock con acceso exclusivo.
- Retornan una protección que libera el lock con RAII.
- Una vez obtenido el lock, se puede acceder al valor protegido.


!!! warning "Locks envenenados"
> Cuando un thread toma un thread de forma exclusiva(write lock) y mientras tiene tomado el lock, ejecuta `panic!`.
> Las llamadas posteriores a `read()` y `write()` sobre el mismo lock, devolverán `Error`.
