# Corrección
## Problema de la Sección Crítica
- En [[Sistemas Operativos/Proceso|procesos]], es suficiente con debuggear para encontrar errores, ya que ante una misma entrada se obtiene siempre la misma salida.
- En programas concurrentes, la salida puede depender del escenario que resultó en la ejecución.
- El problema de la sección crítica consiste en lo siguiente:
	- Cada proceso se ejecuta en un loop infinito cuyo código puede dividirse en parte crítica y parte no-crítica.
	- La sección crítica debe progresar(finalizar eventualmente).
	- La sección no-crítica no requiere progreso(el proceso puede terminar o entrar en un loop infinito).


!!! warning "Propiedades del tipo Safety"
> Deben ser verdaderas siempre.

- **Exclusion mutua**: Dos procesos no deben intercalar ciertas (sub)secuencias de instrucciones. Ejemplo: incremento de variables globales.
	- NO deben intercalarse instrucciones de la sección crítica.
- **Ausencia de Deadlocks**: Un sistema que aún no finalizó debe poder continuar realizando su tarea, es decir, avanzar productivamente.
	- Si dos procesos están tratando de entrar a la sección critica, eventualmente alguno de ellos debe tener éxito.


!!! warning "Propiedades del tipo Liveness"
> Deben volverse verdaderas eventualmente.

- **Ausencia de Starvation**: Todo proceso que esté listo para utilizar un recurso debe recibir dicho recurso eventualmente.
	- Si todo proceso trata de entrar a la sección critica, eventualmente debe tener éxito.
- **Fairness(equidad o justicia)**: Un escenario es (débilmente) fair, si en algún estado en el escenario, una instrucción que esta continuamente habilitada, eventualmente aparece en el escenario.