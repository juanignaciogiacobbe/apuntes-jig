> [!NOTE] Input Variables
> Serve as parameters for a Terraform Module. They allow aspects of the module to be customized without altering the actual module.
> This allows modules to be shared between different configurations.
> They are like Function Arguments.


> [!WARNING] Using Variable Blocks
> The name of the variable can be any valid identifier except for `source, version, providers, count, for_each, lifecycle, depends_on` and `locals`. These are reserved for [Meta-Arguments](05-Meta-Arguments.md).

## Example

![](../img/Pasted%20image%2020240925104229.png)

## Arguments and Constraints

![](../img/Pasted%20image%2020240925104523.png)

## Using Input Variable Values

![](../img/Pasted%20image%2020240925104856.png)

## How to assign Values to Root Modules Variables
- In a Terraform Cloud workspace.
- Individually, with the `-var` command line option.
- In variable definition files like `.tfvrs` or `.tfvars.json`
- As environment variables.

![](../img/Pasted%20image%2020240925105118.png)

![](../img/Pasted%20image%2020240925105312.png)

![](../img/Pasted%20image%2020240925105346.png)

![](../img/Pasted%20image%2020240925105429.png)

## Precedence
- The order in which variables are loaded:
	1. Environment variables.
	2. `terraform.tfvars`
	3. `terraform.tfvars.json`
	4. `*.auto.tfvars` or `*.auto.tfvars.json`
	5. Any command-line options like `-var` and `-var-file`