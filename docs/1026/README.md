# 2023 Boost - Week 13 - Networking
## Theres No Place like 127.0.0.1

📺 <https://youtu.be/dJPJTKhvkBA>

* Grok Internet networking.
    * History
        * <https://youtu.be/qvUYPm2nVXM>
    * Ethernet
        * Routing
           * Local Area Network (LAN)
           * Wide Area Network (WAN)
           * `tracepath`, `traceroute`, `pathping`, `tracert`, `mtr`
           * Mac address, Ethernet address (machine address)
           * Dynamic Host Control Protocol (DHCP)
           * Network Interface Controller (NIC)
        * Ports
           * Pub door analogy
           * Reserved ports
           * `netstat`, `nmap`, `lsof`
        * Network Address Translation (NAT)
    * Firewalls
    * IP
    * TCP/IP
    * UDP
    * Domain names
        * Registrars
        * Discovery
            * `whois`
            * `nslookup`, `dig`
            * <https://shodan.io>
        * localhost 127.0.0.1
        * Reserved
        * `/etc/hosts`
    * HTTP, HTTPS (TLS)
    * Secure Shell
        * `~/.ssh/config`
    * Beware of legacy: FTP, Telnet, Gopher, IPP
* Know the common network query commands.
    * `dig`, `nslookup`
    * `ifconfig`, `ipconfig`, `ip`, `ss`
    * `ping`
    * `nmap`
    * `ncat`/`nc`
    * `iptables`, `ufw`
    * `strace`

---

# Boost Week 13 Notes

* Bit and Bytes
    * Magabits = 1s and 0s; Yes or No
    * Megabyte = 8 Megabits
    * Mbps - Mega-bits-per-second
    * Bandwidth- How much Data is tranferring
    * Latency - The ammount of time it takes for somthing to go.
    * OSI Model - 7 layers

* Network Search Commands
    * `netstat -tuna`
    * `netstat -tua`
    * `netstat -tua |more`
    * `netstat -tua |grep`
    * `netstat -tua |grep LISTEN`
    * `netstat -tpua |grep LISTEN` (To add the -p to add the listing process)
    * `netstat -tpua |LISTEN`
    * `netstat -tpua`
    * `netstat -peanut`
    * `netstat -peaut`
    * `netstat -tulip`
    * `netstat -tuip`
    * `ip -a`
    * `strace <command>`
    * `strace -o output.txt <command>` (Good practice to output to a txt file).
    * `dig` <web-address> or <ip> (lookup)

---

# strace
`strace` is a powerful and widely used command-line tool in Unix-like operating systems (e.g., Linux) that is used for debugging and tracing system calls made by a running process. It allows users to monitor and analyze the interactions between a program and the operating system during its execution.

When a program runs, it makes various system calls to the operating system kernel to perform tasks such as reading/writing files, creating processes, allocating memory, and more. `strace` captures and displays these system calls, along with their arguments and return values, providing valuable insights into the program's behavior and helping identify issues like system call failures or performance bottlenecks.

To use `strace`, you typically run it from the command line and specify the target program as an argument. For example:

```
strace <command>
```

Once `strace` is attached to the running process, it prints a trace of all system calls made by that process to the terminal. This trace can be very detailed, showing the exact sequence of system calls, their parameters, and results. Developers and system administrators often use `strace` to troubleshoot application issues, verify correct system call usage, and gain a deeper understanding of how programs interact with the operating system.

Please note that `strace` requires administrative privileges to trace some system calls, so you may need to run it as the root user or using the `sudo` command. Also, be aware that `strace` can produce a large amount of output, so it's often helpful to redirect the output to a file for later analysis:

```
strace -o output.txt <command>
```

Remember to use `man strace` or `strace --help` to get more information about the options and usage of `strace`.


---
    
         
# Networking and The Internet
## 7 Layers of the OSI Model  

### Layer 7 - Application - End User Layer
    * TCP/IP MODEL
    * Application Layer
        * TCP/IP Protocol Suite
            * HTTP - SMTP - Telnet - FTP - DNS - RIP - SMTP - IRC - POP3 - SSH
            * Resposibilty of the Host

### Layer 6 - Presentation - Syntax Layer
        * TCP/IP MODEL
        * Application Layer
            * TCP/IP Protocol Suite
                * HTTP - SMTP - Telnet - FTP - DNS - RIP - SNMP - SSL - IMAP - SSH - JPEG - MPEG
                * Resposibilty of the Host

### Layer 5 - Session - Sync & Sens to port
        * TCP/IP MODEL
        * Application Layer
            * TCP/IP Protocol Suite
                * HTTP - SMTP - Telnet - FTP - DNS - RIP - SNMP - Various API'S - WinSock - Sockets
                * Resposibilty of the Host
                    
### Layer 4 - Transport - Ened-to-End Connections
        * TCP/IP MODEL
        * Transport Layer
            * TCP/IP Protocol Suite
                * TCP - UDP - ECN - SCTP - DCCP
                * Resposibilty of the Host

### Layer 3 - Network - Packets
        * TCP/IP MODEL
        * Internet Layer
            * TCP/IP Protocol Suite
                * ARP - IP - IGMP - ICMP - IPSec
                * Resposibilty of the Network

### Layer 2 - Data-link - Frames
        * TCP/IP MODEL
        * Network Access Layer
            * TCP/IP Protocol Suite
                * Ethernet - Token Ring - ATM - Frame Relay - SLIP - PPP - FDDI - Switch - Bridge
                * Resposibilty of the Network

### Layer 1 - Physical - Physical Structure
        * TCP/IP MODEL
        * Network Access Layer
            * TCP/IP Protocol Suite
                * Ethernet - Token Ring - ATM - Frame Relay - COAX - Fiber - Wireless - Hubs - Repeaters
                * Resposibilty of the Network


**Documentation By:** `Raymond C. TURNER`