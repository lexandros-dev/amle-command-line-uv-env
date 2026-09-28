# The Command Line and Python Environments

<table>
  <tr>
    <td align="center" width="50%">
      <img src="assets/tux.png" alt="Tux, the Linux penguin" height="220">
      <br>
      <em>Tux, the Linux penguin: your guide to the command line.</em>
    </td>
    <td align="center" width="50%">
      <a href="https://xkcd.com/1987/"><img src="https://imgs.xkcd.com/comics/python_environment.png" alt="xkcd comic 1987, Python Environment: a tangle of arrows between many different Python installations on one laptop" height="220"></a>
      <br>
      <em>What happens without environments. <a href="https://xkcd.com/1987/">xkcd 1987</a> by Randall Munroe.</em>
    </td>
  </tr>
</table>

A hands-on introduction to the two tools you use every day in this course: the **bash command line** and **uv**. First you work through six short command line exercises, each hiding part of a 17-character word, so every command you get right brings you closer to the solution. Then you build a Python project with `uv` from nothing, break its environment on purpose, and rebuild it, so that the `uv sync` at the start of every course repository means something to you.

## Learning Objectives

By the end of this repository, you should be able to:

- Navigate a directory tree with `cd` and `ls`, reveal hidden files with `ls -a`, and read file sizes and permissions with `ls -l`.
- View, edit, create, copy and remove files and directories with `less`, `nano`, `mkdir`, `cp`, `rm` and `rmdir`.
- Compare files with `diff`, search them with `grep`, and unpack `.zip`, `.tar` and `.gz` archives.
- Make a script executable with `chmod +x`, and follow how it chains commands together with a pipe.
- Create a project with `uv`, add and remove dependencies, and run code inside its environment with `uv run`.
- Locate what `pyproject.toml`, `uv.lock`, `.python-version` and `.venv/` each hold, and rebuild a deleted environment with `uv sync`.

## Learning Path

Work through the files in this order:

| File | Description |
| --- | --- |
| [**01 - Command Line Tutorial**](01_command_line_tutorial.md) | Six exercises on directories, text files, copying and removing, comparing files, archives, and permissions, each revealing part of the hidden word. |
| [**02 - More Challenges**](02_more_challenges.md) | Four optional challenges of rising difficulty that combine the commands into small tasks and scripts. |
| [**03 - Python Environments with uv**](03_python_environments_with_uv.md) | Create a project with `uv`, add dependencies, then delete the environment and rebuild it with `uv sync`. |

### Additional Folders and Files

| File / Folder | Description |
| --- | --- |
| [**Exercise Files**](bash_tutorial/) | The directories and files you explore in the tutorial exercises. |
| [**Unix Command Cheat Sheet**](Unix-Command-Cheatsheet.pdf) | A one-page summary of common commands to keep open while you work. |
| [**Solutions**](more_challenges_solution/) | One possible solution for each of the More Challenges, and the answer key for the Recap Questions, with explanations. |
| [**Assets**](assets/) | Images and diagrams used in the command line tutorial and the Python environments exercise. |

## Setup

> [!NOTE]
> Throughout these steps, text in angle brackets like `<repo-name>` is a **placeholder**. Replace it, including the `< >` brackets, with your own value. For example, `cd <repo-name>` becomes `cd my-command-line`.

### 1. Create the Repository from the Template

Click **Use this template** on GitHub.

When creating the repository:

- Set yourself as the **Owner**
- Choose a repository name
- Disable **Include all branches**
- Click **Create repository**

---

### 2. Clone the Repository

Open a terminal. On Windows, use **Git Bash**. Copy the SSH URL from the **Code** button on GitHub, then run:

```bash
git clone <copied-ssh-url>
```

The copied SSH URL will look like `git@github.com:<your-username>/<repo-name>.git`.

---

### 3. Check uv Is Installed

`uv` is installed as part of the [Environment Setup Guide](https://neuefische.github.io/ds-installation/). Check it is there:

```bash
uv --version
```

If that fails, go back to the setup guide for your operating system before starting.

---

### 4. Move into the Exercise Folder

```bash
cd <repo-name>/bash_tutorial
```

Then open the [Command Line Tutorial](01_command_line_tutorial.md) and start with its first exercise.

## References & Further Reading

- [**The Bash Command Line (original tutorial)**](https://github.com/krother/bash_tutorial): Kristian Rother's tutorial that this repository is adapted from.
- [**The Unix Shell (Software Carpentry)**](https://swcarpentry.github.io/shell-novice/): A step-by-step lesson on the shell for researchers and data scientists.
- [**The Linux Command Line**](https://linuxcommand.org/tlcl.php): William Shotts' free book, from the first commands to writing shell scripts.
- [**The Missing Semester: The Shell**](https://missing.csail.mit.edu/2020/course-shell/): MIT's lecture on using the shell well in everyday programming work.
- [**uv documentation**](https://docs.astral.sh/uv/): The official guide, including the project workflow used in the Python environments exercise.
- [**explainshell**](https://explainshell.com/): Paste any command to see what each part of it does.
- [**Git for Windows**](https://gitforwindows.org/): The Git Bash terminal for running these exercises on Windows.

---

## Credits and Licence

The command line tutorial and the More Challenges section are adapted from
[**The Bash Command Line**](https://github.com/krother/bash_tutorial), © 2024 Dr. Kristian Rother, published under the
[Creative Commons Attribution-ShareAlike 4.0 International licence (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/).
Thank you to Kristian Rother for making the tutorial openly available.

The Python environments exercise is written for this course and is not part of the original tutorial.

The comic [Python Environment](https://xkcd.com/1987/) at the top of this page is by Randall Munroe, published on xkcd under the [Creative Commons Attribution-NonCommercial 2.5 licence](https://creativecommons.org/licenses/by-nc/2.5/). It is displayed from xkcd.com and is not part of this repository or its licence. Tux, the Linux penguin, was drawn by Larry Ewing using The GIMP.

Changes from the original: the text is reworked for this course, the exercises are
reorganised and hide a different solution word, the challenges are rewritten, and the
Log Investigator challenge and the solutions guide are new.

As the original licence requires, this adapted tutorial is shared under the same
licence, [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).
