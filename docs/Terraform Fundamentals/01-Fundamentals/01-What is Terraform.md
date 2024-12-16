# Terraform

> [!NOTE] Terraform
> It is a tool for building, changing, and versioning infrastructure safely and efficiently, locally or in the cloud.
> You can manage existing and popular service providers as well as custom in-house solutions.

## Terraform Architecture

![](img/Pasted%20image%2020240925082802.png)


## Key Features

> [!NOTE] Infrastructure as Code
> Your infrastructure is described using a high-level configuration syntax. This allows your infrastructure to be versioned and treated as you would any other code.
> It can also be shared and re-used.


> [!NOTE] Execution Plans
> Terraform generates an execution plan with its "planning" step. This shows what Terraform will do when you apply the configuration.
> This allows you to avoid any surprises when Terraform manipulates infrastructure.


> [!NOTE] Resource Graph
> Terraform builds infrastructure as efficiently as possible, and operators get insight into dependencies in their infrastructure.
> It accomplishes this by building a graph of all your resources, and it gives you greater insight into the creation and modification of any non-dependent resources.


> [!NOTE] Change Automation
> Complex changes can be applied to your infrastructure with minimal interaction.
> With the combination of the execution plan and resource graph, you will know exactly what Terraform will change and in what order. This will help avoid many possible human errors.

