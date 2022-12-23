---
title: Windows 10 KVM with PCIe Passthrough
parent: Software Engineering
---

# Create Virtual Machine with virt-manager

- Create a new VM with Windows 10 install ISO
- 16 GB memory
- 6 CPUs
- Custom storage, VM Storage Pool, 500 GB qcow2 disk
- Network: NAT

Customize configuration before install:

- Firmware: UEFI
- Switch disk to virtio
- Switch NIC to virtio
- Disable NIC for Windows install
- Remove console device
- Add a second CDROM device with the [Windows VirtIO driver ISO](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/stable-virtio/virtio-win.iso)
- Set CDROM device 1 as primary boot device

Then go through the Windows install procedure, making sure to load the VirtIO storage driver from the second CDROM device.


# Passthrough GPU w/ Looking Glass

- Add PCI Host devices for dedicated GPU and GPU audio
- Add an IVSHMEM device for Looking Glass, with the [correct amount of memory for the display setup](https://looking-glass.io/docs/B6/install/#determining-memory):

```
<shmem name='looking-glass'>
  <model type='ivshmem-plain'/>
  <size unit='M'>32</size>
</shmem>
```

- Verify that the Display device is set to Spice
- Under `<video>`, set `<model type='vga'/>`
- Remove the Tablet device
- Add a `<input type='mouse' bus='virtio'/>` and `<input type='keyboard' bus='virtio'/>`
- Disable the memballoon device: `<memballoon model="none"/>`


# Host File Sharing

Add the QEMU schema to the root `<domain>` XML tag:

```
<domain xmlns:qemu="http://libvirt.org/schemas/domain/qemu/1.0" type="kvm">
```

Then add the following QEMU options after `<devices/>` to enable host file sharing via Samba:

```
<qemu:commandline>
    <qemu:arg value="-net"/>
    <qemu:arg value="user,smb=/home/ian"/>
    <qemu:arg value="-net"/>
    <qemu:arg value="nic,model=virtio"/>
</qemu:commandline>
```


# Windows Configuration

Configure Windows using the built-in display in virt-manager:

- Install the VirtIO drivers and virtio-win-guest-tools from the second CDROM device
- Install the [Looking Glass host application](https://looking-glass.io/downloads)
- Install the graphics driver for the passthrough GPU
- In mouse settings, disable "Enhance pointer precision"
- Download [Custom Resolution Utility](https://www.monitortests.com/forum/Thread-Custom-Resolution-Utility-CRU) and add a custom resolution equal to the size of the Looking Glass client window.
- Map a network drive to `\\10.0.2.4\myshare` to access the host shared folder
