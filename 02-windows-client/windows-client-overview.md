## Creating the Windows 11 Client VM 

### VM creation 

For this client VM, the following virtual hardware specifications were sufficient for the lab:
- **Memory:** 3GB
- **Processors:** 2
- **Hard Disk (NVMe):** 64GB

For the CD/DVD drive:
- Downloaded the Windows 11 ISO file (Version 25H2) from the [official Microsoft website](https://www.microsoft.com/en-in/software-download/windows11)
- Mounted the  ISO to the VM's CD/DVD drive (SATA)

For the network adpater...
- Attached the VM to the same host-only network as the other VMs in the virtual LAN
