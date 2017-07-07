# Rebase

In Git, there are two main ways to integrate changes from one branch into another: the merge and the rebase.

Rebasing is the process of moving a branch to a new base commit.

From a content perspective, rebasing really is just moving a branch from one commit to another. But internally, Git accomplishes this by creating new commits and applying them to the specified base—it’s literally rewriting your project history. It’s very important to understand that, even though the branch looks the same, it’s composed of entirely new commits.

### Usage
``` shell
git rebase <base>
```
Rebase the current branch onto <base>, which can be any kind of commit reference (an ID, a branch name, a tag, or a relative reference to HEAD).

### Discussion

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

### Example

The example below combines git rebase with git merge to maintain a linear project history. This is a quick and easy way to ensure that your merges will be fast-forwarded.

```shell
# Start a new feature
git checkout -b new-feature master
# Edit files
git commit -a -m "Start developing a feature"
```

In the middle of our feature, we realize there’s a security hole in our project

```shell
# Create a hotfix branch based off of master
git checkout -b hotfix master
# Edit files
git commit -a -m "Fix security hole"
# Merge back into master
git checkout master
git merge hotfix
git branch -d hotfix
```

After merging the hotfix into master, we have a forked project history. Instead of a plain git merge, we’ll integrate the feature branch with a rebase to maintain a linear history:

```shell
git checkout new-feature
git rebase master
```

This moves new-feature to the tip of master, which lets us do a standard fast-forward merge from master:

```shell
git checkout master
git merge new-feature
```

## Interactive Rebase

Running git rebase with the `-i` flag begins an interactive rebasing session. Instead of blindly moving all of the commits to the new base, interactive rebasing gives you the opportunity to alter individual commits in the process. This lets you clean up history by removing, splitting, and altering an existing series of commits. It’s like git commit --amend on steroids.

### Usage

```shell
git rebase -i <base>
```
Rebase the current branch onto <base>, but use an interactive rebasing session. This opens an editor where you can enter commands (described below) for each commit to be rebased. These commands determine how individual commits will be transferred to the new base. You can also reorder the commit listing to change the order of the commits themselves.

### Discussion

Interactive rebasing gives you complete control over what your project history looks like. This affords a lot of freedom to developers, as it lets them commit a “messy” history while they’re focused on writing code, then go back and clean it up after the fact.

Most developers like to use an interactive rebase to polish a feature branch before merging it into the main code base. This gives them the opportunity to squash insignificant commits, delete obsolete ones, and make sure everything else is in order before committing to the “official” project history. To everybody else, it will look like the entire feature was developed in a single series of well-planned commits.

### Example

The example found below is an interactive adaptation of the one from the non-interactive git rebase page.

```shell
# Start a new feature
git checkout -b new-feature master
# Edit files
git commit -a -m "Start developing a feature"
# Edit more files
git commit -a -m "Fix something from the previous commit"

# Add a commit directly to master
git checkout master
# Edit files
git commit -a -m "Fix security hole"

# Begin an interactive rebasing session
git checkout new-feature
git rebase -i master
```
The last command will open an editor populated with the two commits from new-feature, along with some instructions

```shell
pick 32618c4 Start developing a feature
pick 62eed47 Fix something from the previous commit
```

You can change the pick commands before each commit to determine how it gets moved during the rebase. In our case, let’s just combine the two commits with a squash command

```shell
pick 32618c4 Start developing a feature
squash 62eed47 Fix something from the previous commit
```

Save and close the editor to begin the rebase. This will open another editor asking for the commit message for the combined snapshot. After defining the commit message, the rebase is complete and you should be able to see the squashed commit in your git log output.

## When should I use git pull --rebase?

I know of some people who use `git pull --rebase` by default and others who insist never to use it. I believe I understand the difference between merging and rebasing, but I'm trying to put this in the context of git pull.

You should use git `pull --rebase` when your changes do not deserve a separate branch
Indeed -- why not then? It's more clear, and doesn't impose a logical grouping on your commits.

I would like to provide a different perspective on what `git pull --rebase` actually means, because it seems to get lost sometimes.

Ok, I suppose it needs some clarification. In Git, as you probably know, you're encouraged to branch and merge. Your local branch, into which you pull changes, and remote branch are, actually, different branches, and git pull is about merging them. It's reasonable, since you push not very often and usually accumulate a number of changes before they constitute a completed feature.

However, sometimes--by whatever reason--you think that it would actually be better if these two--remote and local--were one branch. Like in ***SVN***. It is here where `git pull --rebase` comes into play. You no longer merge--you actually commit on top of the remote branch. That's what it actually is about.

Whether it's dangerous or not is the question of whether you are treating local and remote branch as one inseparable thing. Sometimes it's reasonable (when your changes are small, or if you're at the beginning of a robust development, when important changes are brought in by small commits). Sometimes it's not (when you'd normally create another branch, but you were too lazy to do that). But that's a different question.
