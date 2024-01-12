# A list of 50 useful Nmap commands for various purposes:

**1. Basic Scan:**
```bash
nmap target
```

**2. Aggressive Scan:**
```bash
nmap -A target
```

**3. Scan Multiple Hosts:**
```bash
nmap target1 target2
```

**4. Scan Specific Ports:**
```bash
nmap -p 80,443 target
```

**5. Scan a Range of IPs:**
```bash
nmap 192.168.1.1-50
```

**6. Scan Top Ports:**
```bash
nmap --top-ports 10 target
```

**7. Service Version Detection:**
```bash
nmap -sV target
```

**8. OS Detection:**
```bash
nmap -O target
```

**9. Script Scanning:**
```bash
nmap --script=default target
```

**10. Scan for Vulnerabilities:**
```bash
nmap --script vuln target
```

**11. UDP Scan:**
```bash
nmap -sU target
```

**12. Intense Scan:**
```bash
nmap -T4 -A target
```

**13. Ping Scan:**
```bash
nmap -sn target
```

**14. Disable DNS Resolution:**
```bash
nmap -n target
```

**15. Save Output to a File:**
```bash
nmap -oN output.txt target
```

**16. Save Output in XML Format:**
```bash
nmap -oX output.xml target
```

**17. Save Output in All Formats:**
```bash
nmap -oA output target
```

**18. Scan for Heartbleed:**
```bash
nmap --script ssl-heartbleed target
```

**19. Scan for Shellshock:**
```bash
nmap --script http-shellshock target
```

**20. Detect and Print Firewalls:**
```bash
nmap --unprivileged -p 1-65535 target
```

**21. Fast Scan:**
```bash
nmap -F target
```

**22. SYN Stealth Scan:**
```bash
nmap -sS target
```

**23. Full TCP Connect Scan:**
```bash
nmap -sT target
```

**24. IP Protocol Scan:**
```bash
nmap -sO target
```

**25. Show Open Ports and Services:**
```bash
nmap --open target
```

**26. Show Host Interfaces and Routes:**
```bash
nmap --iflist
```

**27. List Nmap Script Categories:**
```bash
nmap --script-help
```

**28. Scan IPv6 Addresses:**
```bash
nmap -6 target
```

**29. Scan with Randomization:**
```bash
nmap --randomize-hosts target
```

**30. Scan Through a Proxy:**
```bash
nmap --proxy socks4://proxy:port target
```

**31. Trace Route to Target:**
```bash
nmap --traceroute target
```

**32. Skip Host Discovery:**
```bash
nmap -PN target
```

**33. Perform Aggressive Scan without Pinging:**
```bash
nmap -PN -A target
```

**34. Set Custom Timings:**
```bash
nmap --timing paranoid target
```

**35. Ping Scan with ARP Requests:**
```bash
nmap -PR target
```

**36. Scan Using a Specific Network Interface:**
```bash
nmap --interface eth0 target
```

**37. Enable OS Detection without Version Detection:**
```bash
nmap -O --version-intensity 0 target
```

**38. Exclude Hosts from Scan:**
```bash
nmap target --exclude 192.168.1.2
```

**39. Show Live Hosts in a Range:**
```bash
nmap -sL 192.168.1.1-50
```

**40. List Supported NSE Categories:**
```bash
nmap --script-help all
```

**41. Scan for DNS Servers:**
```bash
nmap -p 53 target
```

**42. Retrieve MAC Addresses:**
```bash
nmap -p 22 --unprivileged target
```

**43. Scan Using a Custom Configuration File:**
```bash
nmap -sS -iL targets.txt -vv -oN output.txt
```

**44. Scan with Connection Throttling:**
```bash
nmap --max-rate 100 target
```

**45. Scan Multiple Ports and Hosts from a File:**
```bash
nmap -p 80,443 -iL targets.txt
```

**46. Scan IPv4 and IPv6 Addresses:**
```bash
nmap -6 -4 target
```

**47. Exclude Ports from Scan:**
```bash
nmap --exclude-ports 22,80 target
```

**48. Save Nmap Output to a Grepable File:**
```bash
nmap -oG output.grepable target
```

**49. Scan for SNMP Services:**
```bash
nmap -p 161,162 target
```

**50. Scan for Redis Services:**
```bash
nmap -p 6379 target
```

Remember to use Nmap responsibly and ensure that you have proper authorization before scanning any network. Unauthorized scanning may violate laws and policies.



---

Documentation By: **Raymond C. TURNER**

**Revision:** Friday 12th January 2024