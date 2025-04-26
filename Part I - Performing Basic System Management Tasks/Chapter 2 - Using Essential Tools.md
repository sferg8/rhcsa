## Basic Shell Skills

- Before diving into individual commands, it is essential to understand how to interact with the Linux shell, the core tool for managing and controlling system behavior.
- The shell acts as an intermediary between the user and the operating system, translating user input into system actions.
- Mastering shell navigation, file manipulation, and command execution is crucial for system administration and troubleshooting tasks.

### Understanding Commands

- Linux systems heavily rely on the command line interface (CLI) for administrative and operational tasks.
- A typical command entered at the shell prompt consists of a command name, followed optionally by options and arguments.
- Syntax: `command [options] [arguments]`.
- **Options** modify how a command behaves, using short (`-l`) or long (`--help`) formats.
- **Arguments** specify the target resources, such as files or directories, the command operates upon.
- Manual pages (`man <command>`) provide detailed documentation on command usage.
- Regular command practice improves familiarity and system management skills.

### Executing Commands

- To run a simple command, use `echo "Hello, World!"` to print text to the terminal.
- To list directory contents, use `ls -l /etc` to display detailed information about files.
- To run a script, use `./myscript.sh`, ensuring it has execute permissions.
- **Aliases** simplify repeated tasks: define with `alias shortname='full command'` (e.g., `alias ll='ls -l'`).
- View current aliases with `alias` and remove them with `unalias name`.
- Commands are entered at the prompt and executed when pressing Enter.
- The shell locates commands based on the directories listed in the `PATH` environment variable.
- Use relative paths (`./script.sh`) or absolute paths to execute scripts.
- Grant execution permission with `chmod +x filename`.
- Navigate command history with the up and down arrows.

### I/O Redirection

- Redirection controls where input is read from and where output is written.
- `>` redirects standard output (STDOUT) to overwrite a file.
- `>>` appends STDOUT to the end of an existing file.
- `<` redirects standard input (STDIN) from a file.
- `2>` redirects standard error (STDERR) to a file.
- `&>` or `2>&1` combines STDOUT and STDERR into a single stream.
- Redirection is essential for scripting, output management, and debugging.

### Using Pipes

- Pipes (`|`) pass the output of one command as input to another.
- Example: `ls -l | less` paginates a directory listing.
- Use `ps aux | grep ssh` to list SSH-related processes.
- Use `cat /etc/passwd | sort` to alphabetically sort entries.
- Combine commands: `dmesg | grep error | sort | uniq` to find unique system errors.
- Each command in a pipeline runs as a separate subprocess.

### History

- Recall commands using the up/down arrows.
- List previous commands with `history`.
- Re-run a command with `!n` or repeat the last with `!!`.
- Delete a specific entry with `history -d <line_number>`.
- Clear the entire history with `history -c`.
- The Bash history file (`~/.bash_history`) preserves past sessions.
- Tab completion automatically finishes filenames, commands, and arguments.
- Press Tab once to complete, twice to view options.
- Bash uses completion scripts stored in `/etc/bash_completion.d/` for extended behavior.

## Editing Files with vim

- `vim` is a modal text editor widely used for editing configuration files and scripts.
- Upon opening a file, vim starts in command mode.
- Enter insert mode with `i`, `a`, or `o` to type text.
- Return to command mode by pressing `Esc`.
- Mastering vim’s modes improves file editing speed and accuracy.

## Understanding the Shell Environment

### Internal vs External Commands

- **Internal commands** are built into the shell (e.g., `cd`, `echo`, `alias`).
- **External commands** are separate executables found in directories defined by `PATH`.
- Use `type <command>` to determine if a command is internal or external.

### Understanding Variables

- Define variables with `NAME=value` and retrieve them with `$NAME`.
- Example: `greeting="Hello World"` and `echo $greeting`.
- Promote shell variables to environment variables with `export NAME=value`.
- View variables with `set` (shell) or `env` (environment).

### Recognizing Environment Configuration Files

| File             | Context              | Purpose                                         |
|------------------|----------------------|-------------------------------------------------|
| ~/.bash_profile  | Login shell session   | User-specific environment initialization        |
| ~/.bashrc        | Interactive shell     | Aliases, functions, and general user settings   |
| /etc/profile     | System login session  | System-wide environment settings for logins     |
| /etc/bashrc      | System interactive    | System-wide settings for interactive sessions   |

- Apply changes manually using `source filename` or `. filename`.
- Understanding these files ensures consistent and predictable shell behavior.

### Using /etc/motd and /etc/issue

- `/etc/motd` shows login messages post-authentication.
- `/etc/issue` displays pre-login system information.
- Administrators can edit these with `vim` or `nano` to communicate policies or notices.

## Finding Help

### Using --help

- Access basic usage info with `--help` or `-h`.
- Useful for quick reference without opening full manuals.

### Using man

- `man` pages offer detailed documentation organized into sections.
- Search inside man pages with `/term`, navigate with `Space` and `b`, and exit with `q`.

### Updating mandb

- Run `mandb` to update the manual page database after new software installation.

### Using info

- `info` offers hierarchical, hyperlinked documentation.
- Navigate using `n`, `p`, `u`, and arrow keys.

### Using /usr/share/doc Documentation Files

- `/usr/share/doc` stores supplementary package documentation such as READMEs and changelogs.
- View files using tools like `less` or `cat`.

## Summary

- Master basic command usage, redirection, pipes, and file editing.
- Utilize history, aliases, and tab completion for productivity.
- Configure environments through variables and startup files.
- Leverage `--help`, `man`, `info`, and `/usr/share/doc` to solve problems and learn independently.

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

| Command       | Description                                                     |
|---------------|-----------------------------------------------------------------|
| Esc           | Switch to command mode.                                         |
| i, a          | Enter insert mode at or after the cursor.                       |
| o             | Open a new line below and enter insert mode.                    |
| :wq           | Save changes and exit vim.                                      |
| :q!           | Exit vim without saving changes.                                |
| :w filename   | Save the file under a new filename.                             |
| dd            | Delete the current line.                                        |
| yy            | Copy (yank) the current line.                                    |
| p             | Paste yanked or deleted content.                                |
| v             | Enter visual mode for selecting text.                           |
| u             | Undo the last action.                                           |
| Ctrl-r        | Redo the last undone change.                                    |
| gg            | Move the cursor to the beginning of the file.                   |
| G             | Move the cursor to the end of the file.                         |
| /text         | Search forward for "text".                                      |
| ?text         | Search backward for "text".                                     |
| ^             | Move to the beginning of the current line.                      |
| $             | Move to the end of the current line.                            |
| !ls           | Insert the output of the `ls` command into the current file.     |
| :%s/old/new/g | Replace all instances of 'old' with 'new' globally in the file. |

### man Sections of Interest

| Section | Description                     |
|---------|---------------------------------|
| 1       | Executable programs and commands|
| 5       | File formats and conventions    |
| 8       | System administration commands  |

