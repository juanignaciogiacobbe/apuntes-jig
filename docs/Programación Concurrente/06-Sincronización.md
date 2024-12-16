> [!IMPORTANT] Semáforos
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
	- Si el valor es 0 o 1, se llaman semáforos binarios y se comportan igual que los [Locks](Programación%20Concurrente/05-Locks.md) de escritura(También conocidos como `Mutex`).
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

---


> [!IMPORTANT] Barreras en Rust
> Permiten sincronizar varios threads en puntos determinados de un calculo o algoritmo.
> Son reutilizables automáticamente.


> [!DANGER] Operaciones de Barriers
- `fn wait(&self)`: Bloquea al thread hasta que todos se encuentren en el punto.
- `is_leader(&self)`: Devuelve true en el thread líder, es decir el último de los threads que llama a `wait` y desbloquea al resto.

---

> [!IMPORTANT] Condvar
> - No guarda ningún valor.
> - Tiene asociado un FIFO.
> - 3 operaciones atómicas: `waitC(cond)`, `signalC(cond)`, `empty(cond)`.

---

> [!IMPORTANT] Monitors
> Permiten a los hilos tener exclusión mutua y la posibilidad de esperar(`block`) a que una condición se vuelva falsa. -> Tienen un mecanismo para señalizar otros hilos cuando su condición se cumple.


> [!WARNING] Los procesos pueden...
- Esperar para entrar al monitor.
- Ejecutar el monitor(solo un proceso a la vez -> Exclusión mutua).
- Estar bloqueado en FIFO de variable de condición.
- Recibir la liberación de la wait condition.
- Completar una operación `signalC`.

![](Programación%20Concurrente/img%20concu/Pasted%20image%2020241216090535.png)