
> [!IMPORTANT] Backend Configuration
> Each Terraform configuration can specify a backend.

## Where they come from
- Terraform includes a built-in selection of backends, and these are the only backends. You cannot load additional backends as plugins.

## Where they are used
- Backend configuration is only used by [Terraform CLI](02-Terraform%20CLI.md). Terraform Cloud Enterprise always use their own state storage.

## What they do
- Two areas of Terraform's behavior are determined by the backend:
	- Where state is stored.
	- Where operations are performed.


> [!IMPORTANT] Backend Block Limitations
> A configuration can only provide one backend block.
> A backend block cannot refer to named values.



> [!WARNING] Three things to know
> 1. When the backend changes in a configuration, you must run `terraform init`.
> 2. When the backend changes, Terraform gives you the option to migrate your state.
> 3. HashiCorp recommends you manually backup your state. Simply copy the `terraform.tfstate` file.

