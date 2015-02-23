# Workflow

There will be two branches to start with

1. `master`: Default branch when you `git init`. This is stable branch. Latest stable tag will always point to this.
2. `develop`: Development branch. This will be like nightly release branch. Latest RC/alpha/beta release will always point to this.

## Process:

1. When you do `git init`, you will get a `master` branch automatically.
2. Always run `git checkout -b develop` to start a develop branch. Yes, your master will be empty at this point but it's fine as you have nothing to release at this point. Rememeber, master is supposed to always build.

More advance workflow can be followed by using - http://nvie.com/posts/a-successful-git-branching-model/

A tool to automate - https://github.com/nvie/gitflow



