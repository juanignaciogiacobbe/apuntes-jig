# Programación Asincrónica


 !!! warning "Problema del uso de Threads"
> Si una aplicación va creando muchos threads, cada uno puede tener 100kB de stack -> Puede ser un problema la demanda de memoria.


!!! note "Tareas Asincrónicas de Rust"
> Se las pueden usar para intercalar tareas en un único thread o en un pool de threads.
> Son mucho mas livianas que los threads, más rápidas de crear, y más eficientes para pasarles el control.
> - La restricción la tiene en qué tipo de procesamiento voy a hacer.
> - La mayor parte del tiempo la tengo que pasar en "espera"(poco cómputo).
> - Usarlas nos da menor overhead de memoria -> Se pueden tener miles o decenas de miles en un programa.
> - El código asincrónico luce como el de threads, salvo que las operaciones se bloquean y se manejan diferente.

## Ejemplo Sincrónico

![[Programacion Concurrente/img concu/Pasted image 20241002173225.png]]

- La mayor parte del tiempo, el thread principal esta bloqueado a la espera de system calls. -> Para evitar esto, un thread debe poder tomar otras tareas mientras espera que la system call se complete.

![[Programacion Concurrente/img concu/Pasted image 20241002173337.png]]



!!! note "Futures"
> Representa una operación sobre la que se puede testear si se completó.
> El método *poll* nunca bloquea.
> Si la operación se completó, retorna `Poll:Ready(output)`, y si no se completó, retorna `Pending`.
> **Modelo piñata**: Lo único que se puede hacer con un future es golpearlo con poll hasta que caiga el valor.

- Cada vez que un Future es polleado, avanza todo lo que puede.
- Almacena lo necesario para realizar el pedido hecho por la invocación.
- Crate `async-std`: Provee versiones async de las facilidades de I/O de la std.
	- La arquitectura async de Rust esta diseñada para ser eficiente.
	- Se llama a Poll solamente cuando vale la pena(algo debe retornar `Ready`, o progresar al objetivo).


## Ejemplo Async

![[Programacion Concurrente/img concu/Pasted image 20241002174038.png]]

- Invocar a una función async retorna inmediatamente, antes de que comience a ejecutarse el cuerpo de la función.
- Se obtiene un `Future` del valor, que contiene todo lo necesario para que la función pueda ejecutarse(argumentos, espacio para variables locales, etc).
- El tipo específico es generado al momento de compilar.
- Al ejecutar `poll` por primera vez sobre el retorno, se ejecuta el cuerpo de la función hasta el primer `await`.
- Si no se completó, retorna `Pending` y toda la función devuelve ese valor/estado.
- La expresión `await` toma ownership del `Future` y hace el `poll`.
- Si esta `Ready`, el valor final del `Future` es el valor devuelto en la función `await`, y continua. -> En caso contrario, retorna `Pending` a su función que lo invocó.
- La siguiente invocación a `poll` sobre la función `cheapo_request`, continuará desde el punto donde estaba el future connect.
- El `Future` almacena el punto donde debe retomarse en el siguiente `poll` y el estado local.
- Las expresiones `await` tienen la capacidad de continuar, se pueden usar solamente en funciones async.

## `block_on`
- Es una función sincrónica que produce el valor final de la función asincrónica.
- Es un adaptador del mundo asincrónico al sincrónico.
- No debe usarse en una función async, ya que bloquea a todo el thread.
- Conoce cuanto hacer sleep hasta hacer `poll` de nuevo.
- La función async retorna un `Future` -> Alguien debe esperar por el valor.

![[Programacion Concurrente/img concu/Pasted image 20241002174751.png]]


![[Programacion Concurrente/img concu/Pasted image 20241002174958.png]]


## Creación de tareas async
- `async_std::task::spawn_local` recibe un `Future` y lo agrega a un pool que realizará polling en el `block_on`. Es análogo a `spawn` de thread.
- Todas las ejecuciones pueden realizarse en un único thread. Una llamada asincrónica ofrece la apariencia de una única llamada a una función que se ejecuta hasta que se completa. Pero es realizada por una serie de llamadas sincrónicas al método `poll`, que retorna rápidamente, hasta que se completa.
- El cambio de una tarea a otra ocurre solamente en las expresiones `await` -> Un cómputo grande en una función no daría lugar a la ejecución de otras tareas.