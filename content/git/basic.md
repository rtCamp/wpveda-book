git init
git clone
git status
git pull
git pull --rebase
git push
git checkout
git checkout -b
git stash

##5.1.1 : git init

**git init** command used to initialize a empty git repository or reinitialize existing repository.

It will create **.git** folder into your working directory with some other folders and file like branches, hooks, objects, refs etc. An initial HEAD file refer the HEAD of the master branch is created.

>> command: git init

To create new repository, follow this 3 step: [ in below example we create repository with name **example-git** ]

####Example:
```
First you need to create folder into your local machine for git repository.
$ mkdir example-git

Change your working directory as new repository foolder [ example-git ]
$ cd example-git

Execute **git init** to create ot initialize git repository
$ cd example-git
```
reference link : http://git-scm.com/docs/git-init

##5.1.2 : git clone

If you want to work with existing repository then you need to clone your existing repository into your local machine.

For clone repository into your local directory you need to use ** git clone **

>> command: git clone << repository url >>

** you can find git repository url from repository page on github.com.

####Example:
```
To clone wpveda book repo imto your local machine
$ git clone https://github.com/wpveda/book.git
```
reference link : http://git-scm.com/docs/git-clone

##5.1.3 : git status

**git status** command shows status of current repository.

>> command: git status

Status contains list of files which have differences between the Working tree and the index file, files which are not tracked by git.
 It's also show difference of local commit and remote commit so you can know how many commit are not push into remote branch.

####Example:
```
To know status of **example-git** repository execute below command
$ git status
```
reference link : http://git-scm.com/docs/git-status

##5.1.4 : git fetch

Fetch command use to fetch object anf refs from remote or any other repository

>> command: git fetch [option] [remote] [branch]

This command also fetch branches or tags from more then one repository with the object for that histories.
by default it will use origin remote.

####Example:
```
To fetch all branch or tag of origin remote
$ git fetch

To fetch all branch or tag of all configured remote
$ git fetch --all

To fetch master branch of origin remote
$ git fetch origin master

```
reference link : http://git-scm.com/docs/git-fetch

##5.1.5 : git pull

To fetch change form remote or other repository and integrate with repository or local branch git provides **git pull** command

>> command: git pull [option] [remote] [branch]

git runs **git fetch** with given parameter and after that it will runs git merge to merge retrieved branch changes into current branch.

#### Option:

* --rebase: its will run git rebase after git fetch.

* --no-commit: with this option, it's perform git merge without affect merge fail and autocommit.

* --force: it will force to fetch changes from remote and merge it with current branch.

Note: **--rebase** is more preferable to use with git pull, please refer given link for better idea  https://www.atlassian.com/git/tutorials/merging-vs-rebasing/

####Example:
```

```








