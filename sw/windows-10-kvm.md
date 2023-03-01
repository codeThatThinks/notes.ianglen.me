---
title: Windows 10 KVM with GPU Passthrough
parent: Software Engineering
---

# Windows 10 KVM with GPU Passthrough

## Verify PCI Passthrough Support

Intel systems may need `intel_iommu=on` added as a kernel parameter. Then verify that IOMMU is enabled:

```shell
$ dmesg | grep -i -e DMAR -e IOMMU
```

Next, use the following shell script to check IOMMU groups. The IOMMU group of the GPU must not include any devices that need to remain connected to the host.

```shell
#!/bin/bash

shopt -s nullglob

for g in $(find /sys/kernel/iommu_groups/* -maxdepth 0 -type d | sort -V); do
    echo "IOMMU Group ${g##*/}:"
    for d in $g/devices/*; do
        echo -e "\t$(lspci -nns ${d##*/})"
    done;
done;
```


## Prerequisites

Install the following Arch packages:

- libvirt
- virt-manager
- qemu-desktop
- edk2-ovmf
- iptables-nft
- dnsmasq
- looking-glass
- samba

Download the following images:

- [Windows 10 install ISO](https://tb.rg-adguard.net/public.php)
- [VirtIO drivers for Windows](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso)

Add the vfio modules to `/etc/mkinitcpio.conf` and rebuild initramfs:

```
MODULES=(... vfio_pci vfio vfio_iommu_type1 vfio_virqfd ...)
```

Then add a kernel parameter to bind the `vfio-pci` module to the GPU PCI IDs:

```
vfio-pci.ids=10de:1c03,10de:10f1
```


## Create Virtual Machine with virt-manager

- Create a new VM with Windows 10 install ISO
- 16 GB memory (or half available memory)
- 6 CPUs (or half available CPUs)
- Custom storage, VM Storage Pool, 500 GB qcow2 disk
- Network: NAT

Customize configuration before install:

- Firmware: UEFI
- Manually specify CPU topology:
  - sockets = number of physical CPU sockets
  - cores = number of physical CPU cores / 2
  - threads = number of physical CPU threads per core
- Switch disk to virtio
- Switch NIC to virtio
- Disable NIC for Windows install
- Remove console device
- Add a second CDROM device with the VirtIO driver ISO
- Set CDROM device 1 as primary boot device

Then go through the Windows install procedure. Load the VirtIO storage driver from the `amd64/win10` folder on the second CDROM drive.


## Configure Passthrough GPU with Looking Glass

- Verify that the display device is set to Spice
- Remove the Tablet device
- Add PCI Host devices for the dedicated GPU (video and audio may be separate devices)

Make the following edits to the virtual machine XML config, under `<devices>`:

- Add an IVSHMEM device for Looking Glass, with the [correct amount of memory for the display setup](https://looking-glass.io/docs/B6/install/#determining-memory):

```
<shmem name='looking-glass'>
  <model type='ivshmem-plain'/>
  <size unit='M'>32</size>
</shmem>
```

- Under `<video>`, set `<model type='vga'/>`
- Add a `<input type='mouse' bus='virtio'/>` and `<input type='keyboard' bus='virtio'/>`
- Disable the memballoon device: `<memballoon model="none"/>`


## Enable Host File Sharing

Add the QEMU schema to the root `<domain>` XML tag:

```
<domain xmlns:qemu="http://libvirt.org/schemas/domain/qemu/1.0" type="kvm">
```

Then add the following QEMU options after `</devices>` to enable host file sharing via Samba:

```
<qemu:commandline>
  <qemu:arg value="-net"/>
  <qemu:arg value="user,smb=/path/to/shared/folder"/>
  <qemu:arg value="-net"/>
  <qemu:arg value="nic,model=virtio"/>
</qemu:commandline>
```

If the libvirt throws a permission denied error accessing the shared path, edit `/etc/libvirt/qemu.conf` to run QEMU as root. `seccomp` must also be disabled or QEMU will crash when trying to launch Samba:

```
user = "root"
group = "root"
seccomp_sandbox = 0
```


## Configure Windows

Configure Windows using the built-in display in virt-manager:

- Install the VirtIO drivers and virtio-win-guest-tools from the second CDROM drive
- Install the [Looking Glass host application](https://looking-glass.io/downloads)
- Install the graphics driver for the passthrough GPU
- In mouse settings, disable "Enhance pointer precision"
- Download [Custom Resolution Utility](https://www.monitortests.com/forum/Thread-Custom-Resolution-Utility-CRU) and add a custom resolution equal to the size of the Looking Glass client window.
- Map a network drive to `\\10.0.2.4\qemu` to access the host shared folder
