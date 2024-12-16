> [!IMPORTANT] Git
> Source Code Management(SCM) tool.
> Used for tracking changes in code.
> Can be distributed.
> Allows for colaboration.
> Allows versioning of files.

## Git Configuration
- `git config --global user.name`
- `git config --global user.email`
- `git init`
- `.gitignore`

## Git File System
- `tree .git` shows the exploded view of the Git File System.
- `config` is where the local configuration is stored.
- `HEAD` actually points to the current directory the branch that you're in.
- `hooks` is where you store any scripts that need to be run when a commit is made. Anything that reacts to a commit or a merge is going to go into hooks.
- `logs` is where the branch logs are located.
- `objects` is the actual store where objects are place when you do a commit.


> [!IMPORTANT] Git Branches
> These are used to separate code changes.
> They allow multiple users to work on code.

## Git branches Workflow
1. Code is "checked out".
2. Code is changed/ updated and tested.
3. Code is merged back into the master branch.