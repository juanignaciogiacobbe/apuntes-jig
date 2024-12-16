# Repaso Final

## Final 26/07/2022

![[Programacion Concurrente/img concu/Pasted image 20241209144800.png]]

1. Un deadlock ocurre cuando dos o más procesos o hilos en un sistema no pueden continuar con su ejecución, debido a que cada uno de ellos se queda esperando a que otro libere un recurso que necesita. Aquí se genera un ciclo, ya que los procesos no pueden avanzar: Cada uno está esperando a que el otro libere el recurso requerido. Al tener un sistema distribuido, se tiene la necesidad de coordinación para que las entidades entren en su sección crítica. Para que se produzca un deadlock tienen que cumplirse los siguientes 4 requisitos:
	- Exclusión Mutua: Al menos un recurso debe ser retenido en modo exclusivo por un proceso en un momento dado.
	- Espera y Retención: Un proceso debe retener al menos un recurso mientras espera la adquisición de recursos adicionales que actualmente están siendo retenidos por otros.
	- No liberación voluntaria: Un proceso no puede liberar voluntariamente los recursos que tiene en su posesión.
	- Espera circular: Debe haber una cadena circular de dos o más procesos, cada uno de los cuales están esperando un recurso que posee el siguiente proceso en la cadena.


![[Programacion Concurrente/img concu/Pasted image 20241209145440.png]]

1. El robo de trabajo se da cuando un worker comienza a tomar tareas de otros, debido a que se terminaron su trabajo y quedaron libres. La idea de esto es seguir exprimiendo el uso de las CPUs al máximo. Cada thread va a tener una cola de tareas asignadas, y la idea es que se vayan partiendo las tareas en sub-tareas cada vez más pequeñas, y que el thread vaya ejecutando las tareas del final de su cola. Cuando un thread no tiene más trabajo en su cola, toma tareas del inicio de la cola de otro thread(este es elegido de forma random, y se toma del principio de su cola para evitar colisiones), de forma tal de balancear aún más las cargas de trabajo en los threads.
2. Lo que se genera al tener una única cola de tareas es que los threads van a estar constantemente haciendo `lock` de la cola, y agrandaríamos los tiempos de espera de ciertos threads para que se les asigne un trabajo. -> No estamos aprovechando el uso intensivo de la CPU.


![[Programacion Concurrente/img concu/Pasted image 20241212084502.png]]

1. La programación asincrónica es un modelo de programación concurrente en donde se utilizan unidades de ejecución mucho más livianas y más rápidas de crear, llamadas tareas asincrónicas. Estas tareas ejecutan menos memoria que los threads, por lo que usarlas tienen menos overhead. Este modelo tiene las siguientes características:
	- La restricción la tiene en que tipo de procesamiento voy a hacer.
	 	- La mayor parte del tiempo la tengo que pasar en "espera"(poco computo).
	 	- Usarlas nos da menor overhead de memoria -> Se pueden tener miles o decenas de miles en un programa.
	 	- El código asincrónico luce como el de threads, salvo que las operaciones se bloquean y se manejan diferente.

	La idea es intercalar las tareas asincrónicas en un mismo thread o pool de threads. Este modelo se suele utilizar para procesamientos en donde hayan muchos tiempos de espera debido a que se pueden toman otras tareas mientras se espera a terminar la ejecución de ciertas system calls.
	Usando programación asincrónica, se programa de una forma casi idéntica a como se programa con programación sincrónica. -> No se va a esperar por las operaciones bloqueantes, pero cuando estas terminen, se sigue con la ejecución del código de forma secuencial.

2. Rust tiene el trait `Future`, `async`, `await`, `block_on`.


![[Programacion Concurrente/img concu/Pasted image 20241212090026.png]]

1. Writeahead Log:
	- Los archivos se modifican in place, pero se mantiene una lista de los cambios aplicados(primero se escribe la lista y luego se modifica el archivo).
	- Al commitear la transacción, se escribe un registro commit en el log.
	- Si la transacción se aborta, se lee el log de atrás hacia adelante para deshacer los cambios(rollback).
	- Tiene bajos costos de cómputo ya que no se realizan verificaciones previas a la escritura de datos. -> Más rápido.
	- Se tiene que hacer una validación del estado final del log porque es posible que se requiera hacer un rollback.
	- En caso de tenerse muchas T que modifiquen elementos relacionados, al hacer rollback se deberán deshacer muchas T.
	- En caso de tener T muy grandes o en caso de tener mucha probabilidad de conflictos, se suele tener un mal desempeño.

	Private Workspace:
	- Al iniciar una transacción, el proceso recibe una copia de todos los archivos a los cuales tiene acceso.
	- Hasta que hace commit, el proceso trabaja con la copia.
	- Al hacer commit, se persisten los cambios.
	- Evita problemas propios de la concurrencia como la lectura sucia, escritura sucia o la anomalía del fantasma.
	- Hay mayor solapamiento.
	- Es eficiente en caso de tener pocas T grandes.
	- Desventaja: Es extremadamente costoso salvo por optimizaciones.
	- Puede ser costoso unir los snapshots finales, ya que en caso de haber conflictos se deberá deshacer alguna de ellas.

---

## Final 08/08/2023

1. Que se entiende por deadlock.

	Un deadlock se da cuando tenemos un sistema con dos o más procesos que no pueden hacer avances productivos, debido a que están en un ciclo, en el cual estos procesos se quedan esperando por algún recurso retenido por otro proceso. Dado que ninguno llega a finalizar, el trabajo nunca es finalizado, y el sistema queda bloqueado indefinidamente. Para que se dé un deadlock tienen que ocurrir los siguientes 4 eventos:
	- Exclusión Mutua: Al menos uno de los procesos debe tomar indefinidamente un recurso compartido de forma exclusiva(ningún otro puede tomar ese recurso).
	- Espera y retención: Uno de los procesos retiene un recurso mientras espera por otros recursos adicionales tomados por otros procesos.
	- No se permite la liberación voluntaria de recursos: Cuando un proceso toma un recurso, no es capaz de liberarlo -> Tiene que terminar su tarea para liberarlo.
	- Espera circular: Debe haber una cadena circular de dos o más procesos, cada uno de los cuales están esperando un recurso que posee el siguiente proceso en la cadena.

2. Que dificultades adicionales presenta la posibilidad de existencia de deadlocks en un ambiente de Concurrencia Distribuida respecto a un ambiente Centralizado.

	En la concurrencia distribuida se agrega una complejidad en la comunicación con respecto a los ambientes centralizados, ya que se pueden dar problemas como que los mensajes no lleguen en orden, alguno de los nodos puede caerse, etc. Usar este tipo de ambientes nos lleva a realizar modificaciones complejas a los algoritmos, ya que podemos llegar a necesitar implementar una detección de deadlocks, elecciones de líderes, etc.

![[Programacion Concurrente/img concu/Pasted image 20241213141922.png]]

Un socket contiene una API que nos permite por medio de una dirección comunicar entidades que pueden encontrase en lugares físicamente distintos, a través de una red o de manera local.

- Stream sockets: usan el protocolo TCP: entrega garantizada del flujo de bytes.
- Datagram sockets: usan el protocolo UDP: la entrega no está garantizada; servicio sin conexión.
- Raw sockets: permiten a las aplicaciones enviar paquetes IP.
- Sequenced packet sockets: similares a stream sockets, pero preservan los delimitadores de registro. Utilizan el protocolo SPP (Sequenced Packet Protocol).

Para ese caso usaría UDP ya que **inserte justificación genérica de redes**.

---

## Final 06/02/2024

1. Explicar en detalle cómo se implementa un semáforo.

![[Programacion Concurrente/img concu/Pasted image 20241213083318.png]]

```
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
```


2. Cual es la justificación tras el modelo de actores. Escribir detalladamente todas las características de los actores.

	El modelo de actores es un modelo similar al de pasaje de mensajes. Es un modelo de concurrencia distinto que impone las reglas de cómo tiene que estar estructurado nuestro programa.
	
	El actor es la primitiva principal del modelo. Son livianos, por lo que se pueden crear miles (a diferencia de los threads). Los actores encapsulan comportamiento y estado interno. Estas variables son propias e independientes de cada actor: un estado no puede acceder al estado de otro actor.
	
	Están compuestos por una dirección (que es a donde se les envía mensajes) y una casilla de correo (una cola de los últimos mensajes recibidos).
	
	Los actores son aislados entre sí y no comparten memoria. El estado sólo cambia a partir de procesar los mensajes recibidos, y sólo se puede manejar un mensaje a la vez. Además, en un sistema distribuido, la dirección del actor puede ser una dirección remota.****

	Los actores se comunican entre ellos mediante el enviado de mensajes(son estructuras simples inmutables). Estos mensajes son procesados por los actores de forma asincrónica.

	Los actores mantienen el contexto interno de ejecución, o estado. Permite al actor determinar su dirección, cambiar los límites de la casilla de mensajes, o detenerse. Los mensajes llegan a la casilla primero, luego el contexto de ejecución llama al handler específico.


3. Explicar el algoritmo distribuido de exclusión mutua. Hacer un diagrama de un ejemplo. Que problemas puede traer la exclusión mutua en sistemas distribuidos con respecto a una sola computadora.

	En este algoritmo, cuando un proceso quiere entrar en la sección crítica, construye un mensaje con el nombre de la sección crítica, el número de proceso y el timestamp. Al recibir el mensaje:
	- Si no está en la SC y no quiere entrar, envía OK.
	- Si está en la SC, no responde y encola el mensaje. Cuando sale de la SC, envía OK.
	- Si quiere entrar en la SC, compara el timestamp, y gana el menor.

	Podemos tener estos problemas con respecto a usar una sola computadora:
	- Agregar mensajes implica congestionar la red -> Añade latencia y costos de comunicación.
	- Pueden haber fallas de red y desconexiones -> Problemas de sincronización. Además, hay que gestionar la fault tolerance.
	- Starvation.
	- Consistencia de Estados -> No es fácil asegurar que todos los procesos tengan una vista consistente del sistema.
	- Mayor complejidad de implementación.


4. Que tipos de eventos hay en ambientes distribuidos. Como se mide el costo y complejidad. Como está conformado el estado interno de una entidad y como se modifica

	En un ambiente distribuido, las entidades responden solamente a eventos externos(por eso se dice que son reactivas). Los posibles eventos son:
	- Llegada de un mensaje.
	- Activación del reloj.
	- Un impulso espontáneo.
	A excepción del impulso espontáneo, los eventos se generan dentro de los límites del sistema. Los eventos desencadenan acciones en un tiempo futuro. Los distintos delays resultan en distintas ejecuciones del protocolo con posibles resultados diferentes.
	- Los eventos disparan acciones que pueden generar nuevos eventos.
	- Si suceden, los nuevos eventos ocurrirán en un tiempo futuro: `Future(t)`.
	- Una ejecución se describe por la secuencia de eventos que ocurrieron.

	El costo y complejidad son las medidas de comparación de los algoritmos distribuidos, y para medirlos se usan dos métricas:
	- Cantidad de actividades de comunicación:
		- Cantidad de transmisiones o costo de mensajes(M).
		- Carga de trabajo por entidad y carga de transmisión.
	- Tiempo:
		- Tiempo total de ejecución del protocolo.
		- Tiempo ideal de ejecución: Tiempo medido bajo ciertas condiciones, como delays de comunicación unitarios y relojes sincronizados.

	El estado interno de $x$ en el instante $t$ -> $\sigma(x, t)$: contenido de los registros de $x$ y el valor del reloj $c_x$ en el instante $t$.
	- El estado interno de una entidad cambia con la ocurrencia de eventos.

5. Implementar en modelo de actores el algoritmo de elección de lider anillo. Hacer un diagrama mostrando un ejemplo.

	Por simplicidad, hacemos que 



---

## Final 10/12/2024

![[Programacion Concurrente/img concu/Pasted image 20241213143114.png]]

1. El problema de la sección crítica se da cuando tenemos varios procesos que se ejecutan en loop, cuyos códigos pueden separarse en sección crítica y sección no crítica. Para todos estos procesos, la sección crítica debe progresar(y eventualmente finalizar), y la sección no crítica no requiere progreso(es decir que el proceso puede terminar o entrar en un loop infinito). Las especificaciones de corrección de la misma son:
	- Exclusión Mutua: No podemos intercalar instrucciones de varias secciones críticas.
	- Ausencia de Deadlocks: Si dos procesos están tratando de entrar a la sección crítica, eventualmente alguno de ellos debe tener éxito.
	- Ausencia de Starvation: Si un proceso trata de entrar a la sección crítica, eventualmente debe tener éxito.

![[Programacion Concurrente/img concu/Pasted image 20241213144708.png]]

1. Las redes de petri nos permiten modelar, analizar y simular sistemas concurrentes y distribuidos de forma gráfica. Es un grafo bipartito, compuesto por transiciones(eventos que disparan los cambios de estados) y lugares(son los estados del sistema).
	- Las redes ordinarias de petri son redes en las cuales todos sus arcos tienen un peso igual a 1. Esto quiere decir que cuando una transicion se dispara, mueve un token por arco desde cada input hacia el output. 
	- Las redes generales de petri nos permiten que sus arcos tengan pesos arbitrarios(mayores o iguales a 1). Esto quiere decir que si disparamos una transicion, se puede mover un numero especifico de tokens, definido por el peso del arco.

2. El **grafo de alcance** (también conocido como **grafo de estados alcanzables**) es una representación gráfica que muestra todos los estados posibles que puede alcanzar una Red de Petri a partir de un estado inicial dado, mediante la ejecución (disparo) de sus transiciones. Un **estado** en una Red de Petri está definido por una **marcación** M, que es la distribución de tokens en las plazas. El **grafo de alcance** es un **grafo dirigido**, donde:
    - Cada **nodo** representa una marcación posible del sistema.
    - Cada **arco** representa el disparo de una transición que lleva de una marcación a otra.
