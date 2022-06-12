# 00 - Install VMs

- Installed Windows Server 2022 as a Virtual Machine in VMware Workstation 
- Installed Windows 11 as a Virtual Machine in VMware Workstation 

## Bypass Windows 11 requirements

- shift+F10 to open cmd during installation ISO
- Registry keys

````cmd
REG ADD HKLM\SYSTEM\Setup\LabConfig /v BypassTPMCheck /t REG_DWORD /d 1

REG ADD HKLM\SYSTEM\Setup\LabConfig /v BypassRAMCheck /t REG_DWORD /d 1

REG ADD HKLM\SYSTEM\Setup\LabConfig /v BypassSecureBootCheck /t REG_DWORD /d 1
````
