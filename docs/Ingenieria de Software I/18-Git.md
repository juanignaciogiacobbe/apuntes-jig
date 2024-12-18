# Git

!!! note "Git"
> Sistema de control de versiones distribuido y descentralizado. Nos permite manejar versiones de un proyecto en secuencia y en paralelo.
> - Es distribuido porque ningún cliente está privilegiado sobre otros.


!!! note "Commit"
> - Algún estado del sistema -> Queremos referirnos a el para conservarlo para el futuro, y para compartirlo con el resto del equipo.
> - Contiene ancestros, autor, fecha de autoría, un mensaje y archivos.


!!! warning "Commits Atómicos"
> Un commit que aplica un cambio completo:
> - Una sola razón para todo lo que cambió.
> - No depende de cambios posteriores.
> - Facilita manejar commits(revertir, reordenar y buscar en la historia).
> - No hay relación entre el tamaño de un commit y su atomicidad.


!!! note "Conflicto"
> Al hacer `merge`, hay un conflicto cuando los cambios de cada rama interactúan de forma negativa.
> - Conflicto textual -> Mismas líneas(git puede detectarlo).
> - Conflicto semántico -> Misma lógica(requiere analizar la interacción).
> Deseamos que todos los conflictos sean **textuales**.


!!! note "Pull/Merge Requests"
> Nos da la oportunidad de verificar:
> - Calidad del código.
> - Calidad de la aplicación.
> - Cumplimiento de los requerimientos.
> - Si el cambio conviene.


!!! warning "Un buen PR..."
> - Es atómico -> Una sola razón para todo lo que cambió, y no depende de cambios externos.
> - Explica -> Razones que no resultan obvias del resumen, y efectos de los cambios que no resultan obvios al ver el código.

![](Pasted%20image%2020241127161616.png)

!!! note "Branches a largo plazo"
> Lo mejor es evitarlas:
> - Modularizar mejor: Separar variantes por archivo en lugar de por branch.
> - Feature Flag: Activar una u otra sección de código por configuración.
> - A veces representa el significado que queremos, pero debemos manejar cuidadosamente la divergencia.
> - Para reducir los problemas, podemos hacer `merge` intermedios:
> 	- Menos cambios en cada merge.
> 	- Esos cambios son más recientes.
> 	- Evitamos duplicar trabajo.

![](Pasted%20image%2020241127161928.png)


!!! note "Branches de Entorno"
> Son branches a largo plazo que:
> - Representa un entorno de despliegue.
> - Usa CI/CD para desplegar cambios.
> - Por ejemplo: `main`, `qa`, ...


!!! note "Continuous Integration(CI)"
> - Integrar frecuentemente el trabajo realizado.
> - Descubrir errores rápidamente de forma automática.


!!! note "Continuous Deployment(CD)"
> - Asegurar que podemos producir un entregable de forma rápida y certera.
> - Desplegar a entornos de prueba/producción de forma automática


---

!!! note "Historia"
> Cada commit tiene ancestros. Su contenido está relacionado al contenido de sus ancestros.
> Se tiene como requisito que no se generen ciclos.

![](Pasted%20image%2020241127160524.png)



# Organizaciones de la Historia


!!! note "Trunk-Based"
> - Todo cambio se agrega a un mismo branch.
> - Es simple, y todo el código está en el último commit(esto puede ser una desventaja).
> - Cuesta separar de líneas de trabajo.
> - El problema principal es que el control de versiones es naturalmente distribuido(pero también concurrente).

![](Pasted%20image%2020241127160752.png)


!!! note "Feature Branches"
> - Una branch por funcionalidad de código independiente. 
> - Usualmente, 1 funcionalidad de usuario ~ N features.

![](Pasted%20image%2020241127160917.png)


!!! warning "Ventajas"
> 
- Solo un feature incompleto por branch.
- Menos gente trabajando en cada branch.
- El resto del equipo ve todos los cambios juntos.

!!! warning "Desventajas"
- Administración de branches.
- Features necesitan ser independientes entre sí.


!!! note "Github Workflow"
> - Las verificaciones se hacen dentro de cada PR.
> - Software con despliegues simples, rápidos y baratos.

![](Pasted%20image%2020241127162704.png)


!!! note "Git Flow"
> - La verificación se hace al preparar cada release
> - Software con despliegues complejos, lentos y caros.

![](Pasted%20image%2020241127162844.png)

---

!!! note "Monorepo"
> Un repositorio para todo el proyecto:
> - Es simple.
> - Facilita hacer cambios coordinados a N componentes.
> - Fácil de filtrar para crear polirepo con historia equivalente.


!!! note "Polirepo"
> Un repositorio por componente del proyecto:
> - Control de acceso limitando autorización a ciertos repositorios.
> - Facilita modularizar componentes(Evita dependencias implícitas).
> - No hay forma fácil de unificar la historia para crear un monorepo equivalente.
