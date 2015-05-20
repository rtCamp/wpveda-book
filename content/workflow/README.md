# Workflow

Complete workflow for day-to-day WordPress development.

## Setting up local dev env

Depending on OS, dev tools to be installed locally.

## Start a new project

Be it WordPress theme or plugin, free or paid, we will be using a git repo.

1. For public project, github.com is good
2. For private project, you can use paid account on github.com or use gitlab.com

No matter where you host your git repo, on local you will be doing:

1. git clone git://remote-path local-dir
2. cd local-dir
2. atom . #launch editor

### TODO - for new project

1. plugin or theme folder structure
2. grunt task setup
3. scaffolding
4. composer


## Test Driven Development

1. Write test cases
2. Write code that meets those test cases
3. Run test cases
4. git commit
5. git push

### TODO

1. `npm version` alternative for git. Something like `git version minor|major|patch`.
2. git hooks to run test on `git commit` and/or `git push`


### Code Checks

1. Coding Standard - phpcs, jshint, css, etc
2. Code Quality - phpmd, copy-paste detector, etc
3. Unit test cases - phpunit, js (not sure)
4. Functional testing (e2e - end to end tetsing) - using selenium + nightwatch, etc

## Continuous Integration

1. build script (testing)
2. deploy script (cleanup, packaging, delivery, publish)
