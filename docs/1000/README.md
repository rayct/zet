# QEMU/KVM Libvirt - cli commands
## Example uses Windows 10
### Windows 10 Download Link
https://www.microsoft.com/en-us/software-downloads/windows10ISO
1. CLI line backup command
`sudo rsync --sparse --info=progress2 -aAX /var/lib/libvirt/images/"IMAGE_NAME.qcow2 ."`

1. List image info
`qemu-img info [img_name.qcow2]`

1. set dir ownership
`sudo chown rayct:rayct [img_name.qcow2]`

1. `pgrep qemu-system-86_64`

