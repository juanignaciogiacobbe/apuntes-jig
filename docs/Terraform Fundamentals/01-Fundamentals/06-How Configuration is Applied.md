> [!NOTE] `Create`
> Create resources that exist in the configuration but are not associated with a real infrastructure object in the state.


> [!NOTE] `Destroy`
> Destroy resources that exist in the state but no longer exist in the configuration.


> [!NOTE] `Update-in-place`
> Update in-place resources whose arguments have changed.


> [!NOTE] `Destroy and re-create`
> Destroy and re-create resources whose arguments have changed, but which cannot be updated in-place due to remote API limitations.
