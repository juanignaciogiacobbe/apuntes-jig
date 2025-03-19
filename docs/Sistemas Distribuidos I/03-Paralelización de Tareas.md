# Paralelización de Tareas

## Objetivos
- Reducir el tiempo de cómputo de una tarea(latencia). -> Aprovechar los recursos físicos.
- Incrementar la cantidad de tareas que se pueden realizar en paralelo(throughput).
- Reducir la potencia consumida al realizar todas las tareas.


!!! note "Camino Crítico"
> Máxima longitud de tareas secuenciales a computar -> Define el mejor rendimiento que se puede obtener al realizar un conjunto de tareas.

- No todas las tareas las puedo hacer al mismo tiempo. En esa dependencia tengo un conjunto de tareas que tienen mas cantidad de tareas(camino crítico).

---
## Ley de Amdahl


!!! quote "Ley de Amdahl"
> "The effort expended on achieving high parallel processing rates is wasted unless it is accompanied by achievements in sequential processing rates of very nearly the same magnitude".

- $T_P = W_{ser} + W_{par} / P$ con P unidades de cómputo($T_P$ es el tiempo de ejecución).

![[Sistemas Distribuidos I/img/Pasted image 20250319082008.png]]

- Todo trabajo de cómputo se divide en fracciones Secuenciales y Paralelas.
	- $T = W_{ser} + W_{par}$
- Si tengo un solo proceso hago la parte serial primero. 
- La parte paralelizable la hago en varios procesadores. Lo máximo que puedo tardar es con un solo procesador.
### Speedup
- **Speedup**: Ratio de optimización de una operación.
	- $S_P = T_1 / T_P$
		- Reemplazando, se obtiene que:
			- $S_P \leq 1/(f + (1-f)/P)$, pero con $P \rightarrow \infty$ se obtiene que $S_{\infty} \leq 1/f$ 

![[Sistemas Distribuidos I/img/Pasted image 20250319082924.png]]

- El Speedup máximo se encuentra acotado por la fracción de tiempo que no puede ser paralelizable.
- La fracción paralelizable está distribuida de forma uniforme entre procesadores.

![[Sistemas Distribuidos I/img/Pasted image 20250319083051.png]]


#### Ejemplo: Persona yendo a la facultad

![[Sistemas Distribuidos I/img/Pasted image 20250318200442.png]]

- La primera mejora(tomo un colectivo en el último tramo) es buenísima.
- **A medida que se mejora el ultimo tramo, más pesa la parte serializable**.
- Todo trabajo que hagas, está despediciado si tenés una parte serial(porque esta no se puede mejorar).
- No siempre agregando más recursos se mejora la solución.
---

## Ley de Gustafson


!!! quote "Ley de Gustafson"
> "Speedup should be measured by scaling the problem to the number of processors, not by fixing the problem size".

- Aumentar el paralelismo puede permitir la modificación del problema original para ejecutar más trabajo. Si nos concentramos en el paralelismo, al tener más computadoras no debería pensar en un solo problema.
- Si el problema crece, caben dos alternativas:
	- Parte serial disminuye -> El Speedup aumenta.
	- Paralelismo aumenta -> Speedup aumenta.

![[Sistemas Distribuidos I/img/Pasted image 20250319083318.png]]

- Esta ley es demasiado genérica(para mal)
	- Si queremos describir un problema que haga cómputo útil -> Tengo dependencias, no puedo hacer cualquier cosa en cualquier momento.
---

## Modelo Work-Span
- Modelo más cercano a la realidad para estimar optimizaciones que el usado por Amdahl.
- Provee una cota inferior y una cota superior para el Speedup.

### Hipótesis
- Paralelismo Imperfecto: No todo el trabajo paralelizable se puede ejecutar al mismo tiempo.
- Greedy Scheduling: Proceso disponible -> Tarea ejecutada.
- Tiempo de acceso a memoria despreciable.
- Tiempo de comunicación entre procesos despreciable.

### Definiciones
- $T_1(work)$: Tiempo en ejecutar operación/algoritmo con 1 solo proceso.
- $T_{\infty}(span)$: Tiempo en ejecutar el camino crítico de la operación/algoritmo.


| Cota     | Speedup                             | Consideraciones                                                          |
| -------- | ----------------------------------- | ------------------------------------------------------------------------ |
| Superior | $min(P, T_1/T_{\infty})$            | Se obtiene P en escenarios de Speedup lineal.                            |
| Inferior | $(T_1 - T_{\infty})/P + T_{\infty}$ | El trabajo se puede dividir en perfecta e imperfectamente paralelizable. |

![[Sistemas Distribuidos I/img/Pasted image 20250319083930.png]]
![[Sistemas Distribuidos I/img/Pasted image 20250319083949.png]]

- En general Amdahl crece, y Work-Span se plancha en cierto punto. 

---

## Estrategias de Paralelización

### Descomposición Funcional
- $foo(data) = f(data) + g(data) + h(data)$ -> 1 proceso máximo.
- $foo(data) = go f(data) + go g(data) + go h(data)$ -> 3 procesos máximos.

### Particionamiento de Datos
- $foo(data) = f(data)$ -> 1 proceso máximo.
- $foo(data) = go f(data) + go g(data) + go h(data)$ -> 3 procesos máximos.


---

## Patrones de Procesamiento
- Basados en algoritmos
	- No tan abstractos como patrones de diseño.
	- No incluyen detalles de implementación.
	- Agnósticos a lenguajes de programación.
- Patrones deben poder incluid otros patrones(nesting).
- Herramientas básicas de trabajo también en multi-computing.
![[Sistemas Distribuidos I/img/Pasted image 20250319085640.png]]

![[Sistemas Distribuidos I/img/Pasted image 20250319085652.png]]