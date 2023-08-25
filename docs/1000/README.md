# QEMU/KVM Libvirt - cli commands
## Demonstration using Windows 10
### Windows 10 Download Link
https://www.microsoft.com/en-us/software-download/windows10
1. CLI line backup command
`sudo rsync --sparse --info=progress2 -aAX /var/lib/libvirt/images/"IMAGE_NAME.qcow2 ."`

1. List image info
`qemu-img info [img_name.qcow2]`

1. set dir ownership
`sudo chown rayct:rayct [img_name.qcow2]`

1. `pgrep qemu-system-86_64`


---

Documentation by: **Raymond C. TURNER**

Last Updated: Monady 21st August 2023 @ 21:19 BST