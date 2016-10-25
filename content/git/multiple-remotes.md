# Working with multiple remotes

It may happen that your git repo has multiple remotes e.g. main repo, your fork, a gitlab mirror, etc

##git remote command

Using `git remote add <remote repo alias> <remote repo url>` command you can add multiple remote repos for your git project. After cloning git repo just run 'git remote -v' command and inside repo directory and it will show you the associated remote repo. Git remote is the best thing to maintain code in different git repos.

Check these referece links for more details on `git remote`: [gitref](http://gitref.org/remotes/), [git-scm](http://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes)


##Maintain remote repos

Next thing is to push and pull the code to specific remote repos and syne them all. You must be familiar with `git pull` and `git push` command till this point.

###git pull

`git pull <remote repo alias> <branch name>`

Pull commits from specified branch of remote repo into current branch.

### git push

`git push <remote repo alias> <branch name>`

Push new commits to specified branch of remote repo from current branch. If remote repo don't have specified `branch name` than it will create one with the same name on remote repo.
