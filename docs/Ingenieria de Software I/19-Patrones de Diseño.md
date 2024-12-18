# Patrones de Diseño
- [Refactoring Guru](https://refactoring.guru/es/design-patterns/catalog)

!!! note "Patron Strategy"
> Es un patron de comportamiento que permite definir una familia de algoritmos, colocar cada uno de ellos en una clase separada y hacer sus objetos intercambiables.
> - Se toma una clase que hace algo especifico de muchas formas diferentes, y se extraen todos esos algoritmos para colocarlos en clases separadas llamadas *estrategias*.
> - La clase original, llamada *contexto*, debe tener un campo para almacenar una referencia a una de las estrategias. El contexto delega el trabajo a un objeto de estrategia vinculado en lugar de ejecutarlo por su cuenta.
> - La clase contexto no es responsable de seleccionar un algoritmo adecuado para la tarea. En lugar de eso, el cliente pasa la estrategia deseada a la clase contexto. -> Funciona con todas las estrategias a través de la misma interfaz genérica, que sólo expone un único método para disparar el algoritmo encapsulado dentro de la estrategia seleccionada.
> - El contexto se vuelve independiente de las estrategias concretas, así que puedes añadir nuevos algoritmos o modificar los existentes sin cambiar el código de la clase contexto o de otras estrategias.


![](Pasted%20image%2020241127181817.png)


!!! warning "Ventajas"
- Los algoritmos usados se cambian en tiempo de ejecución.
- Se pueden aislar los detalles de implementación de un algoritmo del código que lo utiliza.
- Se sustituye la herencia por composición.
- Open Closed Principle: Se pueden introducir nuevas estrategias sin tener que cambiar el contexto.


!!! warning "Desventajas"
- Si se tiene un par de algoritmos que raramente cambian, no hay razón real para complicar el programa en exceso con nuevas clases e interfaces de este patrón.
- Los clientes deben conocer las diferencias entre estrategias para poder seleccionar la adecuada.
- Muchos lenguajes de programación modernos tienen un soporte de tipo funcional que permiten implementar distintas versiones de un algoritmo dentro de un grupo de funciones anónimas. ->Se pueden utilizar estas funciones exactamente como se habrían utilizado los objetos de estrategia, pero sin saturar el código con clases e interfaces adicionales.
---


!!! note "Template Method"
> Es un patrón de comportamiento que define el esqueleto de un algoritmo en la superclase pero permite que las subclases sobrescriban pasos del algoritmo sin cambiar su estructura.
> - Se divide un algoritmo en una serie de pasos, se convierten estos pasos en métodos y se colocan una serie de llamadas a esos métodos dentro de un único _método plantilla_. Los pasos pueden ser `abstractos`, o contar con una implementación por defecto. Para utilizar el algoritmo, el cliente debe aportar su propia subclase, implementar todos los pasos abstractos y sobrescribir algunos de los opcionales si es necesario (pero no el propio método plantilla).
> - Hay dos tipos de pasos:
> 	- Los _pasos abstractos_ deben ser implementados por todas las subclases
> 	- Los _pasos opcionales_ ya tienen cierta implementación por defecto, pero aún así pueden sobrescribirse si es necesario

![](Pasted%20image%2020241210160024.png)


!!! warning "Ventajas"
- Se puede permitir a los clientes que sobrescriban tan solo ciertas partes de un algoritmo grande, para que les afecten menos los cambios que tienen lugar en otras partes del algoritmo.
- Se puede colocar el código duplicado dentro de una superclase.


!!! warning "Desventajas"
- Algunos clientes pueden verse limitados por el esqueleto proporcionado de un algoritmo.
- Se puede llegar a violar el Liskov Sustitution Principle suprimiendo una implementación por defecto de un paso a través de una subclase.
- Los template methods tienden a ser más difíciles de mantener cuantos más pasos tengan.


!!! warning "Template Method VS Strategy"
> - Template Method se basa en la herencia: Permite alterar partes de un algoritmo extendiendo esas partes en subclases. -> Trabaja al nivel de la clase, por lo que es estático. 
> - Strategy se basa en la composición: Se pueden alterar partes del comportamiento del objeto suministrándole distintas estrategias que se correspondan con ese comportamiento. -> _Strategy_ trabaja al nivel del objeto, permitiéndote cambiar los comportamientos durante el tiempo de ejecución.

---


!!! note "Abstract Factory"
> Es un patrón creacional que nos permite producir familias de objetos relacionados sin especificar sus clases concretas.
> - El código cliente tiene que funcionar con fábricas y productos a través de sus respectivas interfaces abstractas. Esto nos permite cambiar el tipo de fábrica que pasamos al código cliente, así como la variante del producto que recibe el código cliente, sin descomponer el propio código cliente.

![](Pasted%20image%2020241209094001.png)


!!! warning "Ventajas"
- Se puede tener la certeza de que los productos que obtienes de una fábrica son compatibles entre sí.
- Se evita un acoplamiento fuerte entre productos concretos y el código cliente.
- _Principio de responsabilidad única_: Puedes mover el código de creación de productos a un solo lugar, haciendo que el código sea más fácil de mantener.
- _Principio de abierto/cerrado_: Puedes introducir nuevas variantes de productos sin descomponer el código cliente existente.


!!! warning "Desventajas"
- Puede ser que el código se complique más de lo que debería, ya que se introducen muchas nuevas interfaces y clases junto al patrón.
---


!!! note "Factory Method"
> Es un patron creacional que proporciona una interfaz para crear objetos en una superclase, mientras que permite a las subclases alterar el tipo de objetos que se crearan.
> - En lugar de llamar al operador `new` para construir objetos directamente, se invoque a un método *fabrica* especial. Los objetos se siguen creando a través del operador `new`, pero se invocan desde el método fabrica. Los objetos devueltos por el método fabrica a menudo se denominan *productos*.
> - Busca abstraer el proceso de creación de diferentes tipos de objeto.
> - El foco es qué objeto crear.

![](Pasted%20image%2020241127182244.png)


!!! note "Builder"
> Es un patrón creacional que nos permite construir objetos complejos paso a paso. Nos permite producir distintos tipos y representaciones de un objeto empleando el mismo código de construcción.
> - Se saca el código de construcción del objeto de su propia clase y se coloca dentro de objetos independientes llamados *constructores*.
> - Para crear un objeto, se ejecuta una serie de estos pasos en un objeto constructor. -> No necesitas invocar todos los pasos. Puedes invocar sólo aquellos que sean necesarios para producir una configuración particular de un objeto.
> - Busca resolver múltiples opciones y parámetros opcionales. -> El foco es cómo crear el objeto de forma flexible y paso a paso.

![](Pasted%20image%2020241201095637.png)


!!! warning "Builder VS Setters"
> - Usando Setters, hasta no asignar todos los parámetros, el objeto queda en un estado inconsistente -> Genera problemas en ambientes multithread.


!!! warning "Builder VS Factory"
> - Factory busca abstraer el proceso de creación de diferentes tipos de objeto -> El foco es qué objeto crear.
> - Builder busca resolver múltiples opciones y parámetros opcionales -> El foco es cómo crear el objeto de forma flexible y paso a paso.


!!! note "Decorator"
> Es un patrón estructural que permite añadir funcionalidades a objetos colocando estos objectos dentro de otros objetos encapsuladores especiales que contienen estas funcionalidades.
> - Un _wrapper_ es un objeto que puede vincularse con un objeto _objetivo_. El wrapper contiene el mismo grupo de métodos que el objetivo y le delega todas las solicitudes que recibe. No obstante, el wrapper puede alterar el resultado haciendo algo antes o después de pasar la solicitud al objetivo.

![](Pasted%20image%2020241209094758.png)


!!! warning "Decorator VS Herencia"
> - La herencia es estática. No se puede alterar la funcionalidad de un objeto existente durante el tiempo de ejecución. Sólo se puede sustituir el objeto completo por otro creado a partir de una subclase diferente.
> - Las subclases sólo pueden tener una clase padre. En la mayoría de lenguajes, la herencia no permite a una clase heredar comportamientos de varias clases al mismo tiempo.



!!! note "Singleton"
> Es un patrón creacional que nos permite asegurarnos de que una clase tenga una única instancia, a la vez que proporciona un punto de acceso global a dicha instancia.
> - Al igual que una variable global, el patrón Singleton nos permite acceder a un objeto desde cualquier parte del programa. No obstante, también evita que otro código sobreescriba esa instancia. -> Vulnera el Single Responsibility Principle.

![](Pasted%20image%2020241209095336.png)


!!! note "Command"
> Es un patrón de comportamiento que convierte una solicitud en un objeto independiente que contiene toda la información sobre la solicitud -> Permite parametrizar los métodos con diferentes solicitudes, retrasar o poner en cola la ejecución de una solicitud y soportar operaciones que no se pueden realizar.

![](Pasted%20image%2020241209095947.png)



!!! note "State"
> Es un patrón de comportamiento que permite a un objeto alterar su comportamiento cuando su estado interno cambia. -> Está estrechamente relacionado con la *Máquina de Estados Finitos*.
> - En cualquier momento dado, un programa puede encontrarse en un número _finito_ de _estados_. Dentro de cada estado único, el programa se comporta de forma diferente y puede cambiar de un estado a otro instantáneamente. Sin embargo, dependiendo de un estado actual, el programa puede cambiar o no a otros estados. Estas normas de cambio llamadas _transiciones_ también son finitas y predeterminadas.


!!! warning "State VS Strategy"
> En el patrón State, los estados particulares pueden conocerse entre sí e iniciar transiciones de un estado a otro, mientras que las estrategias casi nunca se conocen.
> - Strategy se enfoca en intercambiar diferentes algoritmos o métodos que logran el mismo objetivo.
> - State gestiona diferentes comportamientos según el estado actual del objeto.

![](Pasted%20image%2020241209101232.png)