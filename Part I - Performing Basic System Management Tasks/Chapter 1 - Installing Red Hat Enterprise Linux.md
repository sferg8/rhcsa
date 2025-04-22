## Foundational Topics

### Overview of RHEL Installation Concepts

- RHEL installation requires hardware/software planning and subscription considerations.
- Usually done using an ISO on VMs or bootable media.
- Registration with Red Hat is required for repository access.
- Registration links the system to a support subscription.

### Understanding the RHCSA Objective

- RHCSA exam tests installation skills:
  - Local media installation.
  - Setup of networking, user accounts, and partitions.
- Proficiency with the Anaconda installer is mandatory.

### Deployment Models

- Targets:
  - Physical server (rare in test setups)
  - Virtual machines (preferred for labs)

- Benefits of virtualization:
  - Easy reinstallation via snapshots
  - Supports running multiple VMs for practice

- Expectations:
  - Deploy multiple RHEL instances
  - Vary configs: disk layout, users, networking

### Guidance on Usage

- Practice installation across different virtualization platforms.
- Memorize installer workflow and key options.
- Manual partitioning, user creation, and NIC setup should be second nature.

- Frequent reinstalls help reinforce:
  - Navigating Anaconda
  - Future kickstart scripting
  - Registration and subscription management
  - Post-install tasks (hostname, network, services, etc.)

## Preparing to Install Red Hat Enterprise Linux

### What Is Red Hat Enterprise Linux 9 Server?

- Commercial Linux distro based on open-source.
- Free dev licenses at: <https://developers.redhat.com>
- Paid subs offer:
  - Updates, support, hardware/app certification, portal access
- Free alternatives:
  - CentOS Stream (upstream)
  - Rocky/AlmaLinux (downstream rebuilds)
  - Fedora (cutting edge, not RHEL-compatible)

### Getting the Software

- Use RHEL 9 ISO via dev subscription.
- Can test with CentOS Stream, Rocky, AlmaLinux.

### Using Red Hat Enterprise Linux

- Best choice for RHCSA practice.
- Registration mandatory for repo access and full package set.

### Using CentOS Stream

- Tracks ahead of RHEL.
- Small differences can affect RHCSA accuracy.

### Other Distributions

- Rocky/Alma: accurate rebuilds.
- Fedora: too bleeding-edge for exam prep.

### Understanding Access to Repositories

- Registration unlocks BaseOS and AppStream.
- Required commands:
  - `subscription-manager register`
  - `subscription-manager attach`

### Setup Requirements

- Minimum CLI: 1 GiB RAM, 10 GiB disk
- Lab Recommended: 2+ GiB RAM, 20+ GiB disk, x86_64 CPU, NIC, ISO boot

### Cert Guide Environment Description

- Use VMs: VirtualBox, VMware, Hyper-V, KVM
- Set up 2+ RHEL 9 VMs for exercises
- Take snapshots often
- Avoid bare metal unless necessary

## Performing an Installation

1. Boot system using RHEL 9 ISO.
2. At boot menu, select:
   - *Install Red Hat Enterprise Linux 9*
   - *Test this media and install Red Hat Enterprise Linux 9*
   - *Troubleshooting*

   *Note: Testing media adds time but verifies integrity.*

3. Press `Tab` (or `e` in UEFI mode) to edit boot parameters (optional).
4. Select installation language (default is English).
5. On the **Installation Summary** screen, configure the following:
   - **Keyboard** – Add layout or modify default.
   - **Language Support** – Set additional locale settings.
   - **Time & Date** – Set timezone and enable NTP.
   - **Installation Source** – Should auto-detect ISO.
   - **Software Selection** – Choose Base Environment (e.g., Server with GUI, Minimal Install).
   - **Installation Destination** – Select disk and set partitioning scheme (auto/manual).
   - **Network & Hostname** – Enable NIC, set static IP if needed, configure hostname.
   - **Security Policy** – Optional, select predefined security profiles (e.g., PCI-DSS).
   - **Root Password** – Set strong root password.
   - **User Creation** – Add non-root user and optionally give admin rights.

6. Click **Begin Installation** when all sections are complete.
7. During installation:
   - Set root password
   - Create user (if not done earlier)

8. On completion:
   - Click **Reboot System**
   - Remove installation media

9. After reboot:
   - Skip GNOME Tour
   - Login with user or root
   - Register with `subscription-manager register`

## Summary

- RHEL 9 is the RHCSA prep target.
- Use VMs for repeatable installs and rollback.
- Learn Anaconda's options in detail.
- Use multiple VMs for network labs.
- Register system when access to repos is required.
## Define Key Terms

- **RHEL (Red Hat Enterprise Linux)** – Commercial Linux distro by Red Hat for enterprise use.
- **RHCSA (Red Hat Certified System Administrator)** – Cert for basic Linux admin tasks.
- **Anaconda** – RHEL's installation program.
- **ISO Image** – Bootable image for installing RHEL.
- **Subscription-Manager** – Tool to register RHEL for software access.
- **BaseOS** – Repository with essential system packages.
- **AppStream** – Repository with additional apps.
- **Kickstart** – Automated installation file format.
- **VM (Virtual Machine)** – Emulated machine for lab/testing.
- **Partitioning** – Dividing disk into usable segments.
- **NIC (Network Interface Card)** – Provides network access.
- **Snapshot** – Saved VM state for rollback.
- **Minimal Install** – Base-only install with no GUI.