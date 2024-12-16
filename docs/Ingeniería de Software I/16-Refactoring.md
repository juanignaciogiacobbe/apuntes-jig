> [!IMPORTANT] Refactoring
> Es una técnica para reestructurar un cuerpo existente de tu código, alterando su estructura interna sin cambiar su comportamiento exterior.


> [!WARNING] Como realizar un refactoring efectivo?
> Utilizar tests unitarios para garantizar que el comportamiento exterior no ha cambiado.
> Aplicando los refactoring propuestos.

## Refactoring Flow
1. Asegurarse de que todos los tests pasan.
2. Encontrar **code smells**.
3. Encontrar un posible refactor.
4. Aplicar el refactor.


> [!WARNING] Code Smells
## Ejemplos de Code Smells
- Código duplicado.
- Métodos/funciones muy largos.
- Clases muy largas.
- Listas de parámetros muy largas.
- Cambios divergentes.
- Shotgun Surgery.
- Feature envy.
- Data clumps.
- Primitive Obsession.
- Switch Statements.
- Lazy class. -> Clases anemicas.
- Cadenas de mensajes.