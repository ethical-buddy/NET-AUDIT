# 🔐 Network Penetration Testing Checklist

A comprehensive guide to penetration testing activities across the phases of a typical network security assessment. Includes test cases, tools, and features used.

---

## 📁 Table of Contents

- [🔍 Reconnaissance](#reconnaissance)
- [👣 Footprinting](#footprinting)
- [📡 Scanning](#scanning)
- [📊 Enumeration](#enumeration)
- [🧠 Target Mapping](#target-mapping)
- [💥 Exploitation](#exploitation)
- [🔓 Gaining Access](#gaining-access)
- [📦 Post-Exploitation](#post---exploitation)
- [🧹 Clearing Tracks](#clearing-tracks)

---

## 🔍 Reconnaissance

| Test Case                                | Tools                                           | Feature/Command                                  |
|------------------------------------------|------------------------------------------------|--------------------------------------------------|
| Find network range                       | Angry IP Scanner, Advanced IP Scanner         | IP Range                                         |
| Identifying access points                | Nmap, Zenmap, Sparta, Nessus Pro              | Nmap Aggressive Scan                             |
| Identifying routers/switches/hubs        | Nmap, Zenmap, Sparta, Nessus Pro              | Nmap Aggressive Scan                             |
| Identifying subnets                      | Angry IP Scanner                              | IP Range                                         |
| Identifying VLANs                        | Nmap, Zenmap, Sparta, Nessus Pro              | Nmap Aggressive Scan                             |
| Identifying active hosts                 | Angry IP Scanner                              | IP Range                                         |
| Performing search engine analysis        | Google Dorks, Shodan, OSINT                   | `filetype:`, `inurl:`, `intitle:`, `site:`       |
| Performing WHOIS lookups                 | WHOIS Lookup                                  | WHOIS Database                                   |
| Identifying firewalls/honeypots          | Nmap, Zenmap, Sparta, Nessus Pro              | Nmap TCP ACK Scan `-sA`                          |
| Identifying IDS/IPS                      | Nmap, Zenmap, Sparta, Nessus Pro              | Nmap TCP ACK Scan `-sA`                          |
| Find hosted websites                     | Nmap, Zenmap, Sparta, Nessus Pro              | Nmap Port Scan                                   |
| Find network protocols                   | Nmap, Zenmap, Sparta, Nessus Pro              | Nmap Port Scan                                   |
| Find network devices                     | Angry IP Scanner                              | IP Range                                         |

---

## 👣 Footprinting

| Test Case                                | Tools                                           | Feature/Command                                  |
|------------------------------------------|------------------------------------------------|--------------------------------------------------|
| Find network services                    | Nmap, Zenmap, Sparta, Nessus Pro              | Nmap TCP ACK Scan `-sA`                          |
| Find DNS records                         | nslookup                                       | Use `?` for options                              |
| Find route paths                         | Tracert                                        | `tracert <IP>`                                   |
| Banner grabbing - network devices        | Nmap, Zenmap, Sparta, Nessus Pro              | Nmap NSE Script                                  |
| Banner grabbing - firewalls/IDS/IPS      | Nmap, Zenmap, Sparta, Nessus Pro              | Nmap TCP ACK Scan `-sA`                          |
| Find firewall/IDS/IPS versions           | Nmap, Zenmap, Sparta, Nessus Pro              | Nmap TCP ACK Scan `-sA`                          |
| Find common running services             | Nmap, Zenmap, Sparta, Nessus Pro              | Nmap TCP ACK Scan `-sA`                          |
| Capture LAN/WLAN traffic                 | Wireshark, tcpdump, Bettercap, Acrylic WiFi   | Wireshark LAN/WLAN Interface Scan                |
| Analyze traffic                          | Wireshark                                      | PCAP Analysis                                    |

---

## 📡 Scanning

| Test Case                                | Tools                                           | Feature/Command                                  |
|------------------------------------------|------------------------------------------------|--------------------------------------------------|
| Scan for open ports                      | Nmap, Zenmap                                  | `nmap -p- <IP>`                                  |
| Identify service/protocol vulnerabilities| Nmap, OpenVAS                                 | `nmap -A --script=vulns <IP>`                    |
| Identify vulnerabilities in network devices| Nmap, OpenVAS                                | `nmap -A --script=vulns <IP>`                    |
| Identify critical assets                 | Manual Analysis                               | Analyze recon & footprinting results             |
| Check default credentials                | Hydra, Cain & Abel, JTR                       | `hydra -l user -P passlist.txt <IP>`             |

---

## 📊 Enumeration

| Test Case                                | Tools                                           | Feature/Command                                  |
|------------------------------------------|------------------------------------------------|--------------------------------------------------|
| Enumerate network services               | Nmap, Zenmap                                  | `nmap -A <IP>`                                   |
| Enumerate hostnames                      | DNSenum, DNSRecon, Nmap                       | `nmap -A <IP>`                                   |
| Enumerate user groups/accounts           | Powershell, Finger                            | `get-netgpogroup`, `finger @<IP>`                |
| Enumerate file paths                     | Dirbuster, Dirb                               | `dirb -w <wordlist> <url>`                       |

---

## 🧠 Target Mapping

| Test Case                                | Tools                                           | Feature/Command                                  |
|------------------------------------------|------------------------------------------------|--------------------------------------------------|
| Identify weak points                     | Manual Analysis                               | Deduce from findings                             |
| Discover exploits                        | ExploitDB, OSINT                              | Use search functionality                         |
| Discover payloads                        | ExploitDB, OSINT                              | Use search functionality                         |
| Find exposed sensitive info/keys         | Manual Analysis                               | Check config files, leaked data                  |
| Prepare custom exploits                  | Metasploit, Msfvenom                          | Choose suitable modules                          |
| Prepare dictionary lists                 | CeWL, Crunch, Combinator                      | `cewl -d 2 -m 5 -w docswords.txt <URL>`          |

---

## 💥 Exploitation

| Test Case                                | Tools                                           | Feature/Command                                  |
|------------------------------------------|------------------------------------------------|--------------------------------------------------|
| Perform MAC flooding                     | Macof                                          | `macof -i eth0`                                  |
| DHCP attacks                             | DHCPig                                         | `pig.py <interface>`                             |
| MITM attacks                             | MITMf, Bettercap                              | `bettercap -iface wlan0`                         |
| DNS/ARP spoofing                         | Ettercap, arpspoof                            | Use ARP poisoning and DNS spoof plugins          |
| Exploit vulnerabilities                  | Metasploit, Msfvenom                          | `use exploit/...`                                |
| Crack WEP IV vector                      | Cain & Abel, Aircrack-ng                      | `aircrack-ng <pcap>`                             |
| DOS Attacks                              | Hulk, Hping, Pyloris                          | `pyloris -t -c <IP>`                             |

---

## 🔓 Gaining Access

| Test Case                                | Tools                                           | Feature/Command                                  |
|------------------------------------------|------------------------------------------------|--------------------------------------------------|
| Access network services                  | Netcat, Putty, Metasploit                     | `nc -l <IP>`                                     |
| Brute-force login credentials            | Hydra, Cain & Abel, JTR                       | `hydra -l user -P passlist.txt <IP>`             |
| Identify system/admin/root users         | PowerShell, Terminal                          | Windows: `Get-WmiObject ...`<br>Linux: check `/etc/passwd` |
| Privilege escalation                     | BeRoot, PrivEsc, Traitor, Potato              | Execute respective tool                          |
| Discover user-level info                 | Manual Analysis                               | Check folders, permissions, keys, tokens         |
| Discover internal services               | Manual Analysis                               | Intranet printers, CCTV, etc.                    |

---

## 📦 Post - Exploitation

| Test Case                                | Tools                                           | Feature/Command                                  |
|------------------------------------------|------------------------------------------------|--------------------------------------------------|
| Collect vulnerabilities info             | Nessus Pro, Snipping Tool                     | Take screenshots for reports                     |

---

## 🧹 Clearing Tracks

| Test Case                                | Tools                                           | Feature/Command                                  |
|------------------------------------------|------------------------------------------------|--------------------------------------------------|
| Clear event logs                         | Clearev, Metasploit                           | `clearev` command in session                     |
| Delete payloads/exploits/temp files      | Manual Deletion                               | Manually delete files                            |
| Remove created accounts                  | Manual Deletion                               | Revoke user access                               |
| Reset configurations                     | Manual Reset                                  | Restore default configs                          |


---

