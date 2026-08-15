# Ubuntu Installation Media Unmount Failure

## Problem

After completing the Ubuntu Server installation in VMware Workstation, the
installer failed to unmount the installation media.

The following message was displayed:

```text
[FAILED] Failed unmounting /cdrom.
Please remove the installation medium, then press ENTER:
```

## Symptoms

The installation completed, but during the final stage before rebooting,
Ubuntu reported that it could not unmount `/cdrom`.

The installer requested that the installation medium be removed before
continuing.

## Investigation

The `/cdrom` mount point is associated with the Ubuntu Server installation
media.

Since Ubuntu Server was installed using an ISO file attached to the VMware
virtual CD/DVD drive, the ISO was still connected to the virtual machine when
the installer attempted to unmount it.

## Cause

The Ubuntu Server installation ISO was still mounted as the virtual CD/DVD
drive in VMware Workstation.

The installer was therefore unable to completely unmount the `/cdrom`
installation media.

## Solution
1. Opened the Ubuntu Server's VMware virtual machine settings.
2. Opened the virtual CD/DVD drive settings.
3. Disconnected the Ubuntu Server ISO from the virtual CD/DVD drive by unchecking `Connect at power on`.

## Verification

The virtual machine successfully continued the reboot process and started Ubuntu Server from the installed virtual disk instead of the installation
media.

The server successfully reached the Ubuntu Server CLI.

## Lessons Learned
- Ubuntu Server installation media is mounted during the installation
process.
- A VMware virtual CD/DVD drive can remain connected after installation.
- Installation media should be disconnected before booting the newly installed operating system.
- Virtual machine hardware settings can affect the operating system's installation and boot process.
- Troubleshooting virtualization issues requires checking both the guest operating system and the hypervisor configuration.
