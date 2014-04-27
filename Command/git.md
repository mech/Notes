# Git

* [GitHub flow for rapid deployment and web project](http://scottchacon.com/2011/08/31/github-flow.html)
* [GitFlow for infrequent library releases](http://nvie.com/posts/a-successful-git-branching-model/)

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

* [Learn Git Branching](http://pcottle.github.io/learnGitBranching/)

If the remote already has the branch and your local do not have it, just use:

    git branch --track staging origin/staging
    
Beware of merge ambush on feature branch.
Trunk-based development.

## Stashing

1. Stash away your changes: `git stash`
2. List stash: `git stash list`
3. Restore stash: `git stash apply stash{0}`
4. Clear stash: `git stash clear`

## Pull Request

## Fork

* [Syncing a fork](https://help.github.com/articles/syncing-a-fork)