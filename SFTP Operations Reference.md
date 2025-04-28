## File Transfer Commands

- **put FILE** — Upload a specific file from the local machine to the remote server over a secure SSH channel.
  - Example: `put example.txt`
- **get FILE** — Download a specific file from the remote server to the local machine. Common for retrieving logs, backups, or configuration files.
  - Example: `get report.pdf`
- **mput PATTERN** — Upload multiple files matching a specified pattern, streamlining bulk file transfers.
  - Example: `mput *.jpg`
- **mget PATTERN** — Download multiple files matching a specified pattern to efficiently retrieve batches of data.
  - Example: `mget *.csv`

## Directory Navigation Commands

- **ls** — List the contents of the current remote directory, displaying files and folders.
  - Example: `ls`
- **cd DIR** — Change the working directory on the remote server.
  - Example: `cd /var/www/html`
- **lcd DIR** — Change the working directory on the local machine to better organize transfer operations.
  - Example: `lcd /home/user/Documents`
- **pwd** — Display the current remote directory path.
  - Example: `pwd`
- **lpwd** — Display the current local directory path.
  - Example: `lpwd`

## File and Directory Management Commands

- **mkdir DIR** — Create a new directory on the remote server for better file organization.
  - Example: `mkdir backups`
- **rmdir DIR** — Remove an empty directory on the remote server.
  - Example: `rmdir old_logs`
- **rm FILE** — Delete a file from the remote server to maintain storage hygiene.
  - Example: `rm oldfile.log`
- **chmod MODE FILE** — Modify the permissions of a remote file to enforce appropriate access controls.
  - Example: `chmod 600 secrets.txt`

## Session Management Commands

- **exit** — Safely terminate the SFTP session.
- **quit** — Alternate command to terminate the session.
- **help** — Display an in-session help listing all available SFTP commands.

---

# Best Practices and Advanced Features

## Wildcard Usage
Exercise caution when using wildcards like `mget *.txt`, as all matching files will be transferred automatically. Always run `ls` first to verify the targeted files.

## Tab Completion
Many SFTP clients support tab completion for file and directory names, which minimizes typographical errors and improves operational speed.

## Handling Interrupted Transfers
In networks prone to instability, use `reget` and `reput` to resume interrupted downloads or uploads rather than restarting transfers from scratch.

## Automating Transfers with Batch Mode
SFTP operations can be scripted using batch mode for automation:

1. Create a batch file (`batchfile.txt`) containing sequential SFTP commands:
    ```
    lcd /home/user/files
    cd /remote/dir
    mput *.jpg
    get report.pdf
    exit
    ```
2. Execute the batch file:
    ```bash
    sftp -b batchfile.txt user@host
    ```

Batch scripting significantly improves efficiency, especially for repetitive transfer tasks, while reducing human error.

## Permissions Management
After uploading files, always verify their permissions to restrict access appropriately, especially when handling confidential or critical information.

## Error Handling
Actively monitor file transfer outcomes. Investigate and address any errors immediately rather than assuming successful completion.

## Security Considerations
Whenever possible, use SFTP over a secured network channel such as a VPN. Additionally, prefer SSH key-based authentication over password-based methods to enhance security posture.

---

# Example SFTP Workflow

```bash
sftp user@server.com
lcd /home/user/downloads
cd /remote/files
mget *.tar.gz
exit
```

This workflow securely connects to `server.com`, changes the local working directory to `downloads`, navigates to `/remote/files` on the server, downloads all `.tar.gz` files, and exits the session cleanly.

> **Note:** Wildcards like `*.txt` offer powerful batch transfer capabilities, but always validate selections before proceeding with mass uploads or downloads to prevent unintended data movement.

---

# Final Overview

This comprehensive SFTP reference serves advanced users, network engineers, and system administrators aiming to master secure file transfer operations. It emphasizes best practices in automation, operational security, efficient navigation, error handling, and permission management—critical for maintaining robust and secure enterprise infrastructure workflows.

