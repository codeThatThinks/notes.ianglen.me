---
title: SolidWorks in VirtualBox
parent: Mechanical Engineering
---

# SolidWorks in VirtualBox

SolidWorks will not run if it detects it is inside a virtual machine. The installer won’t even run. You must modify your VirtualBox VM to add ACPI information so that it mimics a real computer.

1. In the VM settings, set the _Paravirtualization Interface_ to `None`.
2. Edit the VM’s `.vbox` file and add the ACPI information that SolidWorks wants to see. You can copy real ACPI values from the host machine or make up some serial numbers.

After `<MediaRegistry>`, add the following:

```xml
<ExtraData>
  <ExtraDataItem name="VBoxInternal/Devices/ahci/0/Config/Port0/FirmwareRevision" value="EMT03L0Q"/>
  <ExtraDataItem name="VBoxInternal/Devices/ahci/0/Config/Port0/ModelNumber" value="SAMSUNG MZ7LN512HCHP-000L1"/>
  <ExtraDataItem name="VBoxInternal/Devices/ahci/0/Config/Port0/SerialNumber" value="S1ZKNXAG609323"/>
  <ExtraDataItem name="VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVendor" value="LENOVO"/>
  <ExtraDataItem name="VBoxInternal/Devices/pcbios/0/Config/DmiBIOSVersion" value="N11ET31W (1.07 )"/>
  <ExtraDataItem name="VBoxInternal/Devices/pcbios/0/Config/DmiSystemSerial" value="R90GLL59"/>
  <ExtraDataItem name="VBoxInternal/Devices/pcbios/0/Config/DmiSystemVendor" value="LENOVO"/>
</ExtraData>
```
