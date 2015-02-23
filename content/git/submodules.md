# Submodules

Submodules are third-party git repositories which can be embedded into your own repository.

They are not to be confused with remotes, which are meant mainly for branches of the same project; submodules are meant for different projects you would like to make part of your source code.

## Starting with submodules

### Add a submodule in a repository

`git submodule add` command followed by a git url of the external project would simply add a submodule into your repo.

Let's take an example of [Watchman plugin](https://github.com/desaiuditd/watchman/) in which git submodule is used.

``` shell
watchman|master ⇒ git submodule add https://github.com/xwp/wp-dev-lib.git dev-lib
Cloning into 'dev-lib'...
remote: Counting objects: 534, done.
remote: Total 534 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (534/534), 90.18 KiB | 16.00 KiB/s, done.
Resolving deltas: 100% (313/313), done.
Checking connectivity... done.
```

By default, submodules will add the subproject into a directory named the same as the repository. You can add a different path at the end of the command if you want it to go elsewhere. In this case, repository name is `wp-dev-lib`, but it is added into `dev-lib` directory.

### Checking repository status

If you run `git status` at this point, you'll notice a few things.

``` shell
watchman|master⚡ ⇒ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   .gitmodules
	new file:   dev-lib
```

### Check content of `.gitmodules`

First you should notice the new .gitmodules file. This is a configuration file that stores the mapping between the project's URL and the local subdirectory you've pulled it into:

``` shell
watchman|master⚡ ⇒ cat .gitmodules
[submodule "dev-lib"]
	path = dev-lib
	url = https://github.com/xwp/wp-dev-lib.git
```

It's important to note that this file is version-controlled with your other files, like your `.gitignore` file. It's pushed and pulled with the rest of your project. This is how other people who clone this project know where to get the submodule projects from.

### Save changes to repository

When you commit, you see something like this:

``` shell
watchman|master⚡ ⇒ git commit -am "Adding dev-lib as submodule"
[master df049b6] Adding dev-lib as submodule
 2 files changed, 4 insertions(+)
 create mode 100644 .gitmodules
 create mode 160000 dev-lib
```

## Cloning a project with submodule

### Regular clone

When you clone such a project, by default you get the directories that contain submodules, but none of the files within them yet:

``` shell
~|⇒ git clone https://github.com/desaiuditd/watchman/
Cloning into 'watchman'...
remote: Counting objects: 271, done.
remote: Total 271 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (271/271), 118.23 KiB | 53.00 KiB/s, done.
Resolving deltas: 100% (106/106), done.
Checking connectivity... done.
~|⇒ cd watchman
watchman|master ⇒ ls -lsa
total 96
 4 drwxrwxr-x 10 udit udit  4096 Feb 23 17:15 .
 4 drwxr-xr-x 81 udit udit  4096 Feb 23 17:15 ..
 4 drwxrwxr-x  2 udit udit  4096 Feb 23 17:15 assets
 4 drwxrwxr-x  2 udit udit  4096 Feb 23 17:15 dev-lib
 4 -rw-rw-r--  1 udit udit   790 Feb 23 17:15 .editorconfig
 4 drwxrwxr-x  8 udit udit  4096 Feb 23 17:15 .git
 4 -rw-rw-r--  1 udit udit     6 Feb 23 17:15 .gitignore
 4 -rw-rw-r--  1 udit udit    83 Feb 23 17:15 .gitmodules
 0 lrwxrwxrwx  1 udit udit    13 Feb 23 17:15 .jshintrc -> bin/.jshintrc
 4 drwxrwxr-x  2 udit udit  4096 Feb 23 17:15 lib
20 -rw-rw-r--  1 udit udit 18027 Feb 23 17:15 LICENSE
 4 -rw-rw-r--  1 udit udit   321 Feb 23 17:15 phpunit.xml
 4 -rw-rw-r--  1 udit udit  3004 Feb 23 17:15 readme.md
 4 -rw-rw-r--  1 udit udit  3308 Feb 23 17:15 readme.txt
 4 drwxrwxr-x  2 udit udit  4096 Feb 23 17:15 revision
 4 drwxrwxr-x  2 udit udit  4096 Feb 23 17:15 settings
 4 -rw-rw-r--  1 udit udit    42 Feb 23 17:15 svn-url
 4 drwxrwxr-x  3 udit udit  4096 Feb 23 17:15 tests
 0 lrwxrwxrwx  1 udit udit    15 Feb 23 17:15 .travis.yml -> bin/.travis.yml
 4 drwxrwxr-x  4 udit udit  4096 Feb 23 17:15 ui
 8 -rw-rw-r--  1 udit udit  4703 Feb 23 17:15 watchman.php
watchman|master ⇒ cd dev-lib
dev-lib|master ⇒ ls -lsa
total 8
4 drwxrwxr-x  2 udit udit 4096 Feb 23 17:15 .
4 drwxrwxr-x 10 udit udit 4096 Feb 23 17:15 ..
```

The `dev-lib` directory is there, but it's empty. You **must** run two commands:

- `git submodule init` to initialize your local configuration file.
- `git submodule update` to fetch all the data from that project.

Then check out the appropriate commit listed in your superproject:

``` shell
watchman|master ⇒ git submodule init
Submodule 'dev-lib' (https://github.com/xwp/wp-dev-lib.git) registered for path 'dev-lib'
watchman|master ⇒ git submodule update
Cloning into 'dev-lib'...
remote: Counting objects: 534, done.
remote: Total 534 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (534/534), 90.18 KiB | 44.00 KiB/s, done.
Resolving deltas: 100% (313/313), done.
Checking connectivity... done.
Submodule path 'dev-lib': checked out '9d192ce5df7b163a08fefbe64a37e9ab98333005'
```

Now your `dev-lib` subdirectory is at the exact state it was in when you committed earlier.

### Recursive Clone

There is another way to do this which is a little simpler, however. If you pass `--recursive` to the `git clone` command, it will automatically initialize and update each submodule in the repository.

``` shell
~|⇒ git clone --recursive https://github.com/desaiuditd/watchman/
Cloning into 'watchman'...
remote: Counting objects: 271, done.
remote: Total 271 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (271/271), 118.23 KiB | 42.00 KiB/s, done.
Resolving deltas: 100% (106/106), done.
Checking connectivity... done.
Submodule 'dev-lib' (https://github.com/xwp/wp-dev-lib.git) registered for path 'dev-lib'
Cloning into 'dev-lib'...
remote: Counting objects: 534, done.
remote: Total 534 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (534/534), 90.18 KiB | 50.00 KiB/s, done.
Resolving deltas: 100% (313/313), done.
Checking connectivity... done.
Submodule path 'dev-lib': checked out '9d192ce5df7b163a08fefbe64a37e9ab98333005'
```

## Working on a project with submodules

### To pull changes from upstream

Simply run following command and your submodule will be updated with the latest changes from the external repository.

``` shell
# git submodule update --remote <submodule-directory>
git submodule update --remote dev-lib
# git add <submodule-directory>
git add dev-lib
# Commit the changes in your own repository
git commit -m "Update dev-lib"
```

## When to use submodules

If you observe closely the above example of [Watchman plugin](https://github.com/desaiuditd/watchman/), submodule is used for a library which is a helper tool for developers.

To be precise, it is not a part of a crux of the plugin. The code that is coming from external library is not used in the execution of the plugin.

The fact :

> When you clone a project with submodules in it, by default you get the directories that contain submodules, but none of the files within them.

plays a very decisive part in choosing submodules for a project.

For this example of plugin, the author could use submodule because he did not wanted the code in the execution of the plugin.

If there is any library and its code which is required in the core execution, then submodule is not quite a good option. Because, the code you will need for the execution won't be present in the repository after a regular clone and your plugin may break. Of course, you will need a explicit reminder to either do a *recursive clone* or *submodule init/update* which is an overhead.

This is just one important fact that comes in the picture when while using submodules in a project.

Subtree is another promising alternative for Submodule. A detailed comparison between two is explained in the latter chapter of this book.

TODO
1. When to use git submodules
2. How to use
3. examples - any real world project, preferably wordpress project. Explain how that project is using
