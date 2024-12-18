# Principios S.O.L.I.D.

!!! note "Single Responsibility Principle"
> There should never be more than one reason for a class to change.
> - In this context, we define a responsibility to be “a reason for change.”
> - If a class has more then one responsibility, then the responsibilities become coupled.

![](Pasted%20image%2020240925152028.png)


!!! note "Open-Closed Principle"
> **Software entities should be open for extension, but closed for modification.**
> - When a single change to a program results in a cascade of changes to dependent modules, that program exhibits the undesirable attributes that we have come to associate with “bad” design.
> - This principle says that you should design modules that never change. 
> - It requires a dedication on the part of the designer to apply abstraction to those parts of the program that the designer feels are going to be subject to change.


!!! warning "OCP Heuristics"
> 1. Make all member variables private.
> 2. No Global Variables.
> 3. Runtime type identification is dangerous.

![](Pasted%20image%2020240925152349.png)



!!! note "Liskov Substitution Principle(LSP)"
> Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it.
> It is only when derived types are completely substitutable for their base types that functions which use those base types can be reused with impunity, and the derived types can be changed with impunity.


!!! note "Interface Segregation Principle(ISP)"
> A client should not be forced to depend on interfaces it does no use. This principle aims to prevent "fat" interfaces, which are interfaces that define methods that some implementing classes may not need.
> 1. Cohesive Interfaces: Interfaces should contain only methods that are logically related and necessary for the specific functionality.
> 2. Avoiding Unused Methods.
> 3. Modularity: ISP promoted modularity by encouraging the use of smaller more focused interfaces.


!!! note "Dependency Inversion Principle"
> High-level modules should not depend on low-level modules; both should depend on abstractions.
> Abstractions should not depend on details; details should depend on abstractions.
> The key goal is to reduce the coupling between different parts of the code, making it more flexible, maintainable, and easier to extend.
> By using abstractions, the code can avoid tight dependencies on specific implementations, allowing it to evolve more smoothly.
