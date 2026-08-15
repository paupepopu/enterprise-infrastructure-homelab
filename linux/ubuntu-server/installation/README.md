# Ubuntu Server Installation

## Environment

| Component | Configuration |
|---|---|
| Host OS | Windows |
| Hypervisor | VMware Workstation |
| Guest OS | Ubuntu Server 26.04 LTS |
| CPU | 2 cores |
| RAM | 2 GB |
| Storage | 25 GB |
| Network | NAT |

## Objective

Install and configure Ubuntu Server as the first server
in the Enterprise Infrastructure Homelab.

## Installation

### 1. Create VMware Virtual Machine for Ubuntu Server

Created a new virtual machine in VMware Workstation for the homelab with the specifications above.

### 2. Install Ubuntu Server

Installed Ubuntu Server 26.04 LTS on the VMware virtual machine.

During installation:
- Created the `homelab` administrative user
- Set the hostname to `ubuntu-server`
- Left Featured Server Snaps unselected
- Completed the installation and rebooted into the Ubuntu Server CLI

During the final stage of the Ubuntu Server installation, the installer
failed to unmount the `/cdrom` installation media. The issue was resolved by
disconnecting the Ubuntu Server ISO from the VMware virtual CD/DVD drive
before continuing the reboot process.

See [Ubuntu CD-ROM Unmount Failure](../../../docs/troubleshooting/ubuntu-cdrom-unmount-failure.md) for details.

### 3. Initial Configuration

After installation, performed the initial configuration:

- Logged into the `homelab` account
- Verified the hostname
- Verified network connectivity
- Updated the system packages

Commands used:

```bash
hostname
ip addr
ping -c 4 google.com
sudo apt update
sudo apt upgrade
```
During the initial package upgrade, an APT repository returned a
`403 Forbidden` error. The issue was investigated and resolved by
switching from the Philippine Ubuntu mirror to the main Ubuntu archive.

See [APT 403 Forbidden Troubleshooting](../../../docs/troubleshooting/apt-403-forbidden.md) for details.

## Verification

The Ubuntu Server VM successfully boots into the CLI and the system is accessible.
...

## Troubleshooting

Two issues were encountered during the installation and initial configuration:

1. [Ubuntu CD-ROM Unmount Failure](../../../docs/troubleshooting/ubuntu-cdrom-unmount-failure.md)
2. [APT 403 Forbidden Error](../../../docs/troubleshooting/apt-403-forbidden.md)

## Lessons Learned

- Learned how to create a virtual machine using VMware Workstation.
- Learned how to install Ubuntu Server in a virtualized environment.
- Learned the difference between a server OS and a desktop environment.
- Learned how the initial Ubuntu Server user and hostname are configured.
- Learned that `apt update` refreshes the package lists, while `apt upgrade` installs available updates.
- Learned how to change a package source from the Philippine mirror to the main
