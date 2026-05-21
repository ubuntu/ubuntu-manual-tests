**This test is a basic smoke test to ensure that the mini.iso image is functional**

This test will verify that the mini.iso:
 - boots with QEMU
 - displays the list of Ubuntu Release available
 - Run the targer ISO installer

0. Requirements

You will need QEMU installed and a good amount of RAM as the mini.iso downloads the target ISO in RAM
For the Desktop ISO we will for example use QEMU with 16GB of RAM for good measure.
This is plenty enough but at the time this was written 8GB wasn't enough.

```
# Install QEMU
$> apt update && apt upgrade
$> apt install qemu-system-x86 qemu-kvm ovmf qemu-utils

# Create 20G Virtual Drive
$> qemu-img create -f qcow2 disk.qcow2 20G

# make a writable copy of the VARS file (stores UEFI settings)
$> cp /usr/share/OVMF/OVMF_VARS_4M.fd qemu/

```
1. Boot the mini ISO
```
$> qemu-system-x86_64 \
  -enable-kvm \              # Use KVM hardware virtualization (requires /dev/kvm)
  -m 16G \                   # Allocate 16 GB of RAM to the VM
  -machine q35 \             # Emulate Intel Q35 chipset (modern PCIe-based, better ACPI/memory tables)
  -cpu host \                # Pass through host CPU model and features to the guest
  -smp 2 \                   # Assign 2 virtual CPUs
  -cdrom resolute-mini-iso-amd64.iso \  # Attach ISO as a virtual CD-ROM drive
  -drive file=disk.qcow2,format=qcow2 \ # Attach a qcow2 virtual disk (copy-on-write, sparse)
  -drive if=pflash,format=raw,readonly=on,file=/usr/share/OVMF/OVMF_CODE_4M.fd \ # UEFI firmware code (read-only flash)
  -drive if=pflash,format=raw,file=OVMF_VARS_4M.fd \ # UEFI variable store (writable, persists boot entries/settings)
  -boot d                    # Boot from CD-ROM (d) rather than hard disk (c)
VNC server running on 127.0.0.1:5900
```
 
2. Chose the server or desktop installer

At this point you should be seeing this menu using tiger vnc
```
$> tigervnc 127.0.0.1:5900
```
<img width="1285" height="631" alt="Screenshot From 2026-03-26 13-48-57" src="https://github.com/user-attachments/assets/9d9ff039-6aab-4feb-b3e6-de75dbc14fee" />

If you don't see this menu: **Test Failed**.

3. Chose the Desktop ISO for 24.04.4
You should see the ISO being downloaded, then boot to the setup wizard
<img width="1283" height="833" alt="Screenshot From 2026-03-26 14-00-41" src="https://github.com/user-attachments/assets/fc063f9e-8d8e-400b-b01b-fbdd4544db69" />

If you don't see the setup wizard: **Test Failed**.

If you can see the Desktop Installer Wizard: **Test Succeeded**!
