> [!IMPORTANT] Arquitectura de Software
> Estructura o las estructuras de un sistema, que consta de componentes de software, las propiedades visibles externamente y las relaciones entre ellas.
> "Son aquellas decisiones que son importantes y difíciles de cambiar".


> [!IMPORTANT] Decisiones de Arquitectura
> Decisiones de Diseño que abordan requisitos significativos desde el punto de vista arquitectónico.
> Se perciben como difíciles de hacer y/o costosos de cambiar.
> Estas decisiones son importantes de guardarlas y conocerlas. Conocer el motivo por el cual se tomó dicha decisión en la arquitectura o diseño.

# Modelo de Vistas 4+1


> [!WARNING] ¿Qué permite este modelo?

- A través de diferentes vistas permite analizar distintas perspectivas del problema, focalizándose en el problema en cuestión.
- Concentra en un único documento las principales decisiones tomadas sobre el sistema.
- Permite a nuevos integrantes del equipo entender la arquitectura del sistema y ubicarse dentro de la solución.
- Permite discutir con todos los stakeholders las distintas decisiones y validarlas en una etapa temprana. -> Mejora la comunicación entre estos.
- Asegurar que la arquitectura cumpla con atributos clave de calidad.
- Facilita la adaptación a cambios y valida los requisitos funcionales.
- Gestiona la complejidad del sistema dividiendo la arquitectura en aspectos específicos.

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020240925163648.png)


> [!IMPORTANT] Vista Lógica
> Apoya principalmente los requisitos funcionales. -> Lo que el sistema debe brindar en términos de servicios a los usuarios.
> - El sistema se descompone en abstracciones clave, en forma de objetos o clases a partir del dominio del problema. -> Se aplican los principios de abstracción, encapsulamiento y herencia.
> - Se busca identificar mecanismos y elementos de diseño comunes a diversas partes del sistema.

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241210131509.png)



> [!IMPORTANT] Vista de Procesos
> Toma en cuenta algunos requisitos no funcionales como el rendimiento y la disponibilidad.
> - Contempla también asuntos de concurrencia y distribución, integridad del sistema, y de la tolerancia a fallas.
> - Especifica en qué hilo de control se ejecuta una operación de una clase definida en la vista lógica.

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241210131619.png)


> [!IMPORTANT] Vista de Desarrollo(o Componentes)
> Se centra en la organización real de los módulos de software en el ambiente del desarrollo de software.
> - Tiene en cuenta los requisitos internos relativos a la facilidad de desarrollo, administración del software, reutilización y elementos comunes, y restricciones impuestas por las herramientas o el lenguaje de programación que se use.

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241210131641.png)



> [!IMPORTANT] Vista Física(o de Despliegue)
> Toma en cuenta primeramente los requisitos no funcionales del sistema tales como la disponibilidad, confiabilidad, rendimento y escalabilidad.
> Detalla cómo los componentes del sistema se distribuyen en servidores, dispositivos y otras infraestructuras físicas.
> - Toma los requisitos no funcionales como la disponibilidad, confiabilidad, performance y escalabilidad.
> - El software se ejecuta sobre una red de computadoras o nodos de procesamiento. Los nodos se relacionan con elementos identificados en las vistas anteriores.

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241210131842.png)


> [!IMPORTANT] Vista de Escenario
> Los escenarios son de alguna manera una abstracción de los requisitos más importantes. Son instancias de casos de uso más generales.
> - Sirven como una guía para descubrir elementos arquitectónicos durante el diseño de arquitectura.
> - Sirven como un rol de validación e ilustración después de completar el diseño de arquitectura, en el papel y como punto de partido de las pruebas de un prototipo de la arquitectura.

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241210131930.png)


