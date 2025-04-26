Text files form the backbone of system configuration, user management, and automation in Linux. This chapter provides in-depth guidance on essential command-line tools and concepts for working with text in Red Hat Enterprise Linux (RHEL). From viewing and filtering to pattern matching and advanced editing, the skills developed here are foundational to professional system administration.

---

## Using Common Text File–Related Tools

### Doing More with *less*

- **Purpose:** Efficiently browse large files interactively without loading them entirely into memory.
- **Basic Usage:** `less filename`
- **Navigation Keys:**
  - `Space`, `Page Down`: Scroll down one screen.
  - `b`, `Page Up`: Scroll up one screen.
  - `/pattern`: Forward search.
  - `?pattern`: Reverse search.
  - `n`/`N`: Repeat search (same/opposite direction).
  - `g`/`G`: Go to start/end.
  - `q`: Quit.
  - `-N`: Show line numbers.
  - `-S`: Disable line wrapping.
- **Use Cases:** Viewing logs, configuration files, and long command outputs.
- **Comparison:** Unlike `more`, `less` allows reverse navigation and resembles `vim` and `man` behavior.

### Showing File Contents with *cat*

- **Purpose:** Display or concatenate file contents.
- **Usage Examples:**
  - `cat file`: Show file.
  - `cat file1 file2 > combined`: Merge into new file.
  - `cat file1 >> file2`: Append to existing file.
  - `cat > newfile`: Create via standard input.
- **Limitations:** Avoid using for very large files—prefer `less`.

### Displaying the First or Last Lines with *head* and *tail*

- **Purpose:** View a limited number of lines or bytes.
- **Basic Usage:**
  - `head -n 5 file`: Show first 5 lines.
  - `tail -n 20 file`: Show last 20 lines.
  - `tail -c 100 file`: Show last 100 bytes.
  - `tail -f /var/log/messages`: Live log viewing.
- **Use Cases:** Monitoring, troubleshooting, and file sampling.

### Filtering Specific Columns with *cut*

- **Purpose:** Extract character positions or delimited fields.
- **Syntax:**
  - `cut -d ':' -f 1 /etc/passwd`: First field.
  - `cut -c 1-10 file`: First 10 characters.
- **Notes:**
  - Fields are 1-indexed.
  - If the delimiter is not present, the line is returned unmodified.

### Sorting File Contents with *sort*

- **Purpose:** Alphabetically or numerically sort file content.
- **Examples:**
  - `sort -n numbers.txt`: Numeric sort.
  - `sort -r file`: Reverse order.
  - `sort -u file`: Remove duplicates.
  - `sort -t ':' -k 1 /etc/passwd`: Field sort.
- **Notes:** POSIX `sort` is unstable—equal lines may reorder unpredictably.

### Counting Lines, Words, and Characters with *wc*

- **Purpose:** Report line, word, byte, or character totals.
- **Options:**
  - `-l`: Line count.
  - `-w`: Word count.
  - `-c`: Byte count.
  - `-m`: Character count.
- **Example:** `grep error file | wc -l`: Count matching lines.

---

## A Primer to Using Regular Expressions

### Overview

Regular expressions (regex) define search patterns for strings. They are widely used in `grep`, `sed`, `awk`, and `vim`. Building from simple literal matches, this section covers anchors, escapes, wildcards, and extended expressions.

### Using Line Anchors

- `^`: Matches the start of a line.
- `$`: Matches the end.
- Example: `grep '^root' /etc/passwd`

### Using Escaping

- Special characters (e.g., `.` `*` `+`) require escaping with `\`.
- Example: `grep '\.conf' files` to match `.conf`.

### Using Wildcards and Multipliers

- `.`: Any character.
- `*`: Zero or more.
- `?`: Zero or one.
- `+`: One or more (requires extended regex).
- Example: `grep 'colou?r' file`: Matches "color" or "colour".

### Using Extended Regular Expressions

- Activate with `grep -E` or `egrep`.
- Extended operators:
  - `{n}`, `{n,}`, `{n,m}`: Repetition ranges.
  - `|`: Alternation.
  - `()` for grouping.
- Example: `grep -E '(foo|bar)+baz' file`

---

## Using `grep` to Analyze Text

- **Purpose:** Filter input by patterns.
- **Common Flags:**
  - `-i`: Ignore case.
  - `-v`: Invert match.
  - `-n`: Show line numbers.
  - `-r`, `-R`: Recurse directories (`-R` follows symlinks).
  - `-l`: Show matching filenames.
  - `-c`: Count matches.
- **Integration:** Often used in pipelines: `ps aux | grep ssh`

---

## Working with Other Useful Text Processing Utilities

### `tr`: Translate or Delete Characters

- `tr 'a-z' 'A-Z'`: Convert to uppercase.
- `tr -d 'aeiou'`: Remove vowels.
- Limitation: No regex support.

### `awk`: Field-Oriented Processing

- `awk -F: '{ print $1 }' /etc/passwd`: Extract usernames.
- Advanced: `awk 'BEGIN{total=0} /x/ {total+=$2} END{print total}' file`
- Supports full scripting syntax.

### `sed`: Stream Editing

- Basic: `sed 's/old/new/' file`
- In-place edit with backup: `sed -i.bak 's/x/y/' file`
- Ideal for quick substitutions or inline edits.

---

## Summary

- Core Linux tools like `less`, `cat`, `head`, `cut`, `sort`, `wc`, `grep`, `awk`, `sed`, and `tr` are critical for manipulating and interpreting text.
- Regular expressions elevate search accuracy and automation.
- Mastering these tools ensures efficiency in log analysis, configuration parsing, and scripting across RHEL systems.

---

## Define Key Terms

- **pager**
- **regular expression**
- **line anchor**
- **escaping**
- **wildcard**
- **multiplier**

