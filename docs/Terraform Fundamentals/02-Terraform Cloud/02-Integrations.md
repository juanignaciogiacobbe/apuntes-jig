# Terraform Cloud and VCS
- Terraform Cloud is more powerful when you integrate it with a Version Control System(VCS).
- When workspaces are linked to a VCS repository, Terraform Cloud can automatically initiate Terraform runs when changes are commited.
- Terraform Cloud makes code review easier by automatically predicting how pull requests will affect infrastructure.
- Publishing new versions of a private Terraform modules is like pushing a tag to the module's repo.


> [!WARNING] How VCS access is used

- Most workspaces in Terraform Cloud are associated with a VCS repository, which provides Terraform configurations for that workspace. To find out which repos are available, access their contents, and create webhooks, Terraform Cloud needs access to your VCS provider.
- To use VCS configs, Terraform Cloud need to do the following:
	- Access a list of repositories.
	- Register webhooks with your VCS provider.
	- Download the contents of a repository at a specific commit.


> [!IMPORTANT] Webhooks
> When someone adds new commits to a branch, any Terraform Cloud workspaces based on that branch will begin a Terraform run.
> When someone submits a pull request/merge request to a branch, any Terraform Cloud workspaces based on that branch will perform a speculative plan with the contents of the request and links to the results on the pull request's page.


## Tips for Using SSH Keys
1. For most supported VCS providers, Terraform Cloud does not need an SSH key. The exceptions are Azure DevOps Server and Bitbucket Server, which require an SSH key for downloading repository contents.
2. For other VCS providers, most organizations will not need to add an SSH private key. However, if the organization repositories include [Git](CompTIA%20Linux%20+%20XK0-OO4/Git/Git.md) submodules that can only be accessed via SSH, an SSH key can be added along with the OAuth credentials.
3. For VCS providers where adding an SSH private key is optional, SSH will only be used to clone Git submodules. All other Git operations will still use HTTPS.