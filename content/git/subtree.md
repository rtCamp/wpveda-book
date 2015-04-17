# Subtree

Subtrees allow subprojects to be included within a subdirectory of the main project.

Subtrees are not to be confused with submodules, which are meant for
the same task.

Unlike submodules, subtrees do not need any special
constructions (like `.gitmodule` files or gitlinks) be present in your repository, and do not force end-users of your repository to do anything special or to understand how subtrees work.

A subtree is just a subdirectory that can be
committed to, branched, and merged along with your project in any way you want.

## Starting with subtree

### Add a subtree in a repository

`git subtree add` command would simply add a subtree into your repo.

Let's take an example of [rtBiz](https://github.com/rtCamp/rtbiz/) in which git subtree is used.

``` shell
rtbiz|master ⇒ git subtree add --prefix app/lib https://github.com/rtCamp/rt-lib.git master --squash
git fetch https://github.com/rtCamp/rt-lib.git master
warning: no common commits
remote: Counting objects: 2327, done.
remote: Total 2327 (delta 0), reused 0 (delta 0), pack-reused 2327
Receiving objects: 100% (2327/2327), 899.12 KiB | 153.00 KiB/s, done.
Resolving deltas: 100% (1375/1375), done.
From https://github.com/rtCamp/rt-lib
 * branch            master     -> FETCH_HEAD
Added dir 'app/lib'
```

Above command,

``` shell
git subtree add --prefix <SUBTREE-DIRECTORY> <GIT-URL> <BRANCH> --squash
```

will create a directory in your main repository and clone the sub-repository in there along with all its source code.

Like this, the sub-repository will literally reside into your main repository.

After this, the changes are already saved into your git history with a squash commit.

``` shell
rtbiz|master ⇒ git log

commit 6841a94f72b41d80bf42cdbf9483980ab157b62e
Merge: a97da4a b66d0a2
Author: Udit Desai <desaiuditd@gmail.com>
Date:   Wed Apr 8 13:33:00 2015 +0530

    Merge commit 'b66d0a2bb78f070988b6c5cce293720662da3166' as 'app/lib'

commit b66d0a2bb78f070988b6c5cce293720662da3166
Author: Udit Desai <desaiuditd@gmail.com>
Date:   Wed Apr 8 13:33:00 2015 +0530

    Squashed 'app/lib/' content from commit 42ba876

    git-subtree-dir: app/lib
    git-subtree-split: 42ba876768960e5a646ee8a4d361ced8b31449dc

commit a97da4a07de0394c363948198cae78086fdaa16d
Author: Udit Desai <desaiuditd@gmail.com>
Date:   Wed Apr 8 13:32:42 2015 +0530

    Test Commit
```

## Cloning a project with submodule

You simply need to `git clone` the main repository in order to clone, as the subtree source code is already a part of the main repository now.

``` shell
~|⇒ git clone git@github.com:rtCamp/rtbiz.git
Cloning into 'rtbiz'...
remote: Counting objects: 7641, done.
remote: Compressing objects: 100% (90/90), done.
remote: Total 7641 (delta 49), reused 0 (delta 0), pack-reused 7544
Receiving objects: 100% (7641/7641), 6.29 MiB | 379.00 KiB/s, done.
Resolving deltas: 100% (4247/4247), done.
Checking connectivity... done.
```

If you check in `app/lib` directory, the codes from the subtree will exists.

``` shell
rtbiz|master ⇒ cd app/lib
lib|master ⇒ ls -lsa
total 120
 4 drwxrwxr-x 19 udit udit  4096 Apr  8 13:33 .
 4 drwxrwxr-x  3 udit udit  4096 Apr  8 13:33 ..
 4 drwxrwxr-x  2 udit udit  4096 Apr  8 13:33 bin
 4 -rw-rw-r--  1 udit udit   790 Apr  8 13:33 .editorconfig
 4 -rwxrwxr-x  1 udit udit    57 Apr  8 13:33 .gitignore
 0 lrwxrwxrwx  1 udit udit    17 Apr  8 13:33 .jshintignore -> bin/.jshintignore
 0 lrwxrwxrwx  1 udit udit    13 Apr  8 13:33 .jshintrc -> bin/.jshintrc
20 -rw-rw-r--  1 udit udit 18332 Apr  8 13:33 LICENSE.txt
 4 -rw-rw-r--  1 udit udit   321 Apr  8 13:33 phpunit.xml
 4 -rw-rw-r--  1 udit udit  3193 Apr  8 13:33 readme.md
 4 -rw-rw-r--  1 udit udit  2529 Apr  8 13:33 readme.txt
 4 drwxrwxr-x  5 udit udit  4096 Apr  8 13:33 rt-attributes
 4 drwxrwxr-x  2 udit udit  4096 Apr  8 13:33 rt-db-model
 4 drwxrwxr-x  2 udit udit  4096 Apr  8 13:33 rt-db-update
 4 drwxrwxr-x  4 udit udit  4096 Apr  8 13:33 rt-email-template
 4 drwxrwxr-x  3 udit udit  4096 Apr  8 13:33 rt-guide-tour
 4 drwxrwxr-x  6 udit udit  4096 Apr  8 13:33 rt-importer
 4 -rw-rw-r--  1 udit udit  1164 Apr  8 13:33 rt-lib.php
 4 drwxrwxr-x  8 udit udit  4096 Apr  8 13:33 rt-mailbox
 4 drwxrwxr-x  2 udit udit  4096 Apr  8 13:33 rt-offerings
 4 drwxrwxr-x  2 udit udit  4096 Apr  8 13:33 rt-plugin-info
 4 drwxrwxr-x  2 udit udit  4096 Apr  8 13:33 rt-plugin-update-checker
 4 drwxrwxr-x  2 udit udit  4096 Apr  8 13:33 rt-reports
 4 drwxrwxr-x  2 udit udit  4096 Apr  8 13:33 rt-theme-info
 4 drwxrwxr-x  2 udit udit  4096 Apr  8 13:33 rt-theme-update-checker
 4 drwxrwxr-x  4 udit udit  4096 Apr  8 13:33 rt-user-groups
 4 drwxrwxr-x  2 udit udit  4096 Apr  8 13:33 rt-wp-autoloader
 4 drwxrwxr-x  4 udit udit  4096 Apr  8 13:33 tests
 0 lrwxrwxrwx  1 udit udit    15 Apr  8 13:33 .travis.yml -> bin/.travis.yml

```

## Working on a project with subtree

### To pull changes from upstream

Simply run following command and your subtree will be updated with the latest changes from the external repository.

``` shell
git subtree pull --prefix <SUBTREE-DIRECTORY> <GIT-URL> <BRANCH> --squash
```

#### Example

``` shell
rtbiz|master ⇒ git subtree pull --prefix app/lib https://github.com/rtCamp/rt-lib.git master --squash
warning: no common commits
remote: Counting objects: 2362, done.
remote: Compressing objects: 100% (18/18), done.
remote: Total 2362 (delta 7), reused 0 (delta 0), pack-reused 2344
Receiving objects: 100% (2362/2362), 917.97 KiB | 216.00 KiB/s, done.
Resolving deltas: 100% (1407/1407), done.
From https://github.com/rtCamp/rt-lib
 * branch            master    -> FETCH_HEAD
Merge made by the 'recursive' strategy.
 app/lib/rt-attributes/class-rt-attributes.php                          |  20 ++++++++++++------
 app/lib/rt-attributes/model/class-rt-attributes-relationship-model.php |   5 +++++
 app/lib/rt-mailbox/class-rt-mail-cron.php                              |   5 -----
 app/lib/rt-mailbox/class-rt-zend-mail.php                              | 129 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++-----------------------------------------------------
 app/lib/rt-mailbox/helper/rt-mailbox-functions.php                     |  44 ++++++++++++++++++++++++++++++++-------
 app/lib/rt-mailbox/settings/class-rt-mail-settings.php                 |  25 ----------------------
 app/lib/rt-mailbox/settings/class-rt-setting-inbound-email.php         |   6 +++---
 app/lib/rt-offerings/class-rt-offerings.php                            |  33 +++++++++++++++--------------
 8 files changed, 146 insertions(+), 121 deletions(-)
```

And your subtree will be updated to latest changes after this.

## When to use subtree (Submodule vs Subtree)

[rtBiz](https://github.com/rtCamp/rtbiz/), chose to use subtree because, it used many of the libraries from [rt-Lib](https://github.com/rtCamp/rt-lib/) as some of the core functionalities. So rtBiz had the necessity of keeping the external code literally inside its repository when it is running.

There are several reasons why you might find subtree better to use:

- Management of a simple workflow is easy.
- Older version of git are supported (even before v1.5.2).
- The sub-project's code is available right after the clone of the super project is done.
- `subtree` does not require users of your repository to learn anything new, they can ignore the fact that you are using subtree to manage dependencies.
- `subtree` does not add new metadata files like `submodules` doe (i.e. `.gitmodule`).
- Contents of the module can be modified without having a separate repository copy of the dependency somewhere else.

There are a few drawbacks in using subtree, but they are acceptable in compared with Submodule.

- You must learn about a new merge strategy (i.e. `subtree`).
- Contributing code back `upstream` for the sub-projects is slightly more complicated.
- The responsibility of not mixing super and sub-project code in commits lies with you.

**References :**

- http://blogs.atlassian.com/2013/05/alternatives-to-git-submodule-git-subtree/
