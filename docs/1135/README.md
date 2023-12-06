# NordVPN Documentation - Linux 2023/24

The NordVPN native application is the recommended option for connecting to NordVPN servers on your Linux device. We designed it with your experience in mind, giving easy access to features such as Threat Protection, auto-connect, and automated Kill Switch.

To start using the NordVPN application for Linux, follow the steps below. 
Installation process

    Download the NordVPN Linux client by opening the terminal, writing the command below, and following any on-screen instructions:

`sh <(curl -sSf https://downloads.nordcdn.com/apps/linux/install.sh)`
 

Note: If you do not have a curl package, evidenced by the fact that the above does not work, you can alternatively use this command:

`sh <(wget -qO - https://downloads.nordcdn.com/apps/linux/install.sh)`

Additionally, if you receive the following issue: Whoops! Permission denied accessing /run/nordvpn/nordvpnd.sock, all you need to do is write the following command: sudo usermod -aG nordvpn $USER and then reboot your device.


## Log in to your NordVPN account:

nordvpn login

## Connect to a NordVPN server:

`nordvpn connect`

## Settings

To access the NordVPN client settings, type the nordvpn command in Terminal.

Here is the list of available commands:

`nordvpn login — log in.`
`nordvpn connect` or `nordvpn c — connect to VPN`. To connect to specific servers, use `nordvpn connect <country_code` `server_number> (eg. nordvpn connect uk715).`
`nordvpn disconnect or nordvpn d — disconnect from VPN.`
`nordvpn c double_vpn — connect to the closest Double VPN server.`
`nordvpn connect --group double_vpn <country_code> — connect to a specific country using Double VPN servers.`
`nordvpn connect --group p2p <country_code> — Connect to a specific country using P2P servers.`

`nordvpn connect P2P — connect to a P2P server.`
`nordvpn connect The_Americas — connect to servers located in the Americas.`
`nordvpn connect Dedicated_IP — connect to a Dedicated IP server.`

`nordvpn set or nordvpn s — set a configuration option.`

## Possible options:

nordvpn set threatprotectionlite on or off — enable or disable Threat Protection Lite.
nordvpn set killswitch on or off — enable or disable Kill Switch.
nordvpn set autoconnect on or off — enable or disable auto-connect. You can set a specific server for automatic connection using nordvpn set autoconnect on country_code+server_number. Example: nordvpn set autoconnect on us2435.

nordvpn set notify on or off — enable or disable notifications.
nordvpn set dns 1.1.1.1 1.0.0.1 — set custom DNS (you can set up a single DNS or two, like shown in this command).
nordvpn set protocol udp or tcp — switch between UDP and TCP protocols.
nordvpn set obfuscate on or off — enable or disable obfuscated servers.
nordvpn set technology — set connection technology (OpenVPN or NordLynx).
nordvpn set meshnet on — turn on Meshnet on your device.
nordvpn set lan-discovery enable or disable — enable/disable LAN discovery.
nordvpn set lan-discovery --help — get more information on LAN discovery.

nordvpn whitelist add port 22 — add a rule to allowlist a specified incoming port. You can allowlist multiple ports — just separate their numbers with a space.
nordvpn whitelist remove port 22 — remove the rule to allowlist a specified port.
nordvpn whitelist add subnet 192.168.0.0/16 — add a rule to allowlist a specified subnet.
nordvpn whitelist remove subnet 192.168.0.0/16 — remove the rule to allowlist a specified subnet.

nordvpn account — see account information.
nordvpn register — register a new user account.
nordvpn rate — rate your last connection quality (1-5).
nordvpn settings — see the current settings.
nordvpn status — see the connection status.
nordvpn countries — see the country list.
nordvpn cities — see the city list. E.g.: nordvpn cities united_states
nordvpn groups — see a list of available server groups.
nordvpn logout — log out.
nordvpn help or nordvpn h — see the list of available commands or help for a specific command.

*You can get an extensive explanation of all commands by using the man nordvpn command in Terminal.*

---

Documentation By: **Raymond C. TURNER**

**Revision:** Wednesday 6th December 2023