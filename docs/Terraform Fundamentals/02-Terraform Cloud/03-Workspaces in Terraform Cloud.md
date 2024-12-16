> [!IMPORTANT] Workspaces
> Collection of infrastructure.
> When run locally, Terraform manages each collection of infrastructure with a persistent working directory, which contains a configuration, state data, and variables.
> Terraform Cloud manages infrastructure collections with workspaces instead of directories.

![](Terraform%20Fundamentals/img/Pasted%20image%2020240927102638.png)


> [!IMPORTANT] State Versions
> Each workspace retains backups of its previous state files.


> [!IMPORTANT] Run History
> When Terraform Cloud manages a workspace's Terraform runs, it retains a record of all run activity, including summaries, logs, a reference to the changes that caused the run, and user comments.

## After creating a Workspace
- It presents a dialog with links to either queue a plan or edit variables.
- It registers a webhook with your VCS if you have connected a VCS repository to a workspace.
- Most common things to do after creating a workspace:
	- Edit variables.
	- Edit additional workspace settings.
	- Work with runs.

## Ways to Use Variables
1. Terraform Variables: Terraform Cloud passes variables to Terraform by writing a `terraform.tfvars` file and passing the `-var-file=terraform.tfvars` options to the Terraform command.
2. Environment Variables: Terraform Cloud performs Terraform runs on disposable Linux worker VMs. Before running Terraform, Terraform Cloud populates the shell with environment variables using the `export` command.
3. Special Environment Variables: Terraform Cloud uses theses to control dangerous or rarely used run behaviors. If `TFE_PARALLELISM` is present, Terraform Cloud uses this to set `terraform plan` and `terraform apply`'s `-parallelism=<N>` flag.