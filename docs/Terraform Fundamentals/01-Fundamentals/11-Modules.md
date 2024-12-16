
> [!IMPORTANT] Modules
> Are containers for multiple resources.
> A module can consist of a collection of `.tf` as well as `.tf.json` files kept together in a directory.

## Module Types
1. **Root Modules**: You need at least one root module.
2. **Child Modules**: Modules that are called by the root module.

![](../img/Pasted%20image%2020240926084847.png)
	- Child Modules can declare [output variables](09-Output%20Variables.md) to selectively export values which are accessible by the calling module.
	![](../img/Pasted%20image%2020240926085716.png)
1. **Published Modules**: Modules loaded from a private or public registry.

## Module Argument Types
1. The source argument is required for all modules.
2. The version argument is recommended for modules from a registry.
3. The [input variable](08-Input%20Variables.md) arguments.
4. The [meta-arguments](05-Meta-Arguments.md) like `for_each` and `depends_on`.



> [!WARNING] Splitting code into Child Modules
> When you split code into other child modules, or when moving resource blocks between modules, you can cause Terraform to see the new location of the module block as an entirely different resource.
> Use the `terraform state mv` command to inform Terraform that the child module block has moved to a different module.

![](../img/Pasted%20image%2020240926090025.png)


> [!IMPORTANT] Tainting Resources within a Module
> The `taint` command can be used to taint specific resources within a module.
> It is not possible to taint an entire module. Instead, each resource within the module must be tainted separately.
