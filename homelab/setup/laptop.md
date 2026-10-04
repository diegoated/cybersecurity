# Homelab Setup: Laptop 

**Goal:** turn the Thinkpad T14 (Arch Linux) into a hyper visor host for the lab.

## 1. Enable Virtualization
- Already enabled in the BIOS from earlier VM work.
- Verified with `lscpu | grep Virtualization`: shows VT-x.

## 2. Install virtualization stack
Ran the command:
- `sudo pacman -S qemu-full libvirt virt-manager dnsmasq edk2-ovmf swtpm 7zip`

Below is a list of what each tool does:
- qemu-full: QEMU with all device types, plus qemu-img for converting disks.
- libvirt: the VM manager service.
- virt-manager: the GUI.
- dnsmasq: a small DHCP/DNS server that gives your VMs IP addresses.
- edk2-ovmf: UEFI firmware for VMs (needed for Windows 11 later).
- swtpm: a software TPM chip (also for Windows 11).
- 7zip: to extract the Kali download.

## 3. Start services and get permissions
```bash
sudo systemctl enable --now libvirtd
sudo usermod -aG libvirt $USER
sudo virsh net-start default
sudo virsh net-autostart default
```
- systemctl enable --now: starts the service now and at every boot
- usermod -aG libvirt $USER: adds the user to the libvert group with the -a meaning append. This allows us to manage VMs without root privillages
- virsh commands: sets default NAT network and make it start at boot.

## 4. Build isolated lab network
In virt-manager:
- Edit > Connection Details > Virtual Networks > +

Key Words:
- NAT: VMs could reach the internet through the laptop, and nothing outside can reach them.
- Isolated: VMs only talk to eachother.
- Bridged: VMs appear as real devices on home networks.

## 5. Setting up Kali Linux
To set up Kali Linux on virt-manager:
- Download the pre-built QEMU Kali Linux image from [kali.org](https://kali.org)
