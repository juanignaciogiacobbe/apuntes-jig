# Introducción a los Sistemas Distribuidos
- Los Sistemas Distribuidos cobran gran relevancia debido al constante crecimiento del nivel de integración e interdependencia entre sistemas, volúmenes de datos a procesar, capacidades de cómputo, paralelismo y virtualización.
- Presentes por ejemplo en Big Data, Data Analytics, ML, etc.

## Tendencias

!!! quote "La ley de Moore no nos garantiza performance"

![[Sistemas Distribuidos I/img/Pasted image 20250312155121.png]]

!!! quote "Internet como medio de integración indiscutido"

!!! quote "Las PCs ya no conducen el movimiento"

![[Sistemas Distribuidos I/img/Pasted image 20250312155204.png]]

---

## ¿Qué es un Sistema Distribuido?


!!! quote "Colección de computadoras independientes que el usuario ve como un solo sistema coherente."

!!! quote "Es un sistema de computadoras interconectadas por una red que se comunican y coordinan sus acciones intercambiando mensajes."

!!! quote "Aquel en el que el fallo de un computador que ni siquiera sabes que existe, puede dejar tu propio computador inutilizable."

### Desglose de las definiciones
- Multiprogramación: Colección de computadoras. Variantes de multiprogramación:

![[Sistemas Distribuidos I/img/Pasted image 20250313085551.png]]

- Independientes -> Autónomos.
- Un solo sistema -> El usuario no conoce su distribución.
- Interconectadas por una red -> Sistemas aislados no son distribuidos.
- Comunican y coordinan acciones -> Colaborativos.
- Intercambiando mensajes -> Protocolo de comunicación.
- Fallo de un computador -> Nuevos problemas no determinísticos. Hay que cosas que fallan que no vamos a poder intuir de forma determinística(hasta ahora, si me apagan la PC, el sistema no anda. A partir de ahora, el programa no deja de ejecutarse porque está corriendo en muchas otras PCs. Hay muchos procesos en juego(¿qué pasa si un proceso muere?))


---
## Pensamiento Distribuido

!!! quote "Ley de Conway"
> “Cualquier organización que diseñe un sistema, inevitablemente producirá un diseño cuya estructura será una copia de la estructura de comunicación de la organización”.

- Diseñamos de acuerdo a lo que conocemos y estamos acostumbrados a hacer en el día a día. -> No es necesariamente negativo: El hombre en su trabajo tiende a encontrar soluciones distribuidas y paralelas eficientes(minimizan costo, energía, tiempo, etc.).


---
### Parámetros de Diseño
- Transparencia
- Acceso a recursos compartidos
- Sistemas distribuidos abiertos(interfaces, interoperability, potability)
- Escalabilidad
- Tolerancia a fallos(scalability, reliability, safety, maintainability)


### Modelos para su análisis
- **Modelo de estados**(Interleaved model): Quiero ver estados de los procesos en cierto punto y en ciertas condiciones. VEAMOS COMO ESTA EL SISTEMA AHORA.

![[Sistemas Distribuidos I/img/Pasted image 20250313085725.png]]

- **Modelo de eventos**(Happened before): Cómo se comunican los procesos. Si algo pasa antes que otra cosa, posiblemente sea la causa.

![[Sistemas Distribuidos I/img/Pasted image 20250313085803.png]]


---
## Topologías de Comunicación

![[Sistemas Distribuidos I/img/Pasted image 20250313085939.png]]

## Centralizados VS Distribuidos
- **Centralizar** implica la concentración de la autoridad en los niveles más altos de una jerarquía.
- **Descentralizar** implica transferir la toma de decisiones a eslabones inferiores de cierta organización -> **Distribuir** implica utilizar un modelo descentralizado de control de computadoras para la coordinación de actividades con una coherencia alta. Queremos que las máquinas tengan nivel de decisión, pero que se mantenga una coherencia(marcos, normas, límites y órdenes).

| Sistemas Centralizados                                                   | Sistemas Distribuidos                                               |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------- |
| Sin conexiones. Sistemas de tiempo compartido. "Terminales de conexión". | Componentes conectados.                                             |
| Sin trabajo colaborativo.                                                | Realizando trabajo colaborativo.                                    |
| Sin un objetivo común.                                                   | Buscando un objetivo común.                                         |
| Muy difíciles de escalar(CPUs, Memoria, HD).                             | Escalan distribuyendo trabajo y recursos(Nodos, Regiones, Canales). |
### Ventajas de Centralizar
- **Control**: Lógica de control muy simple, efectiva, y en ocasiones eficiente.
- **Homogeneidad**: La centralización incita a definir estándares para software y hardware.
- **Consistencia**: Es posible definir fuertes políticas de consistencia de información y monitoreo del estado global del sistema.
- **Seguridad**: Se disminuye la "superficie de ataque" frente a amenazas.

### Ventajas de Distribuir
- **Disponibilidad**: Aún frente a fallos aislados, el sistema general puede prestar servicios.
- **Escalabilidad**: Mejores alternativas de adaptarse a nuevas escalas.
- **Reducción de Latencia**: Al favorecer principio de localidad de recursos.
- **Colaboración**: Permite interacciones entre sistemas de forma orgánica y natural.
- **Movilidad**: No están circunscriptos al alcance de un único computador.
- **Costo**: Componentes más simples. Subsistemas delegados en servicios terceros.

