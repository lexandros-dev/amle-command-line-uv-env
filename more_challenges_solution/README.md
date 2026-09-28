# More Challenges: Solutions and Explanations

The challenges are adapted from [The Bash Command Line](https://github.com/krother/bash_tutorial) by Dr. Kristian Rother ([CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)). See Credits and Licence in the [main README](../README.md#credits-and-licence).

This guide contains one possible solution for the optional More Challenges, and ends with an
[answer key](#recap-questions-answer-key) for the Recap Questions in the command line tutorial. Try each challenge independently before comparing your
commands with this guide.

The commands below assume that you begin in the repository root and create a
separate workspace:

```bash
mkdir -p more_challenges
cd more_challenges
```

Using a dedicated directory keeps your practice files separate from the
`bash_tutorial/` exercises.

## 1. The Locked Chest

### Create the chamber and file

```bash
mkdir secret_chamber
printf '%s\n' 'treasure' > secret_chamber/chest
ls -l secret_chamber/chest
```

`mkdir` creates a directory. The `printf` command produces a line of text, and
`>` redirects that line into a new file named `chest`. `ls -l` displays the
file permissions before they are changed.

### Lock and inspect the chest

```bash
chmod a-rw secret_chamber/chest
ls -l secret_chamber/chest
cat secret_chamber/chest
```

`chmod a-rw` removes read (`r`) and write (`w`) permissions for all users
(`a`). On a Unix-like system, `cat` should no longer be able to display the
file as a regular user.

> Git Bash on Windows might not enforce Unix file permissions in the same way.
> If the file remains readable there, continue with the remaining steps.

### Restore access and hide the directory

```bash
chmod u+r secret_chamber/chest
mv secret_chamber .secret_chamber
ls -a
cat .secret_chamber/chest
```

`chmod u+r` restores read permission for the owner (`u`). A name beginning
with `.` is hidden from a normal `ls` listing; `ls -a` includes hidden entries.
Moving the directory changes its name without changing the `chest` file inside
it.

## 2. Fruit Files

### Create sample files

```bash
mkdir fruit
touch fruit/apple fruit/banana fruit/grape fruit/kiwi fruit/lemon fruit/mango fruit/plum
ls fruit | sort > all_fruit.txt
cat all_fruit.txt
```

`touch` creates empty files. `ls fruit` lists the filenames, `sort` orders the
list alphabetically, and `>` stores that output in `all_fruit.txt`.

### Filter filenames containing `a`

```bash
grep 'a' all_fruit.txt
grep 'a' all_fruit.txt > fruit_with_a.txt
cat fruit_with_a.txt
```

`grep 'a'` prints only lines containing the letter `a`. Redirecting the output
creates a second file with only the matching filenames.

### Compare and count the results

```bash
diff all_fruit.txt fruit_with_a.txt
wc -l all_fruit.txt fruit_with_a.txt
```

Because `fruit_with_a.txt` is a filtered version of `all_fruit.txt`, the lines
marked as removed from the complete list by `diff` are filenames without an
`a`. `wc -l` counts lines, which gives the number of filenames in each file.

With the example filenames above, the fruit without `a` are:

```text
kiwi
lemon
plum
```

## 3. Message Generator Script

### Create an executable script

Create `hello.sh`:

```bash
cat > hello.sh <<'EOF'
#!/usr/bin/env bash

echo "Hello World"
EOF

chmod u+x hello.sh
./hello.sh
```

The first line, called a shebang, tells the system to execute the script with
Bash. `chmod u+x` gives the owner execute permission, and `./hello.sh` runs the
script from the current directory.

### Accept a command-line argument

Replace the contents of `hello.sh`:

```bash
cat > hello.sh <<'EOF'
#!/usr/bin/env bash

echo "$1"
EOF

./hello.sh "Hello World"
```

`$1` is the first argument supplied to the script. Quoting `"$1"` preserves
spaces in a message such as `Hello World`.

### Repeat messages and capture output

Create `repeat_messages.sh`:

```bash
cat > repeat_messages.sh <<'EOF'
#!/usr/bin/env bash

for number in 1 2 3 4 5; do
  ./hello.sh "Message ${number}"
done
EOF

chmod u+x repeat_messages.sh
./repeat_messages.sh > messages.txt
cat messages.txt
```

The `for` loop executes the commands between `do` and `done` once for each
number. `${number}` inserts the current number into the message. Redirecting
the script output writes the five generated lines into `messages.txt`.

Expected output:

```text
Message 1
Message 2
Message 3
Message 4
Message 5
```

## 4. Log Investigator

### Create a sample log file

```bash
cat > application.log <<'EOF'
INFO Server started
WARNING Cache nearing capacity
ERROR Database connection failed
INFO Retrying request
ERROR Database connection failed
ERROR Invalid user token
EOF
```

This here-document writes multiple lines to a file until the closing `EOF`
marker is reached.

### Filter and count errors

```bash
grep 'ERROR' application.log
grep -c 'ERROR' application.log
grep 'ERROR' application.log > errors.log
```

`grep` selects lines containing `ERROR`. The `-c` option reports how many
matching lines were found. The third command stores only those matching lines
in `errors.log`.

### Summarize repeated error lines

```bash
sort errors.log | uniq -c | sort -nr > error_summary.txt
cat error_summary.txt
```

The first `sort` groups identical lines together. `uniq -c` counts consecutive
matching lines, and `sort -nr` orders the result by count in descending numeric
order.

Expected output for the sample log:

```text
      2 ERROR Database connection failed
      1 ERROR Invalid user token
```

## Recap Questions: Answer Key

### What does `cd ..` do?

`cd` changes the current working directory. `..` represents the parent
directory, so `cd ..` moves one directory upward in the directory tree.

For example, from `/home/alex/projects`, running `cd ..` moves you to
`/home/alex`.

### What is the difference between `cd home/` and `cd /home`?

```bash
cd home/
```

uses a relative path. It looks for a directory named `home` inside the current
working directory.

```bash
cd /home
```

uses an absolute path. The leading `/` means it starts from the filesystem root
and navigates to the system directory `/home`, regardless of the current
working directory.

### What does `ls -la` display?

`ls` lists directory contents. The combined options change the display:

- `-l` uses the long format, including permissions, link count, owner, group,
  size, modification date, and filename.
- `-a` includes hidden entries whose names begin with `.`, including `.` for the
  current directory and `..` for its parent.

A line might begin with `-rw-r--r--`: the first character describes the entry
type, and the following characters show read, write, and execute permissions
for the owner, group, and others.

### How can you repeat the last command you entered?

Press the up arrow key to recall the previous command, then press Enter to run
it again. In Bash, `!!` also expands to and runs the previous command:

```bash
!!
```

Use `!!` with care because it executes immediately after expansion.

### When does TAB completion work?

TAB completion works when Bash can complete a command, filename, or directory
name from the characters already entered. For example, if `reports/` is the
only matching directory, typing `cd rep` and pressing Tab completes the name.

When several names match, Bash completes only their common prefix. Press Tab
again to display the available matches, then type more characters to narrow
the choice.

### How can you look up the documentation of Bash commands?

For many terminal programs, use a manual page or the program's built-in help:

```bash
man ls
ls --help
```

On macOS, some commands do not accept `--help`, but `man` works everywhere.

For Bash built-in commands, such as `cd`, use `help`:

```bash
help cd
```

The repository also includes the [Unix command cheat sheet](../Unix-Command-Cheatsheet.pdf)
for quick command lookup while working through the exercises.

## Cleanup

After completing or reviewing the challenges, remove the practice workspace
from the repository root:

```bash
cd ..
rm -r more_challenges
```

Use `rm -r` carefully: it deletes the directory and all of its contents.
