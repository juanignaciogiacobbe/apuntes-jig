# Multitasking y Comunicación
- Se tienen muchos programas a la vez en ejecución. -> La idea es elegir el modelo que corresponda(hay ventajas y desventajas en cada caso).

![[Sistemas Distribuidos I/img/Pasted image 20250319081006.png]]

## Multithreading
- Recursos compartidos:
	- Heap.
	- Data Segment.
	- File Descriptors.
	- Code Segment(read-only). -> Se levanta y corre el mismo programa.
- Sincronización:
	- Soporte threading del SO(pthread-mutex, etc).
	- Soporte threading del runtime(threads Java, .NET, etc.).
	- Inter Process Communication(IPC). 
- Características clave:
	- Sencillo compartir información entre threads.
	- Alto acoplamiento entre componentes del sistema.
	- Escasa estabilidad -> 1 thread defectuoso afecta a todo el sistema.
	- Escalabilidad muy limitada. -> La memoria es única, el procesador es único, y no le puedo dar más potencia a menos que frene todo y mejore la computadora.

---
## Multiprocessing
- Recursos compartidos:
	- Code Segment(read-only). -> Cada proceso tiene su propia memoria.
- Sincronización:
	- Inter Process Communication(IPC).
		- Signals
		- Shared memory
		- Sockets
		- Pipes/ FIFOs
		- Semáforos
		- Queues.
		- Locks
- Características clave:
	- No es trivial compartir información entre procesos.
	- Componentes separados, en general simples.
	- Más escalable y más estable que multithreading.
	- Sin tolerancia a fallos de hardware, sistema operativo, etc.
	- Los problemas los tiene el proceso consigo mismo(No comparte nada con nadie). Se gana performance([[Sistemas Distribuidos I/03-Paralelización de Tareas|Paralelismo]]).

---
## Multicomputing
- Recursos compartidos:
	- Ninguno.
- Sincronización:
	- Mensajes Ad-Hoc entre Computadoras -> Necesidad de implementar mecanismos de sincronización. Se comparten menos recursos pero hay más necesidad de sincronización.
- Características clave:
	- Comunicación de Red -> Problemas por limitaciones de ancho de banda, latencia y pérdida de mensajes.
	- Comunicación entre procesos compleja y central al diseño del sistema.
	- Alta escalabilidad y tolerantes a fallos.


### Taxonomía de Flynn
- Clasificación de sistemas de acuerdo a la cardinalidad de flujos de instrucciones(procesadores) y flujos de datos(memoria).
	- **SISD**(Single Instruction, Single Data): Modelo estándar de un procesador sin paralelismo.
	- **SIMD**(Single Instruction, Multiple Data): Array processors. Ejemplo: GPU.
	- **MISD**(Multiple Instruction, Single Data): No son usuales(procesar múltiples veces los mismos datos de forma determinística retorna el mismo resultado).
	- **MIMD**(Multiple Instruction, Multiple Data): Se divide en dos modelos
		- Multiprocessors(?): Con memoria y/o clock compartidos.
		- Multicomputers: Sin memoria ni clock compartidos.
		![[Sistemas Distribuidos I/img/Pasted image 20250319091343.png]]


#### MIMD: UMA vs NUMA
- Colisión entre procesadores para acceder a la memoria. Los procesadores se conectan mediante un bridge.
- Uniform Memory Access(UMA)
	- Tiempo de acceso a la memoria es idéntico para todos los procesadores(Parecido a la caché).
- Non Uniform Memory Access(NUMA)
	- Ideado en SGI, ahora presente en Linux Kernel y MS Servers.
	- Cada CPU controla un bloque de memoria y se transforma en su "home agent".
	![[Sistemas Distribuidos I/img/Pasted image 20250319091553.png]]
	- Cada computadora tiene su propia memoria local.
	- Cada computadora puede fallar de forma independiente.
	- No poseen un reloj central de ejecución de instrucciones.
	- Requieren comunicación entre computadoras(necesidad de implementar mecanismos de sincronización):
		- Networking: LAN, MAN, WAN

---
## Propiedades de Sistemas Distribuidos
- Safety Properties(Siempre verdaderas)
	- Exclusión Mutua.
	- Ausencia de Deadlocks.
- Liveness Properties(Eventualmente verdaderas)
	- Ausencia de Starvation.
	- Fairness.

- Asegurar el estado safety de propiedades de un sistema se transforma en un pilar de la teoría de concurrencia.


| Basada en Algoritmos                                                                  | Basada en Abstracciones                                                  |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| Sin existencia de abstracciones especiales.                                           | Basada en abstracciones provistas por el SO.                             |
| Condiciones lógicas simples para asegurar el cumplimiento de cierta Critical Section. | Permite construir mecanismos compuestos por combinaciones de las mismas. |

### Basados en Algoritmos
- **Busy-Waiting**: Responsable de la mayoría de los problemas de performance en sistemas concurrentes.
- **Spin-Lock**: Caso más simple de Busy-Wait(`while(flag)`).
- **Algoritmos de Espera**: Dekker, Lamport(del panadero), Peterson, etc.
- **Operaciones Atómicas:** Mecanismos provistos por un lenguaje para actualizar variables/objetos sin utilizar mecanismos de sincronización
	- Contadores atómicos de tipos POD(int, char, double, etc.).
	- CAS(Compare and Swap): Operación por excelencia para actualizar contenedores forma segura en ambientes multithreading.


---
## Inter-Process Communication(IPCs)
- Permiten la comunicación entre dos o más procesos.
- Provistos por el SO.
- Creación y destrucción exceden la vida del proceso
	- Usuario es responsable de la vida de los mismos.
	- Proceso `Launcher` y `Terminator` para administrar la vida de los mismos.
- Usualmente identificados por nombre.
- En Linux todos los IPCs son vistos como diferentes tipos de archivos.

![[Sistemas Distribuidos I/img/Pasted image 20250313181057.png]]

### Signals
- Existen 31 tipos distintos(`kill -l`).
- Cada proceso decide cuales handlear. `SIGSTOP` y `SIGKILL` son la excepción.
- Ejemplos de signals estándar:
	- `SIGINT` y `SIGTERM`: Graceful Quit.
	- `SIGSEGV`: Problemas en la memoria.
	- `SIGABRT`: Code assertions.
- Propagación de signals en threads.

### Shared Memory
- Mecanismo provisto por el SO(Linux) para compartir recursos.
- Abstracción inexistente en threads: Heap entre dos threads de un mismo proceso es compartido.
- Su tamaño se define al ser creada.
- Mutex es necesario solo si dos procesos no pueden acceder a la memoria al mismo tiempo(e.g. shared counter).

![[Sistemas Distribuidos I/img/Pasted image 20250313181527.png]]

### File Locks
- Control de acceso a un file descriptor
	`int flock(int fd, int operation);`
- Existen dos tipos
	- Shared Lock(R): Read only lock.
	- Exclusive Lock(W): RW lock. -> Sólo un exclusive lock por File.


### Pipes y FIFOs
- Pasaje de información directa entre 2 procesos.
- Linux provee una API de un archivo para la escritura/lectura.
- Unnamed Pipes(Pipes)
	- Comunicación entre procesos padre e hijo.
	- Dejan de existir al finalizar el proceso.
- Named Pipes(FIFO)
	- Comunicación entre dos procesos cualesquiera.
	- Viven en el SO por lo cual excede la vida del proceso.

![[Sistemas Distribuidos I/img/Pasted image 20250313181830.png]]


### Message Queues(System V)
- Procesos escriben/reciben bloques de bytes.
- Campo `mtype`
	- Identifica el tipo de mensaje.
	- Sender debe enviar mensajes con `mtype > 0`.
	- Receptor con `mtype = 0` recibe mensajes sin importar el `mtype`.
	- Caso esotérico: Receptor con `mtype < 0`.
- Mensajes leídos son removidos de la cola.
- Buffer size definido durante la creación.

![[Sistemas Distribuidos I/img/Pasted image 20250313182115.png]]

