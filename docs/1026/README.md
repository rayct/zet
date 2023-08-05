# 2023 Boost - Week 13

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

---

# Boost Week 13 Notes

* Bit and Bytes
    * Magabits = 1s and 0s; Yes or No
    * Megabyte = 8 Megabits
    * Mbps - Mega-bits-per-second
    * Bandwidth- How much Data is tranferring
    * Latency - The ammount of time it takes for somthing to go.
    * OSI Model - 7 layers

         
    # Networking and The Internet
    ## OSI Model  

    ### Layer 7 - Application
        * TCP/IP MODEL
        * Application Layer
            * TCP/IP Protocol Suite
                * HTTP - SMTP - Telnet - FTP - DNS - RIP - SNMP - IRC
                * Resposibilty of the Host

    ### Layer 6 - Presentation
            * TCP/IP MODEL
            * Application Layer
                * TCP/IP Protocol Suite
                    * HTTP - SMTP - Telnet - FTP - DNS - RIP - SNMP - SSL - IMAP - SSH
                    * Resposibilty of the Host

    ### Layer 5 - Session
            * TCP/IP MODEL
            * Application Layer
                * TCP/IP Protocol Suite
                    * HTTP - SMTP - Telnet - FTP - DNS - RIP - SNMP - Various API'S - Sockets
                    * Resposibilty of the Host
                        
    ### Layer 4 - Transport
            * TCP/IP MODEL
            * Transport Layer
                * TCP/IP Protocol Suite
                    * TCP - UDP - ECN - SCTP - DCCP
                    * Resposibilty of the Host

    ### Layer 3 - Network
            * TCP/IP MODEL
            * Internet Layer
                * TCP/IP Protocol Suite
                    * ARP - IP - IGMP - ICMP - IPSec
                    * Resposibilty of the Network

    ### Layer 2 - Data-link
            * TCP/IP MODEL
            * Net Access Layer
                * TCP/IP Protocol Suite
                    * Ethernet - Token Ring - ATM - Frame Relay - SLIP - PPP - FDDI
                    * Resposibilty of the Network

    ### Layer 1 - Physical
            * TCP/IP MODEL
            * Net Access Layer
                * TCP/IP Protocol Suite
                    * Ethernet - Token Ring - ATM - Frame Relay - COAX - Fiber - Wireless
                    * Resposibilty of the Network