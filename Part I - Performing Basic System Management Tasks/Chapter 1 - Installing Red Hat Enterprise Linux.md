## Preparing to Install Red Hat Enterprise Linux

- Red Hat Enterprise Linux 9 (RHEL 9) is a commercially supported Linux distribution developed by Red Hat.
- A valid subscription is required to access updates, patches, and full software repositories.
- A 60-day free trial is available for testing and learning purposes; full licenses are available for enterprise use.
- Alternatives to RHEL include CentOS Stream, which serves as a development preview, and community-maintained rebuilds.
- Access to software repositories is tightly coupled to the subscription model; the installation method impacts post-install repository availability.
- Verifying hardware compatibility is essential before proceeding with installation, especially for physical servers or resource-limited virtual machines.
- This guide assumes installation and exercises will be conducted in a virtual machine environment.

### What Is Red Hat Enterprise Linux 9 Server?

- RHEL 9 is a Linux-based operating system built for reliability, performance, and long-term enterprise support.
- It is produced by Red Hat, now a subsidiary of IBM, and is widely used in enterprise data centers and cloud deployments.
- RHEL benefits from upstream development in Fedora, a fast-moving open-source project that contributes innovations.
- Intended use cases include bare-metal servers, virtual machines, and containerized environments.
- RHEL includes tools like Cockpit (a browser-based management tool), advanced performance tuning capabilities, and kernel live patching support.
- The system runs on a broad range of hardware platforms and is certified for use with many enterprise software packages.
- A Red Hat subscription provides access to software repositories, security updates, official documentation, and technical support.

---
## Getting the Software

- Multiple methods are available to acquire installation media and access RHEL-based systems.
- Options include downloading official RHEL from Red Hat, using CentOS Stream for preview builds, or choosing from several RHEL-compatible alternatives.

### Using Red Hat Enterprise Linux

- For RHCSA study, using official RHEL is strongly recommended due to guaranteed software and feature alignment.
- Access RHEL downloads by creating a Red Hat developer account at https://developers.redhat.com.
- A developer subscription permits non-commercial use on up to 16 systems.
- Benefits include full access to the Red Hat Customer Portal, knowledge base, errata, and updates.
- Red Hat Network (RHN) services provide centralized software updates and license management.

### Using CentOS Stream

- Previously, CentOS was a downstream rebuild of RHEL; it now operates as CentOS Stream, which sits between Fedora and RHEL in the development cycle.
- CentOS Stream receives updates before they land in RHEL, making it a rolling-release platform.
- It is not suitable for production RHCSA environments due to its shifting features and lack of versioned snapshots.
- Still, it is useful for previewing future changes to RHEL but does not reflect a stable RHEL release.

### Other Distributions

- Fedora is a cutting-edge Linux distribution sponsored by Red Hat and acts as the upstream source for RHEL.
  - It evolves rapidly and is not recommended for RHCSA prep due to possible feature differences.
- AlmaLinux and Rocky Linux are both binary-compatible forks of RHEL.
  - These projects aim to provide free, community-supported versions of RHEL with equivalent functionality.
  - They lack official Red Hat support but offer stable alternatives for lab environments.

### Understanding Access to Repositories

- Official RHEL repositories are gated behind active subscriptions; access requires valid system registration with Red Hat.
- Without a subscription, package installation and updates through Red Hat’s repos are blocked.
- CentOS Stream’s repositories remain publicly accessible and are not subscription-bound.
- AlmaLinux and Rocky Linux maintain open repositories with full access to their software packages.
- Repository configuration files are stored in `/etc/yum.repos.d/` and are used by the DNF package manager.
- The system’s subscription status dynamically influences which repositories are active.
- Developer accounts include limited repository access suitable for training and testing setups.

### Setup Requirements

- Minimum system requirements to install RHEL:
  - 1 GiB RAM, 10 GiB storage, 1 NIC — sufficient for command-line install only.
- Recommended setup for this guide:
  - 64-bit Intel or ARM CPU
  - 2 GiB RAM minimum
  - 20 GiB available disk space
  - Network interface and virtual/physical DVD drive
- Clarify storage units: 1 GiB = 1024^3 bytes, distinct from 1 GB = 1000^3 bytes.
- Ensure virtual machine software supports necessary features for RHEL installation.

### Cert Guide Environment Description

- This guide primarily uses one RHEL 9 virtual machine to complete hands-on tasks.
- Some chapters, especially involving network services, require a second RHEL VM.
- Recommended virtualization platforms: VMware Workstation, Fusion, Hyper-V, VirtualBox.
- Use VM snapshots before each major configuration change to quickly revert in case of errors.
- KVM (Linux-native hypervisor) is supported but requires more setup knowledge.
- Physical installations are possible but less convenient due to lack of rollback capability.
- Creating a fresh VM per chapter can help isolate exercises and reduce environment issues.

---
## Performing an Installation

- Begin by booting the installation media via ISO or physical DVD in the target system.
- The boot menu offers options to install, test media, or troubleshoot.
- Choose "Install Red Hat Enterprise Linux 9.0" to start the graphical installer.
- The welcome screen prompts for language and keyboard selection, followed by the Installation Summary screen.
- Key configuration categories in the summary screen include:
  - Keyboard, Time & Date, Language Support
  - Installation Source, Software Selection, Installation Destination
  - Root Password, User Creation, Network & Hostname, KDUMP, Connect to Red Hat, Security Policy
- Select "Server with GUI" environment to follow RHCSA GUI-based instructions.
- Set a strong root password and add a standard user account for practice (e.g., student or admin).
- Ensure the network connection is active and set an appropriate hostname (e.g., server1.example.com).
- Click "Begin Installation" to proceed; the installer handles partitioning and file system setup (default is XFS).
- After installation completes, reboot the system and finalize the setup.
- Log in with the credentials you created and verify the system is functioning.

---
## Summary

- RHEL is the standard system for RHCSA certification preparation.
- Installation may be performed on physical machines or virtual machines using ISO, USB, or DVD.
- Red Hat’s developer subscription is ideal for lab environments.
- CentOS Stream and RHEL clones provide alternatives but with caveats.
- Proper subscription or repository configuration is essential for accessing packages and updates.
- Use virtualization for flexibility and snapshot recovery.
- The installation process covers localization, network, user, and storage configuration.

---
## Define Key Terms

- **distribution** – A complete operating system built around the Linux kernel, packaged with software tools and utilities.
- **Linux** – A family of open-source Unix-like operating systems based on the Linux kernel.
- **Red Hat** – A software company that develops RHEL and offers commercial support and enterprise solutions.
- **CentOS** – A community-driven RHEL-based distribution; now a rolling-release as CentOS Stream.
- **Fedora** – A cutting-edge community Linux distribution sponsored by Red Hat, used as a testing ground for RHEL.
- **AlmaLinux** – A free, open-source RHEL fork maintained by the AlmaLinux OS Foundation.
- **Rocky Linux** – A free RHEL-compatible distribution initiated by one of CentOS's original founders after the CentOS Stream shift.

