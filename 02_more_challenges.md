# More Challenges

> [!NOTE]
> These challenges are adapted from [The Bash Command Line](https://github.com/krother/bash_tutorial) by Dr. Kristian Rother, published under the [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) licence. See [Credits and Licence](README.md#credits-and-licence) in the README.

These optional challenges practise the commands from the [Command Line Tutorial](01_command_line_tutorial.md).

Solutions for the optional challenges are provided in
[more_challenges_solution/README.md](more_challenges_solution/README.md).
Attempt the challenges first. If you get stuck, search for the relevant
command or consult the cheat sheet before using the solution guide to compare
commands and understand each step.

Complete these challenges in a new working directory so that you do not change
the tutorial exercise files:

```bash
mkdir more_challenges
cd more_challenges
```

## 1. The Locked Chest 🌶️

Practice creating files, changing permissions, and working with hidden
directories.

1. Create a directory named `secret_chamber/`.
2. Create a text file named `chest` inside it and store the word `treasure`.
3. Display the permissions of `chest`.
4. Remove read and write permission from `chest` for everybody.
5. Try to read the file and observe what happens.
6. Restore your read permission without recreating the file.
7. Rename `secret_chamber/` to `.secret_chamber/`.
8. List hidden directories and read the chest contents again.

> Note: Permission changes do not behave consistently in Git Bash on Windows.

---

## 2. Fruit Files 🌶️🌶️

Practice wildcards, redirection, text filtering, and file comparison.

1. Create a directory named `fruit/`.
2. Create seven empty files inside it named after fruit. Include some filenames
   with `a` and some without `a`.
3. Save an alphabetical list of all fruit filenames to `all_fruit.txt`.
4. Display only the filenames containing the letter `a`.
5. Save the matching filenames to `fruit_with_a.txt`.
6. Use `diff` to determine which filenames do not contain an `a`.
7. Count the total number of fruit files and the number that contain an `a`.

---

## 3. Message Generator Script 🌶️🌶️🌶️

Practice script creation, command-line arguments, executable permissions, and
loops.

1. Write a Bash script named `hello.sh` that prints `Hello World`.
2. Make the script executable and run it.
3. Modify `hello.sh` so it prints a message supplied as the first command-line
   argument, available as `$1`.
4. Test the script with the message `Hello World`.
5. Write another script named `repeat_messages.sh` that calls `hello.sh` five
   times with numbered messages.
6. Run `repeat_messages.sh` and redirect its output into `messages.txt`.
7. Display `messages.txt` to verify that all five lines were created.

---

## 4. Log Investigator 🌶️🌶️🌶️

Practice searching text and building a small terminal report.

1. Create a file named `application.log` containing at least six lines. Include
   lines with the words `INFO`, `WARNING`, and `ERROR`, and repeat at least one
   error message.
2. Display only lines containing `ERROR`.
3. Count the number of error lines.
4. Save the error lines to `errors.log`.
5. Produce a sorted list of unique error lines with their occurrence counts.
6. Save that summary to `error_summary.txt` and display it.

---

Next, continue with [Python Environments with uv](03_python_environments_with_uv.md).
