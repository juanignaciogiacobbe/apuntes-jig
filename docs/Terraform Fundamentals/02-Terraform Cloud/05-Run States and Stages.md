# The 6 Stages of Run State

## 1. The Pending Stage
- Pending State: Terraform Cloud hasn't stated action on any run yet. It processes each workspace's runs in the order they were queued.
- Leaving this stage:
	- Proceeds automatically to the plan stage when it becomes the first run in the queue.
	- Can skip to completion if a user discards it before it starts.

## 2. The Plan Stage
- Planning State: Terraform Cloud is currently running `terraform plan`.
- Needs Confirmation State: `terraform plan` has finished. Runs sometimes pause in this state, depending on the workspace and organization settings.
- Leaving this stage:
	- If the `terraform plan` command failed, the run skips to completion.
	- If a user canceled the plan by pressing the "Cancel Run" button, the skips to completion.
	- If the plan succeeded and doesn't require any changes, the run skips to completion.
	- If the plan succeeded and requires changes, it will proceed to the proper stage.

## 3. The Cost Estimation Stage
- Cost Estimating State: Terraform Cloud is currently estimating the resources in the plan.
- Cost Estimated State: The cost estimate completed.
- Leaving this stage:
	- If the cost estimation succeeded or errors, the run moves to the next stage.
	- If there are no policy checks or applies, the run skips to completion.