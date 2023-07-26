
# TODO:
# FreeBSD: Installation & First Look.
## The X Window System(Xorg) with kde plasma Desktop and Utilities

# HOST HARDWARE SPECS
### Dell PowerEdge R710
1. CPU - Intel(R) Xeon(R) CPU X5670 @ 2.93GHz
1. Sockets: 2
1. Cores per socket: 6
1. Memory: 32GB


# HOST OS:
## VMWare ESXi 6.2 U3

# Installation Guide/Commands for Display Server, Display Manager and Display Environment.
We can acheive this with one command.
    `pkg install xorg sddm kde5 plasma5-sddm-kcm`

1. Xorg: The X Window System(Graphical User Interface)
2. sddm: Simple Desktop Display Manager
1. kde5: Desktop Environment(KDE Plasma) GPL 2.0 or later
1. plasma-sddm-kcm:

## Now we need to enable some services

Now there are still a few steps we need to do before we can actually reboot the machine first we need to actually enable
the services we need and we need to actually configure also xor to work with kvm now if you're installing this on a laptop or on a pc you can probably skip.

#### List of Desktop Environments: <https://docs.freebsd.org/en/books/handbook/desktop/>

# Tip!
### You must login as ROOT to complete the install:

 `pkg install sudo`

#### Youtube Install Video by: EF - Linux Made Simple <https://www.youtube.com/watch?v=kZyW7oiAvvo> 



# Note!
"FreeBSD is a free and open-source Unix-like operating system descended from the Berkeley Software Distribution (BSD), which was based on Research Unix." FreeBSD differs from Linux in that it's a whole OS (Unix), from the kernel, drivers, software and documentation, whereas Linux offer the kernel and drivers only, and it's then up to the distribution to provide the rest (all distributions being derivatives of the GNU/Linux operating system). A different approach indeed.

#### FreeBSD Handbook: <https://docs.freebsd.org/en/books/handbook/x11/#x11-wm>
#### SFreeBSD update: <https://docs.freebsd.org/en/books/handbook/cutting-edge/#updating-upgrading-freebsdupdate>





**Documentation By:** `Raymond C. TURNER`