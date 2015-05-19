# Changelog Generation

TODO:
1. Using git command to generate changelog

####Git change log

```bash
$ git log --oneline --decorate

OR

git shortlog
```

If you only wanted to see the changes between v1.0 and v1.1 you could also use following command,

```bash
git log --oneline --decorate v1.0..v1.1
```

####GitHub Changelog Generator
This gem generates change log file based on tags, issues and merged pull requests (and splits them into separate lists according labels) from GitHub Issue Tracker.
[GitHub Changelog Generator](https://github.com/skywinder/github-changelog-generator)
