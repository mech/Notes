# Git

## Branching

1. At your local machine: `git branch <branch_name>`
2. Push the branch to GitHub: `git push origin <branch_name>`
3. Switch to new branch: `git checkout <branch_name>`
4. Write, test, refactor, commit!
5. Push to GitHub: `git push origin <branch_name>`

Later, while your co-worker at another machine can just:

    git checkout <branch_name>

To delete your branch locally and then remotely:

    git branch -d <branch_name>
    git push origin :<branch_name>

## Stashing

1. Stash away your changes: `git stash`
2. List stash: `git stash list`
3. Restore stash: `git stash apply stash{0}`
4. Clear stash: `git stash clear`

## Pull Request