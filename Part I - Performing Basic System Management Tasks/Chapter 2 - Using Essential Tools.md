# Chapter 2: Basic Shell Skills and Shell Environment

## Basic Shell Skills

- Before learning individual commands, it's important to understand how to interact with the shell environment.
- The shell interprets user input and executes commands, serving as the primary interface for system operations.
- Navigating directories, managing files, and controlling command behavior within the shell are foundational Linux skills.

### Understanding Commands

- Linux relies on the command line for most tasks.
- A command typically includes the command name, options, and arguments, entered at the shell prompt.
- General format: `command [options] [arguments]`.
- **Options**: Modify command behavior (e.g., `-l`, `--help`).
- **Arguments**: Specify targets like files or directories.
- Use `man <command>` to read manual pages.
- Frequent practice with commands builds fluency.

### Executing Commands

- You can define **aliases** to create shortcuts for frequently used commands.
- Syntax: `alias shortname='full command'`, e.g., `alias ll='ls -l'`.
- Use `alias` to view all current aliases and `unalias name` to remove them.

- Enter a command at the shell prompt and press Enter.
- The shell finds the command using paths listed in the `PATH` environment variable.
- Commands not found may be missing or outside `PATH`.
- Use relative (`./script.sh`) or absolute paths to run scripts.
- Ensure files are executable using `chmod +x filename`.
- Use arrow keys to recall command history.

### I/O Redirection

- Redirection changes input/output flow.
- `>` writes STDOUT to a file, overwriting.
- `>>` appends STDOUT to a file.
- `<` reads STDIN from a file.
- `2>` redirects STDERR.
- Use `&>` or `2>&1` to combine STDOUT and STDERR.

### Using Pipes

- Pipes (`|`) send output from one command to another as input.
- Example: `ls -l | less` for paginated output.
- Useful for filtering (`grep`), sorting (`sort`), etc.
- Each stage runs in a subprocess.

### History

- Access previous commands using up/down arrows.
- `history` lists stored commands.
- Use `!n` to run history line `n`; `!!` repeats last command.
- `history -c` clears the list.
- Stored in `~/.bash_history` across sessions.

- Use `alias` to list current aliases and `unalias name` to remove them.


- Tab completion simplifies input.
- Press Tab to auto-complete filenames, paths, and commands.
- Pressing Tab twice shows all possible completions.
- Configurable via `/etc/bash_completion.d/` scripts.

## Editing Files with vim

- `vim` is a modal text editor. It starts in command mode.
- Use `i`, `a`, or `o` to enter insert mode and type.
- Press `Esc` to return to command mode for navigation and commands.


[Intro omitted—non-substantive.]

## Understanding the Shell Environment

### Internal vs External Commands

- Internal commands are built into the shell itself (e.g., `cd`, `echo`, `alias`).
- External commands are separate binaries located in directories listed in `$PATH`.
- Use `type <command>` to determine whether a command is internal or external.


### Understanding Variables

- A **shell variable** exists only within the current shell session.
- An **environment variable** is inherited by child processes.


- Define variables using `NAME=value`.
- Access with `$NAME`, e.g., `echo $HOME`.
- Quote variables containing spaces: `"Hello world"`.
- Use `set` to list shell variables, `env` for environment.

### Recognizing Environment Configuration Files

- Shells load specific configuration files depending on whether they are login or non-login, interactive or non-interactive.


| File            | Context     | Purpose                                         |
| --------------- | ----------- | ----------------------------------------------- |
| ~/.bash_profile | Login shell | User-specific login initialization              |
| ~/.bashrc       | Interactive | User shell behavior (aliases, functions)        |
| /etc/profile    | Login shell | System-wide login environment                   |
| /etc/bashrc     | Interactive | System-wide settings for all interactive shells |

- Files are sourced automatically or manually using `source`.

### Using /etc/motd and /etc/issue

- `/etc/motd`: Message of the Day—shown at login.
- `/etc/issue`: Shown before login prompt, contains identification.
- Both are editable with any text editor.

## Finding Help

### Using --help

- Most commands support `--help` or `-h`.
- Shows basic syntax and option summary.

### Using man

- `man` displays detailed manuals.
- Use `/` to search, `q` to quit.

### Updating mandb

- Run `mandb` to update manual index.
- Required after installing new software.

### Using info

- `info` provides structured, linked manuals.
- Use `n`, `p`, `u`, and arrows for navigation.

### Using /usr/share/doc Documentation Files

- Contains READMEs, changelogs, examples.
- Useful when man/info pages are unavailable.

## Summary

- Understand commands, syntax, and input/output flow.
- Practice efficient shell use with history and tab completion.
- Configure environments using variables and startup files.
- Use built-in documentation resources (`--help`, `man`, `info`).

## Define Key Terms

- shell
- bash
- internal command
- $PATH
- STDIN
- STDOUT
- STDERR
- redirection
- file descriptor
- device file
- pipe
- environment variable
- login shell
- subshell

## vim Essential Commands

| Command       | Description                           |
| ------------- | ------------------------------------- |
| Esc           | Switch to command mode.               |
| i, a          | Enter input mode at/after cursor.     |
| o             | Open line below and enter input mode. |
| :wq           | Write changes and quit.               |
| :q!           | Quit without saving.                  |
| :w filename   | Save file with new name.              |
| dd            | Delete current line.                  |
| yy            | Copy current line.                    |
| p             | Paste copied/cut content.             |
| v             | Enter visual mode to select text.     |
| u             | Undo last change.                     |
| Ctrl-r        | Redo last undo.                       |
| gg            | Go to first line.                     |
| G             | Go to last line.                      |
| /text         | Search forward for 'text'.            |
| ?text         | Search backward for 'text'.           |
| ^             | Move to beginning of current line.    |
| $             | Move to end of current line.          |
| !ls           | Insert output of `ls` into file.      |
| :%s/old/new/g | Replace all 'old' with 'new'.         |

### man Sections of Interest

| Section | Description                     |
|---------|---------------------------------|
| 1       | Executable programs or commands |
| 5       | File formats and conventions    |
| 8       | System administration commands  |