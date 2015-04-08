#.gitignore file

During development, We have some file and folders which you don't want to push on git. Simple way to tell git to ignore those files and folders is .gitignore file

## How to create .gitignore file

you can create .gitignore file for diffrent scop

### Global .gitignore file

Global .gitignore file contains rules for ignoring files and folders in every Git repositories on your computer.

Create a global .gitignore file

1. Open terminal

2. Create a gitignore file. Here gitignore file name is **.gitignore_global** and it located at **~/**
```
vim ~/.gitignore_global
```

3. Add rule into .gitignore_global file and save it.

4. set the above .gitignore file as global .gitignore file using below command
```
git config --global core.excludesfile ~/.gitignore_global
```
" ~/.gitignore_global " is a path of global gitignore file

### local .gitignore file
local .gitignore file unsed to ignore file for single git repository. it must be located into your git repository.
.gitignore file should be committed into your repository to share with other user.

Create a local .gitignore file

1. open terminal and navigate to the location of git repository

2. Create a .gitignore file. Here .gitignore file name is **.gitignore**
```
vim .gitignore
```

3. Add rule into .gitignore file and save it.

**note:** Git will not ignore the file if you add a rule later. In those case, you need to untrack those files with use of below command
```
git rm --cached
```

### Example of .gitignore file
```
### Sass ###
.sass-cache

### Bower ###
bower_components
.bower-cache
.bower-registry
.bower-tmp

### PhpStorm ###
## Directory-based project format:
.idea/

# GitBook build output
_book

### NetBeans ###
nbproject/private/
build/
nbbuild/
dist/
nbdist/
nbactions.xml
nb-configuration.xml
.nb-gradle/

### Node ###
# Logs
*.log

# Dependency directory
node_modules

```

For gitignore rule visit https://www.gitignore.io/

