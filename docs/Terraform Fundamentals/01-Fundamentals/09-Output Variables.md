
> [!NOTE] Output Variables
> Are like return values.
> A child module can use them to expose a subset of resource attributes to the parent module.
> A root module can use them to print values in the CLI.
> Root module outputs can be accessed by other configurations via the `terraform_remote_state` data source.


## Declaring an Output Variable

![](../img/Pasted%20image%2020240925110423.png)

- The `name` label after the `output` keyword must be a valid identifier.
- The `value` argument takes an expression whose result will be returned to the user.
- When accessing child module outputs in a parent module, the outputs of the child modules are available in expressions as `module.<module_name>.<output_name>`.

![](../img/Pasted%20image%2020240925110724.png)

- The `description` should clearly explain the purpose of the `output` and what kind of `value` is expected.
- The `depends_on` argument should be used as a last resort. You should always include a comment explaining why it is being used.

![](../img/Pasted%20image%2020240925111125.png)