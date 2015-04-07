# Linux Commands

TODO

1. Setup local dev environment
2. Useful linux commands

Command:
1. Find: This command is used to search and locate list of files and directories based on different conditions specified for files that match the arguments. Find can be used by permissions, users, groups, file type, date, size etc.
Example: Find all the files whose name is file-name.txt in a current working directory.
```
find . -name file-name.txt
```
Refer for more details: http://www.tecmint.com/35-practical-examples-of-linux-find-command/

2. sed
Refer for more details: http://www.tecmint.com/sed-command-to-create-edit-and-manipulate-files-in-linux/

3. grep
Example: To find pdf files having word details and it should not contact copy word in it.
```
find . –name “*.pdf” | grep –i details | grep –vi “copy”
```
Refer for more details: http://www.tecmint.com/12-practical-examples-of-linux-grep-command/

4. xargs
5. parallel
6. bg
7. screen/tmux
