# Homelab Setup: Laptop 

**Goal:** turn the Thinkpad T14 (Arch Linux) into a hyper visor host for the lab.

## 1. Enable Virtualization
- Already enabled in the BIOS from earlier VM work.
- Verified with `lscpu | grep Virtualization`: shows VT-x.

## 2. Install virtualization stack
- Ran the command:
- `sudo pacman -S qemu-full libvirt virt-manager dnsmasq edk2-ovmf swtpm 7zip`
Below is a list of what each tool does:
- qemu-full: QEMU with all device types, plus qemu-img for converting disks.
- libvirt: the VM manager service.
- virt-manager: the GUI.
- dnsmasq: a small DHCP/DNS server that gives your VMs IP addresses.
- edk2-ovmf: UEFI firmware for VMs (needed for Windows 11 later).
- swtpm: a software TPM chip (also for Windows 11).
- 7zip: to extract the Kali download.
