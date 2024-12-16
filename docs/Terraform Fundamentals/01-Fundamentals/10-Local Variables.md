
> [!NOTE] Local Variables
> Are like a Function's Temporary Local Variables.
> Allows you to assign a name to an expression, and to use the variable multiple times within a module without repeating it.


![](../img/Pasted%20image%2020240925111329.png)

- A set of related `local` values can be declared together in a single block.
- The `expressions` are not limited to literal constants; they can reference other values in the module.
- When a local value is declared, you can reference it in expressions as `local.<name>`.
- Local values can only be accessed in expressions within the module where they were declared.