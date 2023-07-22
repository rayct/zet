# VMWare ESXi 6.7 Update 3 - Notes and Issues

## Answer from Stackoverflow

## Unsupported or invalid disk type 2 for 'scsi0:0'. Ensure that the disk has been imported
* Asked 5 years, 5 months ago
* Modified 3 months ago
* Viewed 50k times

### Option 1
* I solved the issue by changing the Virtual Device Node from SCSI controller 0 to IDE controller 0 or 1 in the hard disk settings of the virtual machine.
* https://kb.vmware.com/s/article/1028943

### Option 2
If anyone has also the same issue, check this article from Vmware. It solved for me: https://kb.vmware.com/s/article/1028943

1. Connect to the ESX/ESXi host via SSH. I used Putty for that.

1. Run this command:

    `vmkfstools -i <HostedVirtualDisk> <ESXVirtualDisk>`

    Where <HostedVirtualDisk> is the path to the vmdk on the host and <ESXVirtualDisk> is the vmdk to be output by the command.

    For example:

    `vmkfstools -i /vmfs/volumes/datastore/virtual_machine_folder/virtual_machine.vmdk /vmfs/volumes/datastore/ new_virtual_machine_folder/virtual_machine.vmdk`

1. Detach the currently attached VMDK from the virtual machine:

    In the vSphere Client or vSphere Web Client, right-click the virtual machine and click Edit Settings.
    Select the hard disk.
    Click Remove.
    Select the Remove from virtual machine option.
    Click OK.
    1. Reattach the newly formatted VMDK from Step 2:

    In the vSphere Client or vSphere Web Client, right-click the virtual machine and click Edit Settings.
    Click Add.
    Select the hard disk.
    Click Next.
    Select the Use an existing virtual disk option.
    Click Next.
    Click Browse and locate the new VMDK created in Step 2.
    Click Next.
    Click Next.
    Click Finish to close the Add Hardware window.
    Click OK to close the Virtual Machine properties window.
1. Power on the virtual machine.

## The Third Industrial Revolution: A Radical New Sharing Economy
    * https://www.youtube.com/watch?v=QX3M8Ka9vUA - min:31:00

**Documentation By:** `Ray C. TURNER`

