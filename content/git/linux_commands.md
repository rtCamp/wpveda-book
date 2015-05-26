#Linux Commands

TODO

1.	Setup local dev environment
2.	Useful linux commands

**find**

This command is used to search and locate list of files and directories based on different conditions specified for files that match the arguments. Find can be used by permissions, users, groups, file type, date, size etc. Example: Find all the files whose name is file-name.txt in a current working directory.

```bash
find . -name file-name.txt
```

Refer for more details: http://www.tecmint.com/35-practical-examples-of-linux-find-command/

**sed**

Refer for more details: http://www.tecmint.com/sed-command-to-create-edit-and-manipulate-files-in-linux/

**grep**

To find pdf files having word details and it should not contact copy word in it.

```bash
find . –name “*.pdf” | grep –i details | grep –vi "copy"
```

Find specific word in current directory,

```bash
grep -Hr "STRING" .
```

Find Database related details from wp-config.php file,

```bash
grep 'DB_NAME\|DB_USER\|DB_PASSWORD\|DB_HOST' wp-config.php
```

Refer for more details: http://www.tecmint.com/12-practical-examples-of-linux-grep-command/

1.	xargs
2.	parallel
3.	bg
4.	~~screen/tmux~~
5.	rsync
6.	ssh
7.	vim
8.	tail
9.	head

---

##Xargs

Reference: http://www.unixmantra.com/2013/12/xargs-all-in-one-tutorial-guide.html

---

##screen / tmux

screen and tmux are two terminal multiplexers. You can choose either one of them as both are doing same thing.

**why screen or tmux ?**

Screen is a full-screen software program that can be used to multiplexes a physical console between several processes (typically interactive shells). It offers a user to open several separate terminal instances inside a one single terminal window manager.

Ever ssh to remote server for long process ? say for example release a plugin to [wordpress.org](wordpress.org)? It is long process if your connection get broken in between you are in trouble without screen or tmux.

Login to remote via ssh firstly then follow these step.

---

### screen

**Installation**

```bash
sudo apt-get install screen
```

**Usage** To start screen just type `screen`

Execute your long lasting command here like,

```bash
sudo apt-get update && sudo apt-get upgrade
```

You can have more than one screen by `ctrl + a` and `c`.

To detach screen press `ctrl + a` then `d` this will continue running command in remote. so go grab a coffee or watch a movie if your process gonna take long time.

To list sessions: `screen -ls`

To attach `screen -r` and you will see that the process you left is still running.

you can use `exit` to terminate your screen.

for command line help in screen press `ctrl + a` then press `?`

For learning more on screen command visit this [link](http://www.tecmint.com/screen-command-examples-to-manage-linux-terminals/).

---

### tmux

**Installation**

```bash
sudo apt-get install tmux
```

**Usage**

To start tmux just type,

```bash
tmux

OR

tmux new -s mySessionName
```

Execute your long lasting command here like,

```bash
sudo apt-get update && sudo apt-get upgrade
```

You can have more than one session by `ctrl + b` and `c`.

To swich between session press `ctrl + b` then `p` for prevous and `n` for next.

To detach tmux press `ctrl + b` then `d` this will continue running command in remote.

To list sessions: `tmux ls`

To attach `tmux a  #  (or at, or attach)` attach to named `tmux a -t myname` And you will see that the process you left is still running.

You can use `exit` to terminate your tmux.

For command line help in screen press `ctrl + b` then press `?`

Watch [this video](https://www.youtube.com/watch?v=BHhA_ZKjyxo) for more tmux commands.

---

### rsync

rsync is a file transfer program capable of efficient remote update via a fast differencing algorithm.

**Usage**

```bash
rsync [OPTION] SRC DEST

OR

rsync [OPTION] SRC [USER@]HOST:DEST

OR

rsync [OPTION] [USER@]HOST:SRC DEST
```

*Recommanded Options*

```bash
-a, --archive `archive mode`
-v, --verbose `increase verbosity`
-z, --compress `compress file data during the transfer`
-h, --human-readable `output numbers in a human-readable format`
--progress `show progress during transfer`
```

For more help run `man rsync` OR `rsync --help` command in your terminal.

---

### ssh

ssh (SSH client) is a program for logging into a remote machine and for executing commands on a remote machine.

**Usage**

```bash
ssh [USERNAME]@[HOST]
```

```bash
Login to Remote server using specific port

ssh [USERNAME]@[HOST] -p [PORT]
```

For more help run `man ssh` or `ssh --help` command in your terminal.

---

### vim

Vim is a text editor that is upwards compatible to Vi. It can be used to edit all kinds of plain text.

**Usage**

```bash
vim /etc/hosts
```

Press `i` to insert / update text in file. To save changes press `esc` key on keyboard then press `:wq`.

`w` = save

`q` = quit

For more help run `man vim` command in your terminal.

---

### tail

Output the last part of files.

**Usage**

```bash
tail -f /path-to-log/error.log
```

For more help run `man tail` command in your terminal.

---

### head

Output the first part of files.

**Usage**

```bash
head /path-to-file/style.css
```

For more help run `man head` command in your terminal.
