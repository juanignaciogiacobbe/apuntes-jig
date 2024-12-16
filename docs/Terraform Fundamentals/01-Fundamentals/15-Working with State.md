> [!IMPORTANT] State
> Is a requirement for Terraform to function properly.
> Terraform requires some sort of database to map Terraform configuration to the real world.
> Terraform uses its own state structure to map configurations to resources.



> [!IMPORTANT] Metadata
> Terraform must track metadata like resources dependencies. To ensure operation, Terraform retains a copy of the most recent set of dependencies within the state.


> [!IMPORTANT] Performance
> Terraform stores a cache of attribute values for all resources in the state. This comes in handy with large configurations, so you don't have to query all the resources in the configuration.


> [!IMPORTANT] Syncing
> When working in a team, it is recommended to use remote state. It is important that, if working in a team, all members work with the same state. Remote state ensures the state is synced.



> [!IMPORTANT] Remote State
> Allows you to share output values with other configurations.
> Allows teams to share infrastructure resources in a read-only way.
> Can be a convenient, built-in mechanism for sharing data between configurations, but you may prefer to use more general stores to pass settings to other configurations and consumers.
