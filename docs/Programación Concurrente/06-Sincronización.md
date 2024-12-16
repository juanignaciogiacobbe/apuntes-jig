
!!! note "Semáforos"
> Es un mecanismo de sincronización, implementado como una construcción de programación concurrente de mas alto nivel.
> Es un tipo de dato compuesto por dos campos:
> - Un entero no negativo llamado *V*.
> - Un set de procesos llamado *L*.

 ## Inicialización de semáforos
 - Se inicializan con un valor $k \geq 0$ y con el conjunto vacío $\emptyset$.
 - Se definen dos operaciones atómicas sobre un semáforo S:
	 - `wait(S)` también llamada `p(S)`.
	 - `signal(S)` también llamada `v(S)`.
- Un semáforo debe inicializarse con un valor entero no negativo.
- La instrucción `signal()` debe despertar a uno de los procesos suspendidos, pero no esta definido cual de todos los procesos debe despertarse.


## Sincronismo de acceso a un recurso
- Un semáforo es un contador:
	- Si contador $> 0$ -> Recurso disponible.
	- Si contador $\leq 0$  -> Recurso no disponible.
	- El valor del semáforo representa la cantidad de recursos disponibles.
	- Si el valor es 0 o 1, se llaman semáforos binarios y se comportan igual que los [[Programación Concurrente/05-Locks|Locks]] de escritura(También conocidos como `Mutex`).
- `p (wait)`: Resta 1 al contador.
- `v (signal)`: Suma 1 al contador.

## Semáforos en Rust
- Obtener el acceso(wait):

```
fn acquire(&self)
```

- Liberar el semáforo(signal):

```
fn release(&self)
```

## Implementación de un Semáforo

	struct Semaphore {
		condvar: Arc<Condvar>,
		counter: Arc<Mutex<i32>>
	}

	impl Semaphore {
		fn new(initial_count: i32) {
			// hay que chequear que initial count no sea negativo
			Semaphore {
				counter: Arc::new(Mutex::new(initial_count)),
				condvar: Arc::new(Condvar::new())
			}
		}

		fn wait(&self) {
			let mut count = self.counter.lock().unwrap();

			while *count <= 0 {
				count = self.condvar.wait(count);
			}

			*count -= 1;
		}

		fn signal(&self) {
			let mut count = self.counter.lock().unwrap();

			*count += 1;

			self.condvar.notify_all();
		}
	}

---


!!! note "Barreras en Rust"
> Permiten sincronizar varios threads en puntos determinados de un cálculo o algoritmo.
> Son reutilizables automáticamente.


> [!DANGER] Operaciones de Barriers
- `fn wait(&self)`: Bloquea al thread hasta que todos se encuentren en el punto.
- `is_leader(&self)`: Devuelve true en el thread líder, es decir el último de los threads que llama a `wait` y desbloquea al resto.

---

!!! note "Condvar"
> - No guarda ningún valor.
> - Tiene asociado un FIFO.
> - 3 operaciones atómicas: `waitC(cond)`, `signalC(cond)`, `empty(cond)`.

---

!!! note "Monitores"
> Permiten a los hilos tener exclusión mutua y la posibilidad de esperar(`block`) a que una condición se vuelva falsa. -> Tienen un mecanismo para señalizar otros hilos cuando su condición se cumple.


!!! warning "Los procesos pueden..."
- Esperar para entrar al monitor.
- Ejecutar el monitor(solo un proceso a la vez -> Exclusión mutua).
- Estar bloqueado en FIFO de variable de condición.
- Recibir la liberación de la wait condition.
- Completar una operación `signalC`.

![[Programación Concurrente/img concu/Pasted image 20241216090535.png]]