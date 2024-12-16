
> [!IMPORTANT] Migrating Terraform State to Terraform Cloud
> It lets you continue managing that infrastructure without de-provisioning anything.


> [!NOTE] Terraform Cloud
> An application that helps teams use Terraform together. It manages Terraform runs in a consistent and reliable environment.


> [!WARNING] Steps to Migrate Local Terraform

1. You will need Terraform 0.11.13 or later on the workstation you are doing the migration on. Older versions will either not have the remote backend, or will only partially support it.
2. Gather credentials, Data, and Code. Make sure you have the following:
	- The location of the VCS repository for the Terraform config.
	- A local working copy of the Terraform config.
	- The existing state data.
	- A Terraform Cloud user account.
3. Stop Terraform runs: Let any current runs finish, then make sure there won't be more. This could involve locking or deleting CI jobs, restricting access to the state backend, or just communicating clearly with your team.
4. Prepare your Terraform Working Directory:
	- If you've already been doing Terraform runs in this directory, you should be good to go.
	- If you had to retrieve a `terraform.tfstate` file from elsewhere, copy it into the root of the working directory and run `terraform init`.
	- If you used a remote backend and had to check out a fresh working directory from version control, run `terraform init`.
5. Edit the Backend Config:
	![](Terraform%20Fundamentals/img/Pasted%20image%2020240927094459.png)
	- Use the remote backend.
	- In the organization attribute, specify the name of your Terraform Cloud organization.
	- The hostname attribute is only necessary with Terraform Enterprise instances.
	- In the name attribute within the workspaces block, specify the name of the new Terraform Cloud workspace to create with your state.
6. Run `terraform init` to migrate the workspace.
7. Configure the Terraform Cloud Workspace. Possible setting changes:
	- Set the VCS repository.
	- Set values for variables.
	- Set team access permissions.
8. Queue a Run in the New Workspace:
	- Run `terraform plan` or navigate to the workspace in Terraform Cloud and queue a plan.
	- The plan should result in no to small changes. After that, Terraform Cloud can take over all Terraform runs for the infrastructure.


> [!WARNING] Troubleshooting
> - If the plan would create an entirely new set of infrastructure resources, you probably have the wrong state file.
> - If the plan recognizes the existing resources but would make unexpected changes, check whether the designated VCS branch for the workspace is the same branch you've been running Terraform on.
