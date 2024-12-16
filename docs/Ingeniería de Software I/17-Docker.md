
> [!IMPORTANT] Máquinas Virtuales
> Emulan una máquina real -> Proveen aislamiento total, y tienen una única opción de ejecutar programas de otras arquitecturas de hardware.


> [!IMPORTANT] Infrastructure as Code
> - En lugar de realizar modificaciones manualmente, se usa un lenguaje de programación específico para el dominio de configuraciones de máquinas.
> - Ejemplo: [Terraform](Terraform%20Fundamentals/01-Fundamentals/01-What%20is%20Terraform.md).
> - Suelen ser declarativas(qué objetivo lograr) e imperativas(cómo lograr dicho objetivo)-> Nos abstraemos del estado actual.



> [!IMPORTANT] Docker
> Es una herramienta que automatiza el despliegue de aplicaciones aisladas dentro de contenedores.


> [!WARNING] Algunos conceptos importantes
- **Container**: Grupo aislado de [procesos](Sistemas%20Operativos/Proceso.md).
- **Image**: Template usado para crear containers.
- **Dockerfile**: Archivo con instrucciones para construir una imagen.
- **Mounts**: Acceso a directorios del host.
- **Volumes**: Área donde se persisten los datos.
- **Networks**: Interfaces de red internas.
- **Ports**: Forwardear puertos del host a puertos del contenedor.

> [!WARNING] ¿Qué nos brinda Docker?
> 
- **Consistencia**: Cualquier imagen se obtiene, inicia y configura de la misma manera.
- **Replicabilidad**: Los contenedores basados en una misma imagen son inicialmente iguales.
- **Aislamiento**: Se puede controlar la interacción entre la aplicación en un contenedor y el mundo exterior(en ambas direcciones).

## Contenedores Livianos
El ecosistema Docker asume que los contenedores son livianos:
- Dedicados a un único propósito -> Ejecutan un comando, y no incluyen dependencias innecesarias.
- Mantienen el estado mínimo necesario.
- Pueden encenderse/apagarse rápidamente.

# Containers VS Virtual Machines

![](Ingeniería%20de%20Software%20I/img/Pasted%20image%2020241126170440.png)


> [!IMPORTANT] Orquestadores
> Coordinan el uso de múltiples contenedores para implementar una única aplicación, brindando:
> - Configuración de contenedores heterogéneos.
> - Distribución.
> - Balanceo de Carga.
> - Tolerancia a fallos.
> Ejemplo: docker-compose y Kubernetes.

