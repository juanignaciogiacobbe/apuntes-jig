# Resource Behavior

## Accessing Resource Attributes
- Expressions within Terraform modules.
- Read-only attributes with information obtained from remote APIs.
- Provider-included data sources.

## Resource Dependencies
- Most resource dependencies are handled automatically.
- Terraform analyzes any expressions within a resource block to find references to other objects, and treats those references as ordering requirements when creating, updating, or destroying resources.
- It's usually not necessary to manually specify dependencies between resources, however some dependencies cannot be recognized implicitly in the configuration.

## Local-only Resources
- Specialized resource types that operate only within Terraform itself, calculating some results and saving those results in the state for future use.
- Examples:
	- ssh-keys
	- self-signed certs
	- random ids