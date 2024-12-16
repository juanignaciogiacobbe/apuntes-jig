> [!IMPORTANT] Workspaces
> Separate instances of state data that can be used from the same working directory.
> Allows you to use the same working copy of your configuration as well as the same plugin and module caches, while still keeping separate states for each collection of resources you manage.
> Are separte instances of state data that can be used from the same working directory. You can use workspaces to manage multiple non-overlapping groups of resources with the same configuration.


> [!WARNING] Things to know
> 1. Every initialized working directory has at least one Workspace.
> 2. For a given working directory, only one workspace can be selected at a time.
> 3. Most Terraform commands only interact with the currently selected workspaces.
> 4. Use the `terraform workspace select` command to change the currently selected workspace.
> 5. Use the `terraform workspace list`, `terraform workspace new`, and `terraform workspace delete` commands to manage the available workspaces in the current working directory.

![](../img/Pasted%20image%2020240926100114.png)
![](../img/Pasted%20image%2020240926100042.png)