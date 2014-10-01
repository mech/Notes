# Git

* [GitHub flow for rapid deployment and web project](http://scottchacon.com/2011/08/31/github-flow.html)
* [GitFlow for infrequent library releases](http://nvie.com/posts/a-successful-git-branching-model/)
* [Git flight rules](https://github.com/k88hudson/git-flight-rules)
* [Pretty nice tips on history and git-blame](http://mislav.uniqpath.com/2014/02/hidden-documentation/)
* [Git Immersion by Neo](http://gitimmersion.com/)
* [Git the safety net](http://alistapart.com/article/git-the-safety-net-for-your-projects)
* [Atlassian's Git Guide](https://www.atlassian.com/git/)

```
git add -u
git add -A

# Undo last commit
git reset --soft HEAD~1
```


## Workflow

Workspace -> Index -(commit)-> Local Repo -(push)-> Remote Repo

Establish version control practices. There are myriad workflows in git. Find one that works for you and stick to it. This will help you plan how you will do releases and handle sticky situations.

Ask yourself questions like — will you tag? If so what is the tag naming convention?

Do you do rebase when you pull or merge when you pull? When you merge branches back into master do you `--squash` or not? 

Do you merge to master with the `--no-ff` flag? What is your method for handling nasty merge conflicts (they will happen and they will happen at the worst time possible)? If you establish all this at the start things will go much more smoothly as you introduce new people to the team - each with their own version control histories and preferences. You don't want a master log full of squashed commits, merge commit from other branches, and rebasing conflict resolution commits. This is terrible. Enforce consistency.


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