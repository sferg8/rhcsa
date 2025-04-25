This chapter provides an extensive examination of file management in Red Hat Enterprise Linux (RHEL), emphasizing the operational and conceptual competencies necessary for successful system administration. These skills are central to many tasks encountered in both practical environments and certification scenarios, particularly the RHCSA (Red Hat Certified System Administrator) exam. This chapter builds upon foundational shell usage principles and advances into structured file and directory navigation, manipulation techniques, link management, data compression, and file archival practices using native Linux utilities.

Mastering these topics enables administrators to manage resources efficiently, perform automated operations, and maintain systems with precision and scalability. The consistent use of command-line tools enhances repeatability and supports broader scripting and configuration management practices.

---

## Working with the File System Hierarchy

Linux systems adopt a hierarchical file system structure where all paths originate from the root directory (`/`). This layout resembles an inverted tree, with directories branching downward. Efficient use of this structure facilitates reliable navigation and resource access.

### Defining the File System Hierarchy

The **Filesystem Hierarchy Standard (FHS)** defines and standardizes the layout of the Linux directory structure across distributions. This consistency ensures software compatibility and administrative predictability.

Important directories include:
- `/bin`, `/sbin`: Contain essential user and administrative binaries needed during boot and recovery.
- `/etc`: Hosts configuration files critical to system setup.
- `/dev`: Represents devices as files for programmatic access.
- `/proc`, `/sys`: Interface with kernel and process data as pseudo-filesystems.
- `/usr`, `/var`: Store user applications, logs, and variable runtime data.
- `/tmp`, `/home`, `/root`: Manage temporary and user-specific content.
- `/media`, `/mnt`: Designated for temporary or manually mounted filesystems.
- `/lib`, `/lib64`: Store shared libraries required by essential binaries.

Familiarity with this structure is essential for secure configuration, file retrieval, and service troubleshooting.

### Understanding Mounts

Mounting is the process of integrating additional filesystems into the main directory hierarchy. Mount points serve as access gateways for these filesystems.

Key tools and concepts:
- `mount`, `umount`: Attach/detach filesystems.
- `df -h`, `findmnt`: Inspect mount status and disk usage.
- `/etc/fstab`: Defines persistent mounts across reboots.

Common filesystem types:
- `ext4`, `xfs`: Native Linux filesystems.
- `vfat`, `ntfs`: Used for external and Windows-compatible devices.
- `nfs`: Supports network-based storage sharing.

Persistent and temporary mounts allow integration of various storage types, enabling scalable resource allocation and modular storage design.

---

## Managing Files

Effective file management is critical to operational efficiency and script automation. Key commands include `cp`, `mv`, `rm`, `mkdir`, and `rmdir`. These facilitate organized storage, logical structuring, and controlled modification or removal.

### Working with Wildcards

Wildcards allow flexible pattern matching:
- `*`: Matches any string of characters.
- `?`: Matches a single character.
- `[ ]`: Matches specified characters or ranges.

Escaping wildcards (e.g., `\*`) allows literal usage. Wildcards are interpreted by the shell before command execution, optimizing batch operations across multiple files or directories.

### Managing and Working with Directories

Administrators use directory commands for creating, removing, and navigating nested structures:
- `mkdir -p`: Creates directory trees in one step.
- `rmdir`, `rm -r`: Remove directories conditionally or recursively.
- `ls -d */`: Filters output to show only subdirectories.

Proper directory layout supports access control, backups, and logical resource grouping.

### Working with Absolute and Relative Pathnames

- **Absolute paths** begin with `/` and specify full location.
- **Relative paths** start from the current working directory.

Navigation tokens include:
- `.`: Current directory
- `..`: Parent directory

Understanding path types is essential for accurate scripting and command execution.

### Listing Files and Directories

`ls`, `stat`, and `file` commands provide insights into file attributes, types, and metadata. Use `du -sh *` to summarize storage usage.

These tools assist in diagnostics, resource planning, and permissions auditing.

### Copying Files and Directories

Use `cp` to duplicate data. Options include:
- `-r`: Recursive
- `-a`: Archive (preserve attributes)
- `-v`, `-u`: Verbose and update-only modes

This command supports both safety and efficiency when cloning data structures or creating backups.

### Moving Files and Directories

`mv` renames or relocates files. Options:
- `-i`: Interactive
- `-u`: Update
- `-v`: Verbose

Moving files between filesystems triggers a copy-delete sequence. Plan accordingly when handling large data sets.

### Deleting Files and Directories

`rm` and `unlink` permanently remove content. Use `-r`, `-f`, and `-i` for recursive, forced, and interactive deletion.

Deletion is irreversible. Administrators should verify targets with `ls` or `stat` before proceeding.

---

## Using Links

Links facilitate flexible file referencing. Linux supports two types:

### Understanding Hard Links

Hard links share inodes, making them indistinguishable. They are limited to the same filesystem and cannot link directories.

### Understanding Symbolic Links

Symlinks point by name to targets and can span filesystems or directories. They break if the target is moved or deleted.

### Creating Links

- `ln fileA fileB`: Creates a hard link.
- `ln -s target link`: Creates a symbolic link.

Use `ls -li` or `ls -l` to confirm link creation.

### Removing Links

Remove links with `rm` or `unlink`. Removing the last hard link frees inode storage. Removing a symlink leaves the original untouched.

---

## Working with Archives and Compressed Files

Archiving and compression consolidate data for storage or transfer. `tar` is the primary archiving utility.

### Managing Archives with tar

- `-c`, `-x`, `-t`: Create, extract, list
- `-v`: Verbose mode
- `-f`: Specify archive file

`tar` is frequently paired with compression.

### Creating Archives with tar

Use `tar -cf archive.tar files/` or `tar -cvf archive.tar files/` for verbose output. Structure and permissions are retained.

### Monitoring and Extracting tar Files

- `tar -tf archive.tar`: Preview contents
- `tar -xf archive.tar`: Extract
- `tar -xf archive.tar -C /path`: Extract to specified directory
- `--wildcards`: Enable pattern-based extraction

### Using Compression

Compression tools:
- `gzip` → `.gz`
- `bzip2` → `.bz2`
- `xz` → `.xz`

Combined commands:
- `tar -czvf`: Gzip-compressed tarball
- `tar -cjvf`: Bzip2-compressed
- `tar -cJvf`: XZ-compressed

Compression reduces archive size and is essential for backups and network transfers.

---

## Summary

- A structured hierarchy and core file operations are foundational for Linux system management.
- Commands like `cp`, `mv`, `rm`, `ln`, `tar`, and navigation tools are critical.
- Mastery of wildcards, links, archives, and compression supports automation, configuration management, and secure administration workflows.

---

## Define Key Terms

- **Filesystem Hierarchy Standard (FHS)**: Linux directory structure convention
- **absolute pathname**: Complete file path from `/`
- **archive**: A unified file combining multiple files
- **compression**: Size reduction using `gzip`, `bzip2`, `xz`
- **device file**: Interface file for hardware in `/dev`
- **directory**: Organizational file container
- **file**: Basic data storage unit in Linux
- **file type**: Classification (regular, directory, link)
- **filesystem hierarchy**: Structured tree of directories and files
- **hard link**: File that shares inode with another
- **inode**: Data structure containing file metadata
- **mount point**: Directory where a filesystem is attached
- **pathname**: Full or relative location string of a file
- **recursive**: Operation that applies to contents of a directory and subdirectories
- **relative pathname**: Location relative to current working directory
- **soft link (symbolic link)**: Named pointer to another path
- **tar**: Utility for bundling multiple files into one archive
- **gzip**: Compression tool that creates `.gz` files
- **bzip2**: Compression tool for `.bz2` format
- **xz**: High-ratio compression utility
- **wildcard**: Character pattern for filename matching
- **working directory**: Current directory in shell session (`pwd`)

