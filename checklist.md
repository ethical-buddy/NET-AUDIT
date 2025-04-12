Category	Test case	Tools	Feature
Reconnaisance	Find network range	angry ipscanner,advanced ipscanner	 IP Range
	Identifying access points	nmap, zenmap, sparta, nessus pro	nmap aggressive scan
	Identifying routers/switches/hubs	nmap, zenmap, sparta, nessus pro	nmap aggressive scan
	Identifying subnets	angry ipscanner	 IP Range
	Identifying Vlans	nmap, zenmap, sparta, nessus pro	nmap aggressive scan
	Identifying active hosts	angry ipscanner	 IP Range
	Performing search engine analysis	google dorks, shodan, OSINT	google dorks - use filetype,inurl,intitle,site etc
	Performing whois lookups	whois lookup	who is database
	Identifying firewalls/Honeypots	nmap, zenmap, sparta, nessus pro	 Nmap TCP ACK scan (-sA)
	Identifying Intrusion detecting systems	nmap, zenmap, sparta, nessus pro	 Nmap TCP ACK scan (-sA)
	Identifying Intrusion prevention systems	nmap, zenmap, sparta, nessus pro	 Nmap TCP ACK scan (-sA)
	Find any websites hosted	nmap, zenmap, sparta, nessus pro	nmap port scan
	Find network protocols	nmap, zenmap, sparta, nessus pro	nmap port scan
	Find network devices	angry ipscanner	 IP Range
			
Foot-Printing	Find network services	nmap, zenmap, sparta, nessus pro	 Nmap TCP ACK scan (-sA)
	Find DNS records	nslookup	nsllokup options (use ? To get)
	Find route paths	Tracert	tracert <ip address>
	Switches/ routers/ hubs Banner grabbing	nmap, zenmap, sparta, nessus pro	NMAP NSE script
	Firewall Banner grabbing	nmap, zenmap, sparta, nessus pro	Nmap TCP ACK scan (-sA)
	IDS/IPS Banner grabbing	nmap, zenmap, sparta, nessus pro	NMAP NSE script
	Network devices Banner grabbing	nmap, zenmap, sparta, nessus pro	NMAP NSE script
	Find firewall version	nmap, zenmap, sparta, nessus pro	Nmap TCP ACK scan (-sA)
	Find IDS version	nmap, zenmap, sparta, nessus pro	Nmap TCP ACK scan (-sA)
	Find IPS version	nmap, zenmap, sparta, nessus pro	Nmap TCP ACK scan (-sA)
	Find common running services in network	nmap, zenmap, sparta, nessus pro	Nmap TCP ACK scan (-sA)
	Running services information gathering	nmap, zenmap, sparta, nessus pro	Nmap TCP ACK scan (-sA)
	Find hosted websites platform	nmap, zenmap, sparta	Nmap TCP ACK scan (-sA)
	Capturing LAN network traffic	wireshark, tcpdump, bettercap	WIRESHARK LAN INTERFACE SCAN
	Capturing wireless network traffic	wireshark, tcpdump, acrylic wifi	WIRESHARK WLAN INTERFACE SCAN
	Analysing wireless network traffic	wireshark	WIRESHARK PCAP ANALYSIS
	Analysing LAN network traffic	wireshark	WIRESHARK PCAP ANALYSIS
			
Scanning	Scanning for open ports	nmap, zenmap	nmap -p- IP
	Identifying vulnerablities in running services	nmap  openvas	nmap -A --script=vulns IP
	Identifying vulnerabilities in network protocols	nmap  openvas	nmap -A --script=vulns IP
	Identifying vulnerabilities in switches/routers/hubs	nmap  openvas	nmap -A --script=vulns IP
	Identifying vulnerabilities in firewall	nmap  openvas	nmap -A --script=vulns IP
	Identifying vulnerabilities in IDS	nmap  openvas	nmap -A --script=vulns IP
	Identifying vulnerabilities in IPS	nmap  openvas	nmap -A --script=vulns IP
	Identify critical endpoints	Analysing recon & footprinting results	deducing from findings
	Identify critical servers	Analysing recon & footprinting results	deducing from findings
	Identify critical network devices	Analysing recon & footprinting results	deducing from findings
	check default credentials of routers/switches/hubs	THC Hydra, Cain & Abel, JTR	hydra -l user -P passlist.txt URL or IP
	Check default credentails of network devices	THC Hydra, Cain & Abel, JTR	hydra -l user -P passlist.txt URL or IP
			
Enumeration	Enumerate network services	nmap, zenmap	nmap -A IP
	Enumerate Hostnames	DNSenum, DNSRecon, nmap	nmap -A IP
	Enumerate user groups	powershell	get-netgpogroup
	Enumerate user accounts	finger	finger @IP
	Enumerate file paths	dirbuster, dirb	dirb -w wordlist-path url
			
Target - Mapping	Identifying weak points from gathered information	Manual analysis	Deducing from the findings
	Identifying entry points	Manual analysis	Deducing from the findings
	Discover exploits for vulnerable services	exploitDB, OSINT	use search box
	Discover exploits for vulnerable network protocols	exploitDB, OSINT	use search box
	Discover exploits for vulnerable switches/routers/hubs	exploitDB, OSINT	use search box
	Discover exploits for vulnerable firewall	exploitDB, OSINT	use search box
	Discover exploits for vulnerable IDS	exploitDB, OSINT	use search box
	Discover exploits for vulnerable IPS	exploitDB, OSINT	use search box
	Discover payloads for vulnerable services	exploitDB, OSINT	use search box
	Discover payloads for vulnerable network protocols	exploitDB, OSINT	use search box
	Discover payloads for vulnerable switches/routers/hubs	exploitDB, OSINT	use search box
	Discover payloads for vulnerable firewall	exploitDB, OSINT	use search box
	Discover payloads for vulnerable IDS	exploitDB, OSINT	use search box
	Discover payloads for vulnerable IPS	exploitDB, OSINT	use search box
	Discover exposed sensitive information	Manual findings	Deducing from the findings for sensitive information leaks
	Discover exposed sensitives keys	Manual findings	Deducing from the findings for sensitive keys leaks
	Discover exposed network keys	Manual findings	Deducing from the findings for network key leaks
	Prepare custom exploits for vulnerable services	metasploit, msfvenom	use suitable exploits/payloads in metasploit
	Prepare custom exploits for vulnerable network protocols	metasploit, msfvenom	use suitable exploits/payloads in metasploit
	Prepare custom exploits for vulnerable switches/routers/hubs	metasploit, msfvenom	use suitable exploits/payloads in metasploit
	Prepare custom exploits for vulnerable firewall	metasploit, msfvenom	use suitable exploits/payloads in metasploit
	Prepare custom exploits for vulnerable IDS	metasploit, msfvenom	use suitable exploits/payloads in metasploit
	Prepare custom exploits for vulnerable IPS	metasploit, msfvenom	use suitable exploits/payloads in metasploit
	Prepare custom dictionary list	ceWL, crunch, combinator	cewl -d 2 -m 5 -w docswords.txt URL
			
Exploitation	Identify attack surfaces	Manual findings	Deducing from findings
	Identify attack vectors	Manual findings	Deducing from findings
	Perform MAC flooding	Macof	macof [-i interface] [-s src] [-d dst] [-e tha] [-x sport] [-y dport] [-n times]
	Perform DHCP Attacks	DHCPig	pig.py <interface>
	Perform MITM attacks	MITMf, bttercap	bettercap [arguments you are using for testing]
	Perform DNS spoofing Attacks	ettercap	ettercap>MITM>ARP poisoning>sniff remote connections>plugins>DNS_spoof
	Perform ARP spoofing attacks	arp, arpspoof	arpspoof -I <interface> <target ip> <accesspoint ip>
	Exploit identified vulnerabilities in services	metasploit, msfvenom	use run command or exploit command in respective payload module
	Exploit identified vulnerabilities in network protocols	metasploit, msfvenom	use run command or exploit command in respective payload module
	Exploit identified vulnerabilities in swithces/routers/hubs	metasploit, msfvenom	use run command or exploit command in respective payload module
	Exploit identified vulnerabilities in IDS	metasploit, msfvenom	use run command or exploit command in respective payload module
	Exploit identified vulnerabilities in IPS	metasploit, msfvenom	use run command or exploit command in respective payload module
	Exploit identified vulnerabilities in communication protocols	metasploit, msfvenom	use run command or exploit command in respective payload module
	Exploit to Break IV-vector	cain & Abel, aircrack-ng	aircrack-ng <pcap file>
	Perform DOS attack	Hulk, Hping, pyloris	pyloris -t -c IP/interface
			
Gaining Access	Acccess network services	netcat, putty, metasploit	nc -l IP
	Check for default/weak credentials	THC Hydra, Cain & Abel, JTR	hydra -l user -P passlist.txt URL or IP
	Perform brute force for user credentials	THC Hydra, Cain & Abel, JTR	hydra -l user -P passlist.txt URL or IP
	Identify root/system admin user on windows	powershell	Get-WmiObject Win32_UserAccount -filter “LocalAccount=True” | Select-Object Name,FullName,Disabled.
	Identify root/system admin user on linux	Terminal	check for /etc/passwd file
	Attempt for escalation	BeRoot, PrivEsc, traitor, potato	execute beroot or potato on target
	Bruteforce for root/system admin user password	THC Hydra, Cain & Abel, JTR	hydra -l user -P passlist.txt URL or IP
	Access least privileges user account	netcat, putty, metasploit	nc -l IP
	Identify vulnerable process	Manual finding & Analysis	execute os commands ( ps command on linux)
	Perform process injection	DLL Hijacking	manual injection
	Perform DLL injection	DLL Hijacking	parse.py -d DLL  -f header file -b bumpfile
	Discover user level available information	Manual finding & Analysis	check user folders, directories, files
	Discover user level sentive information	Manual finding & Analysis	check for passwords, sensitive information
	Discover user level atuhorizations	Manual finding & Analysis	check for user level authorizations, permissions
	Discover additional internal network services	Manual finding & Analysis	check for intranet network services like printer, scanners, attendace device, CC cameras etc
	Find private keys/access keys	Manual finding & Analysis	check for ssh keys, private keys, public keys
			
Post - Exploitation	Collect vulnerabilities info of network services	nessus pro report, snipping tool	take screenshots using snipping tool
	Collect vulnerabilities info of network protocols	nessus pro report, snipping tool	take screenshots using snipping tool
	Collect vulnerabilities info of Swithces/routers/hubs	nessus pro report, snipping tool	take screenshots using snipping tool
	Collect vulnerabilities info of firewalls	nessus pro report, snipping tool	take screenshots using snipping tool
	Collect vulnerabilities info of IDS	nessus pro report, snipping tool	take screenshots using snipping tool
	Collect vulnerabilities info of IPS	nessus pro report, snipping tool	take screenshots using snipping tool
	Collect vulnerabilities info of Hosted web servers	nessus pro report, snipping tool	take screenshots using snipping tool
	Collect vulnerabilities info of wireless network	nessus pro report, snipping tool	take screenshots using snipping tool
			
Clearing Tracks	Clear event logs	clearev, metasploit	execute cleraev command in running session
	Delete uploaded payloads	Manual deletion	manual deletion
	Delete uploaded exploits	Manual deletion	manual deletion
	Delete temporary files	Manual deletion	manual deletion
	Delete any rootkits if installed	Manual deletion	manual deletion
	Remove user accounts created	Manual deletion	manual deletion of created accounts
	Reconfigure settings to original state	Manual reset	manual reconfiguring
`
