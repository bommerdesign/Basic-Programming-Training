# Exercise and Homework

## Exercise

### Problem
Imagine that you have to use linux command download latest verion of below documents and move them to a folder named `specs` everyday:
- Document 1: https://raw.githubusercontent.com/pa-vuhn/HTML-Tut/html-css-js/exercises/readme.md
- Document 2: https://raw.githubusercontent.com/pa-vuhn/HTML-Tut/html-css-js/exercises/tut1.md

How to do it with only one command to reduce our effort?

### Solution
- Write a script to do all tasks and we only execute the script.

First, make a folder `~/workspace` to contain all your exercise by following command:

```sh
# Goto home folder
cd ~
# Make folder workspace under home folder
mkdir -p ~/workspace
# Goto folder workspace
cd workspace
```

### The problem if we have no script

**If we don't make script to do it automatically, we have to do below command everyday**

Create a foler named `specs`:

```bash
mkdir -p specs
```

Download file https://raw.githubusercontent.com/pa-vuhn/HTML-Tut/html-css-js/exercises/readme.md and move it to `specs` by commands:

```sh
# Download file
wget https://raw.githubusercontent.com/pa-vuhn/HTML-Tut/html-css-js/exercises/readme.md

# Move to folder specs
mv readme.md specs
```

We also do almost same command to download file https://raw.githubusercontent.com/pa-vuhn/HTML-Tut/html-css-js/exercises/tut1.md and move this document to folder `specs`

```sh
# Download file
wget https://raw.githubusercontent.com/pa-vuhn/HTML-Tut/html-css-js/exercises/tut1.md

# Move to folder specs
mv tut1.md specs
```
**Above way will take too much effort, we will make a script to do all the command**

### Make Script

Now, create a script named `update-daily.sh`, and put all above commands into the file, the content of `update-daily.sh` will be:

```sh
# create specs folder
mkdir -p specs

# Download file readme.md
wget https://raw.githubusercontent.com/pa-vuhn/HTML-Tut/html-css-js/exercises/readme.md
# Move readme.md to folder specs
mv readme.md specs

# Download file tut1.md
wget https://raw.githubusercontent.com/pa-vuhn/HTML-Tut/html-css-js/exercises/tut1.md

# Move tut1.md to folder specs
mv tut1.md specs
```

Try to run `update-daily.sh`
```sh
./update-daily.sh
```

You will get message like below, because file `update-daily.sh` have no persmission to execute:

```txt
permission denied:
```

Therefore, let set the execute permission for it. Note that with script file, we also need read permission for execute
```sh
cd ~/workspace
chmode +rx update-daily.sh # add execute permission
```

Run the command `./update-daily.sh` again, and check result in `~/workspace/specs`

## Homeworks

1. (Easy: 10 min) create a bash file that print some content (example hello world!). Set its permission to able to execute (execute permission, do not use +x as above)
2. (Easy: 30 min) Using commands
   - 2.1 Open your Visual Studio Code and use kill command to kill it
   - 2.2 Create below directory from your home directoy `~/tmp/tmp1/tmp2/tmp3/tmp4/tmp5` (just use only 1 command and use 1 times to create all folder)
   - 2.3 Rename directory `tmp3` to `tmp3-sub`
   - 2.4 Restart your computer
   - 2.5 Create a zip file for folder `tmp2`
   - 2.6 Create tar file for folder `tmp3`
   - 2.7 Create a custom command `ll` to do the task similar with `ls -la`. It means, when I input `ll` and enter in the termial window, the result is the same when i enter `ls -la`. (Remember, Just setup 1 time, and you can do it everytime when open the termial window)
   - 2.8 Create a file in `~/tmp/test.txt` and put below content inside test.txt by `just 1 command and 1 time`

  If the first character is a `-` the item is a file, if it is a `d` the item is a directory. The rest of the string is three sets of three characters. From the left, the first three represent the file permissions of the owner, the middle three represent the file permissions of the group and the rightmost three characters represent the permissions for others. In each set, an `r` stands for read, a `w` stands for write, and an x stands for execute.

3. (Easy: 10 min) Find the word `character` in `/tmp/test.txt` file.
4. (Medium: 15 min) Print to console (terminal console) the Count of the `character`, how many words Occurrences
