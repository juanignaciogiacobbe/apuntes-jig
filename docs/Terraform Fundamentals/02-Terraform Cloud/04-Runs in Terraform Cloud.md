> [!IMPORTANT] Navigating Runs
- Each Workspace has two ways to view runs:
	- A Runs Link, which brings you to a full list of runs.
	- A Current Run Link, which takes you to the most recent active run.
- The run page shows:
	- The current status of the run.
	- The code commit associated with the run.
	- How, when, and by whom the run was initiated.
	- A timeline of events related to the run.
	- The output from both `terraform plan` and `apply` commands.


> [!IMPORTANT] Destroy Mode
> Instructs Terraform to create a plan which destroys all objects, regardless of configuration changes.

- **CLI**: Use `terraform plan -destroy` or `terraform destroy`.
- **API**: Use the `is-destroy` option.
- **UI**: Use a workspace's "Destruction and Deletion" settings page.


> [!IMPORTANT] Refresh-Only Mode
> Instructs Terraform to create a plan which updates the Terraform state to match changes made to remote objects outside of Terraform.

- **CLI**: Use `terraform plan -refresh-only` or `terraform apply -refresh-only`.
- **API**: Use the `refresh-only` option.


> [!IMPORTANT] Skipping Automatic State Refresh
> The `-refresh=false` option is used in normal planning mode to skip the default behavior of the refreshing of the state before checking for configuration changes.

- **CLI**: Use `terraform plan -refresh=false` or `terraform apply -refresh=false`.
- **API**: Use the `refresh` option.


> [!IMPORTANT] Replacing Selected Resources
> The `replace` option instructs Terraform to replace the object with the given resource address.

- **CLI**: Use `terraform plan -replace=ADDRESS` or `terraform apply -replace=ADDRESS`-
- **API**: Use the `replace-adds` option.


> [!IMPORTANT] Target Plan and Apply
> Resource Targeting is intended for exceptional circumstances only and should not be used often.

- **CLI**: Use `terraform plan -target=ADDRESS` or `terraform apply -target=ADDRESS`.
- **API**: Use the `target-addrs` option. 


> [!WARNING] Limitations on Terraform Cloud features for remote plans created with targeting
> - Sentinel policy checks for targeted plans may cause a failure for any policy that requires a planned change to a resource instance elected by its address.
> - Cost Estimation is disabled for any run created with `-target` set to prevent producing a misleading underestimate of cost due to resource instances being excluded from the plan.

## Types of Run Workflows
1. UI/VCS-driven Runs: Every workspace is associated with a specific branch of a VCS repo of Terraform configurations.
2. API-driven Runs: Workspaces are not directly associated with a VCS repo, and runs are not driven by webhooks on your VCS provider.
3. CLI-driven Runs: Terraform Cloud runs [Terraform CLI](Terraform%20Fundamentals/01-Fundamentals/02-Terraform%20CLI.md) to provision infrastructure.

## Terraform Cloud's Run Environment

![](Terraform%20Fundamentals/img/Pasted%20image%2020240927110650.png)