
!!! note "Programa"
> Conjunto de datos, asignaciones e instrucciones de control de flujo que compilan a instrucciones de máquina, las cuales se ejecutan secuencialmente en un procesador y acceden a datos almacenados en memoria principal o memorias secundarias.


!!! note "Programa Concurrente"
> Conjunto finito de programas secuenciales que pueden ejecutarse en paralelo. 
> - Cada uno de estos programas que lo conforman es un [[Sistemas Operativos/Proceso|Proceso]].
> - Los procesos están compuestos por un conjunto finito de instrucciones atómicas.


!!! note "Sistema Paralelo"
> Es un sistema compuesto por varios programas que se ejecutan simultáneamente en procesadores distintos.


!!! note "Multitasking"
> Ejecución de múltiples procesos concurrentemente en un cierto período de tiempo. El [[Sistemas Operativos/Scheduler|Scheduler]], parte del kernel del sistema operativo, se encarga de coordinar el acceso a los procesadores.


!!! note "Multithreading"
> Construcción provista por algunos lenguajes de programación que permite la ejecución concurrente de threads del mismo programa.


!!! note "Ejecución del Programa Concurrente"
> Resulta al ejecutar una secuencia de instrucciones atómicas que se obtiene de intercalar arbitrariamente las instrucciones atómicas de los procesos que lo componen.

![[Programación Concurrente/img concu/Pasted image 20240929114224.png]]

!!! warning "Ejecución de las instrucciones atómicas"
> Una instrucción atómica puede ejecutarse de principio a fin sin interrupciones, o directamente no ejecutarse. 
