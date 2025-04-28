cp file /tmp and cp file /tmp/ behave identically if /tmp is a directory. But here are the rules:

If destination is an existing directory (with or without /), the file is copied into it:
cp file /tmp → /tmp/file
cp file /tmp/ → /tmp/file

If destination is a nonexistent path without trailing slash, cp treats it as a file rename:
cp file /tmp → creates /tmp (as file) only if /tmp does not exist

If destination has a trailing slash but doesn't exist, it's an error:
cp file /tmp/ → error: /tmp/ not found

Get to know tar and compression adding and removing specfic files
echo b > /proc/sysrq-trigger
Here’s the full important /proc/sysrq-trigger key table:


Key	Action
b	Immediate reboot (no sync, no clean shutdown).
o	Power off immediately (if supported by hardware).
s	Sync all mounted filesystems (flush to disk).
u	Remount all filesystems read-only (protects from corruption).
e	Send SIGTERM to all processes except PID 1 (try graceful shutdown).
i	Send SIGKILL to all processes (force kill).
l	Kill everything but init (leaves only PID 1 alive).
c	Crash the system (panic) — triggers kernel crash dump if configured.
m	Dump current memory info to console.
t	Dump current tasks/processes to console.
p	Dump current CPU registers and flags to console.
h	Help (list available commands).
Example full safe sequence to reboot a locked system cleanly:

bash
Copy
Edit
echo s > /proc/sysrq-trigger   # Sync disks
echo u > /proc/sysrq-trigger   # Remount read-only
echo b > /proc/sysrq-trigger   # Hard reboot
sed -i -e '1d' known_hosts 
