# Rebase

In Git, there are two main ways to integrate changes from one branch into another: the merge and the rebase.

Rebasing is the process of moving a branch to a new base commit.

From a content perspective, rebasing really is just moving a branch from one commit to another. But internally, Git accomplishes this by creating new commits and applying them to the specified base—it’s literally rewriting your project history. It’s very important to understand that, even though the branch looks the same, it’s composed of entirely new commits.

###Usage
``` shell
git rebase <base>
```
Rebase the current branch onto <base>, which can be any kind of commit reference (an ID, a branch name, a tag, or a relative reference to HEAD).

###Discussion

The primary reason for rebasing is to maintain a linear project history. For example, consider a situation where the master branch has progressed since you started working on a feature:

Before merge/rebase

```
A <- B <- C    [master]
^
 \
  D <- E       [feature]
```

After `git merge master`

```
A <- B <- C
^         ^
 \         \
  D <- E <- F
```

after `git rebase master`
```
A <- B <- C
^         ^
 \         \
  D <- E <- F
```

Rebasing is a common way to integrate upstream changes into your local repository. Pulling in upstream changes with git merge results in a superfluous merge commit every time you want to see how the project has progressed. On the other hand, rebasing is like saying, “I want to base my changes on what everybody has already done.”
