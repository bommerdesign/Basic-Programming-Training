# Homework 1 
- Hint 1: create a bash file (`sh`) and use `echo` command.
----
- Hint 2: Set permission of bash file to can be execute. Because the homework required don't use `+x`, but we know that the numbers are a binary representation of the `x` string is `1`

---
Hint 3: Create a file homework1.sh and add the command `echo 'hello world'` to the file as below:

```sh
echo "echo 'hello world'" > homework1.sh
```

Final, to make sure it run for your user, you need to set it to read (4) and execute (1), mean that you will set file permission to `500`, run below command to set:

```bash
chmod 500 homework1.sh
```

Now, try to run the command `./homework.sh`

# Homework 2

## Homework 2.1

Hint 1: Use the command `mkdir` to create directories.

---

Hint 2: Use additional param with the command `mkdir`

---

Hint 3: Use additional param `p` (`p` is short for `--parents`. It creates the entire directory tree up to the given directory.), and the command will be:

```bash
mkdir -p  ~/tmp/tmp1/tmp2/tmp3/tmp4/tmp5
```

### Homework 2.3

Hint 1: Use the command to move `mv`, and move to same place with the folder want to rename

---

Hine 2: What we have to do that execute the command `mv tmp3 tmp3-sub`


### Homework 2.4

Hint: only one command `sudo reboot`

### Homework 2.5

Hint 1: You cannot use `gzip` command to compress a folder.

---

Hint 2: Should use `tar` command to compress a folder.

---

Hint 3: Execute the command below:

```bash
tar -zcvf tmp2.tar.gz tmp2/
```

`-c`: Create an archive.
`-z`: Compress the archive with gzip.
`-v`: Display progress in the terminal while creating the archive, also known as “verbose” mode. The `v` is  optional, but it’s helpful.
`-f`: Allows you to specify the filename of the archive.


### Homework 2.6

Hint: Is almost same with 2.5, but there is no param `z` (z: compress it using the gzip algorithm):

```bash
tar -cvf tmp3.tar tmp3/
```

### Homework 2.7

- Hint 1: The command `alias`, it will help you to change a command to your own command.

---

Hint 2: Define a command `ll` by using `alias` (`alias ll="ls -la"`)

---

Hint 3: In order to define one time and use everytime when open ternimal, let define it in the file `~/.bash_profile` following steps:

Open `.bash_profile` by command by `vim`:

```bash
vim ~/.bash_profile
```

Add below line to bottom of `.bash_profile`
```bash
alias ll="ls -la"
```

Reload (close and open) terminal again, try the command `ll`.

### Homework 2.8

Hint 1: You learned the command `echo`, you know that the command can output something on screen, but it also help you to write content to a file.

---

Hint 2: Using command `echo` with operator `>` help you output the content to a filee

---

Hint 3: Use below command to ouput content to a file, please note that char "`" is a special charactor, we need to add slashes "\" before them, and the command will be:

```bash
echo "If the first character is a \`-\` the item is a file, if it is a \`d\` the item is a directory. The rest of the string is three sets of three characters. From the left, the first three represent the file permissions of the owner, the middle three represent the file permissions of the group and the rightmost three characters represent the permissions for others. In each set, an \`r\` stands for read, a \`w\` stands for write, and an x stands for execute." > ~/tmp/test.txt
```
## Homework 3
Hint 1: use command `grep` to find a string

---

Hint 2: The basic grep command syntax is as follows:
```bash
grep 'word' filename
```
`word`: is the keyword that you want to find:
`filename`: the file that you want to search content inside it.

---

Hint 3: there is a param `-w` to search only for words, and the command will be:

```bash
grep -w 'character' ~/tmp/test.txt
```

## Homework 4

Hint 1: Use `grep` command in `Homework 3`, and mix it with one more command to count.

Hint 2: Using `tr` command, the `tr` command translates one string to another. So we translate all the spaces into a new line and then grep for the pattern.

Hint 3: Finally count the number of occurrences of the specific word by using the -c switch of grep for count and -i switch for ignoring the uppercase/lowercase word.

```
tr '[:space:]' '[\n*]' < ~/tmp/test.txt | grep -i -c character
```

The resule is `3`.
