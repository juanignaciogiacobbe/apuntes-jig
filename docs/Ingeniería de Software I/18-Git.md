
> [!IMPORTANT] Git
> Sistema de control de versiones distribuido y descentralizado. Nos permite manejar versiones de un proyecto en secuencia y en paralelo.
> - Es distribuido porque ningún cliente está privilegiado sobre otros.


> [!IMPORTANT] Commit
> - Algún estado del sistema -> Queremos referirnos a el para conservarlo para el futuro, y para compartirlo con el resto del equipo.
> - Contiene ancestros, autor, fecha de autoría, un mensaje y archivos.


> [!WARNING] Commits Atómicos
> Un commit que aplica un cambio completo:
> - Una sola razón para todo lo que cambió.
> - No depende de cambios posteriores.
> - Facilita manejar commits(revertir, reordenar y buscar en la historia).
> - No hay relación entre el tamaño de un commit y su atomicidad.


> [!IMPORTANT] Conflicto
> Al hacer `merge`, hay un conflicto cuando los cambios de cada rama interactúan de forma negativa.
> - Conflicto textual -> Mismas líneas(git puede detectarlo).
> - Conflicto semántico -> Misma lógica(requiere analizar la interacción).
> Deseamos que todos los conflictos sean **textuales**.


> [!IMPORTANT] Pull/Merge Requests
> Nos da la oportunidad de verificar:
> - Calidad del código.
> - Calidad de la aplicación.
> - Cumplimiento de los requerimientos.
> - Si el cambio conviene.


> [!WARNING] Un buen PR...
> - Es atómico -> Una sola razón para todo lo que cambió, y no depende de cambios externos.
> - Explica -> Razones que no resultan obvias del resumen, y efectos de los cambios que no resultan obvios al ver el código.

![](Ingeniería%20de%20Software%20I/img/Pasted%20image%2020241127161616.png)

> [!IMPORTANT] Branches a largo plazo
> Lo mejor es evitarlas:
> - Modularizar mejor: Separar variantes por archivo en lugar de por branch.
> - Feature Flag: Activar una u otra sección de código por configuración.
> - A veces representa el significado que queremos, pero debemos manejar cuidadosamente la divergencia.
> - Para reducir los problemas, podemos hacer `merge` intermedios:
> 	- Menos cambios en cada merge.
> 	- Esos cambios son más recientes.
> 	- Evitamos duplicar trabajo.

![](Ingeniería%20de%20Software%20I/img/Pasted%20image%2020241127161928.png)


> [!IMPORTANT] Branches de Entorno
> Son branches a largo plazo que:
> - Representa un entorno de despliegue.
> - Usa CI/CD para desplegar cambios.
> - Por ejemplo: `main`, `qa`, ...


> [!IMPORTANT] Continuous Integration(CI)
> - Integrar frecuentemente el trabajo realizado.
> - Descubrir errores rápidamente de forma automática.


> [!IMPORTANT] Continuous Deployment(CD)
> - Asegurar que podemos producir un entregable de forma rápida y certera.
> - Desplegar a entornos de prueba/producción de forma automática


---

> [!IMPORTANT] Historia
> Cada commit tiene ancestros. Su contenido está relacionado al contenido de sus ancestros.
> Se tiene como requisito que no se generen ciclos.

![](Ingeniería%20de%20Software%20I/img/Pasted%20image%2020241127160524.png)



# Organizaciones de la Historia


> [!IMPORTANT] Trunk-Based
> - Todo cambio se agrega a un mismo branch.
> - Es simple, y todo el código está en el último commit(esto puede ser una desventaja).
> - Cuesta separar de líneas de trabajo.
> - El problema principal es que el control de versiones es naturalmente distribuido(pero también concurrente).

![](Ingeniería%20de%20Software%20I/img/Pasted%20image%2020241127160752.png)


> [!IMPORTANT] Feature Branches
> - Una branch por funcionalidad de código independiente. 
> - Usualmente, 1 funcionalidad de usuario ~ N features.

![](Ingeniería%20de%20Software%20I/img/Pasted%20image%2020241127160917.png)


> [!WARNING] Ventajas
> 
- Solo un feature incompleto por branch.
- Menos gente trabajando en cada branch.
- El resto del equipo ve todos los cambios juntos.

> [!WARNING] Desventajas
- Administración de branches.
- Features necesitan ser independientes entre sí.


> [!IMPORTANT] Github Workflow
> - Las verificaciones se hacen dentro de cada PR.
> - Software con despliegues simples, rápidos y baratos.

![](Ingeniería%20de%20Software%20I/img/Pasted%20image%2020241127162704.png)


> [!IMPORTANT] Git Flow
> - La verificación se hace al preparar cada release
> - Software con despliegues complejos, lentos y caros.

![](Ingeniería%20de%20Software%20I/img/Pasted%20image%2020241127162844.png)

---

> [!IMPORTANT] Monorepo
> Un repositorio para todo el proyecto:
> - Es simple.
> - Facilita hacer cambios coordinados a N componentes.
> - Fácil de filtrar para crear polirepo con historia equivalente.


> [!IMPORTANT] Polirepo
> Un repositorio por componente del proyecto:
> - Control de acceso limitando autorización a ciertos repositorios.
> - Facilita modularizar componentes(Evita dependencias implícitas).
> - No hay forma fácil de unificar la historia para crear un monorepo equivalente.
