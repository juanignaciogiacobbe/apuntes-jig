
!!! note "Exclusión Mutua: Algoritmo Centralizado"
> 1. Un proceso es elegido como coordinador.
> 2. Cuando un proceso quiere entrar a su sección crítica, envía un mensaje al coordinador.
> 3. Si no hay ningún proceso en la sección crítica, el coordinador envía OK, y si hay algún proceso en esa sección, el coordinador no envía respuesta hasta que se libere la sección crítica.


!!! note "Exclusión Mutua: Algoritmo Distribuido"
> Construye un mensaje con el nombre de la sección crítica, el número de proceso y timestamp. Al recibir el mensaje:
> 1. Si no está en la sección crítica y no quiere entrar, envía OK.
> 2. Si está en la sección crítica, no responde y encola el mensaje. Al salir de la sección crítica, envía OK.
> 3. Si quiere entrar en la sección crítica, compara el timestamp y gana el menor.


!!! note "Exclusión Mutua: Algoritmo Token Ring"
> - Se conforma un anillo mediante conexiones punto a punto.
> - Al inicializar, el proceso 0 recibe un token que va circulando por el anillo.
> - Sólo el proceso que tiene el token puede entrar a la sección crítica.
> - Cuando el proceso sale de la sección crítica, continua circulando el token.
> - El proceso no puede entrar a otra sección crítica con el mismo token.

