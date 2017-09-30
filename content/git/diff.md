# Git Diff

Using visual git tools can save time and help you efficiently review changes.

There are many tools but we prefer and recommend [diffmerge](http://www.sourcegear.com/diffmerge/downloads.php). It's open-source and cross-platform.

## Important Note for Mac

Please download "installer" version, not "DMG" version.

## Install

1. [Download diffmerge for your platform](http://www.sourcegear.com/diffmerge/downloads.php).
2. Run following commands on your machine to set `diffmerge` as git's diff and merge tool.

```
git config --global diff.tool diffmerge
git config --global difftool.diffmerge.cmd 'diffmerge "$LOCAL" "$REMOTE"'
git config --global merge.tool diffmerge
git config --global mergetool.diffmerge.cmd 'diffmerge --merge --result="$MERGED" "$LOCAL" "$(if test -f "$BASE"; then echo "$BASE"; else echo "$LOCAL"; fi)" "$REMOTE"'
git config --global mergetool.diffmerge.trustExitCode true
```

After this instead of `git diff`, you can use `git difftool`.

To resolve merge conflicts, you can run `git mergetool`

TODO: if there are multiple files modified, `git difftool` can't open them all together. `git difftool -d` opens two dir but `diffmerge` doesn't show diff. Not sure it it's diffmerge issue or `git difftool` issue.

## References

1. Main Source for this article - http://twobitlabs.com/2011/08/install-diffmerge-git-mac-os-x/
2. [Meld](http://meldmerge.org/) - an alternative to diffmerge. *Not tested yet.*
3. More diff tools for Mac - http://www.git-tower.com/blog/diff-tools-mac/

