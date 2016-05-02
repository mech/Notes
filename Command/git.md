# Git

**Virtual commit - See Bamboo**

Discuss your code changes before they get merged! - Use Pull Request

Git is a 3-stage thinking: Working -> Staging (`git add`) -> Repo (`git commit`)

* [Git Style Guide](https://github.com/agis-/git-style-guide)
* [GitHub flow for rapid deployment and web project](http://scottchacon.com/2011/08/31/github-flow.html)
* [GitFlow for infrequent library releases](http://nvie.com/posts/a-successful-git-branching-model/)
* [Git flight rules](https://github.com/k88hudson/git-flight-rules)
* [Pretty nice tips on history and git-blame](http://mislav.uniqpath.com/2014/02/hidden-documentation/)
* [Git Immersion by Neo](http://gitimmersion.com/)
* [Git the safety net](http://alistapart.com/article/git-the-safety-net-for-your-projects)
* [Atlassian's Git Guide](https://www.atlassian.com/git/)
* [How to write the perfect pull request](https://github.com/blog/1943-how-to-write-the-perfect-pull-request)
* [How to undo almost anything with git](https://github.com/blog/2019-how-to-undo-almost-anything-with-git)
* [Atlassian has nice doc](https://www.atlassian.com/git/tutorials/undoing-changes)
* [Read about the Git Objects](https://git-scm.com/book/en/v2/Git-Internals-Git-Objects)
* [19 git tips for everyday use](http://www.alexkras.com/19-git-tips-for-everyday-use/)

```
▶ git add -u
▶ git add -A

▶ git commit -A -m '' # Only add in modification that has been tracked

▶ git checkout -- filename # To undo deletion if you have not stage
▶ git reset HEAD filename  # To undo if you have staged it

## Plumbing and Porcelain

Plumbing is the low level utilities. Rarely seems but working behind the scene.

Porcelain is the set of useful commands. SHA hash is the implementation details. User do not need to know. Porcelain are comprises of plumbing.

# Undo last commit
▶ git reset --soft HEAD~1
▶ git reset --soft HEAD^
▶ git reset --mixed HEAD^

# Get back things you have lost
▶ git reflog
▶ git reset --hard HEAD@{1}
```

## HEAD

```
HEAD^
HEAD~3

git log HEAD^^^..HEAD -p # In patch format, 3 back
```

## Amend

After your commit, you realise the same file need some more modification, you can amend the previous commit. Only the previous commit and a new commit SHA will be produced.

```
git add filename
git commit --amend # Bring up the editor so you can commit new message
```

## Revert

Go back in time and revert commits.

## Rebasing

1. Keep a nice clean history. Improve commit message. Bring your work up to date.
2. Manipulate history, done through interactive rebasing.

```
// Check what your feature branch is lacking in behind
git log ..master

git rebase master

// Recorded resolution???
git config --global rerere.enabled true

git rebase -i SHA1 // Interactive for you to pick, squash, edit, reword

git pull --rebase
```

```
▶ git rebase --interactive HEAD^^^
// Then pick or edit your commit from now on...
▶ git reflog
```

## Workflow

1. Centralized
2. Patch - Linux and quite an old way to work. Do not trust other people
3. Forking - Fork your copy and merge with pull request. More modern.
4. Branched - What Jobline is currently doing. We do trust our collaborator.

The original repository is the upstream. Your forks is your own copy.

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

Feature branching has "big scary merge" problem. Cherry-picking may not be the solution. Instead, use trunk based development.

See http://paulhammant.com/2013/04/05/what-is-trunk-based-development/

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

## Tags

A point in time. A bookmark.

```
git tag                  # See your tags
git tag tag_name sha1    # Tag it
git tag -a tag_name sha1 # Vim open to let you annotate

git tag -d tag_name      # Delete tag

git show tag_name        # Show the diff
git checkout tag_name    # Detached HEAD
git checkout master      # Attached the HEAD back!

git checkout -- filename    # Remove the edited file
git checkout -b branch_name # Actually commit changes

git push --tags origin   # Add
git push origin :tagname # Remove
```

## Bisect

Finding the last working state with Bisect. Walk through a series of commit and branch out.

You want to find bad bug. Not finding bug you have fixed.

```
git bisect start     # Start the bisect
git bisect good sha1 # State the good commit
git bisect bad sha1  # State the bad commit

git bisect good # Git will give you single commit to check
git bisect good # Found!!
git checkout -b fix_branch_name # Edit the fix
git bisect reset

```


## Stashing

1. Stash away your changes: `git stash`
2. List stash: `git stash list`
3. Restore stash: `git stash apply stash{0}` or `git stash pop`
4. Clear stash: `git stash clear` or `git stash drop stash@{0}`

## Pull Request

## Fork

* [Syncing a fork](https://help.github.com/articles/syncing-a-fork)