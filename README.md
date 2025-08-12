📚 Scanning Networks – Zero to Hero Master Notes
1. What is Scanning?
Scanning means finding details about a target network after you’ve identified it in the footprinting stage.
It’s like checking all the doors and windows of a house to see which ones are open.

Purpose:

Find live hosts (computers/devices that are ON)

Find open ports (doorways into a system)

Find services running on those ports (e.g., web server, FTP, SSH)

Find vulnerable services (weak points for attack)

2. Types of Scanning
A. Network Scanning
Finds live devices on the network.

Tools: Angry IP Scanner, Netdiscover, Nmap, hping3.

Methods:

Ping Sweep – Sends ICMP packets to see which devices respond.

ARP Scan – Uses ARP requests to find devices in local network.

B. Port Scanning
Checks which ports are open or closed.

Finds the service running on each port.

Tools: Nmap, SuperScan, Zenmap.

Port Number Basics:

0–1023 → Well-known ports (HTTP 80, HTTPS 443, FTP 21, SSH 22)

1024–49135 → Random/Registered ports

49136–65535 → Experimental/private ports

3. Live Host Discovery
Goal: Identify which machines are turned on.

Techniques:

ICMP Ping – Like saying “Hello, are you there?”

ARP Requests – Works within local networks.

TCP/UDP Ping – Using ports instead of ICMP.

Practical Tools & Commands:

bash
Copy
Edit
fping -aqg 192.168.0.1/24
sudo netdiscover -r 192.168.0.1/24
sudo arp-scan 192.168.0.1/24
Angry IP Scanner → GUI tool, shows live hosts with a green dot.

4. TCP & UDP Basics
TCP – Reliable, connection-based. Needs 3-way handshake:

SYN → Start

SYN-ACK → Acknowledge

ACK → Confirm and start communication

UDP – Fast but unreliable, no handshake. Used for streaming, voice, video.

5. Port Scanning Techniques
1. TCP Connect Scan (Full Open)
bash
Copy
Edit
nmap -sT <IP>
Fully connects to the port → detectable.

2. SYN Scan (Half-Open / Stealth)
bash
Copy
Edit
sudo nmap -sS <IP>
Sends SYN, waits for SYN-ACK, then drops connection → stealthy.

3. ACK Scan (Firewall Detection)
bash
Copy
Edit
sudo nmap -sA <IP>
Finds firewall rules, not open ports.

4. XMAS Scan
bash
Copy
Edit
sudo nmap -sX <IP>
Sends packets with FIN, PSH, URG flags.

5. FIN Scan
bash
Copy
Edit
sudo nmap -sF <IP>
6. NULL Scan
bash
Copy
Edit
sudo nmap -sN <IP>
7. UDP Scan
bash
Copy
Edit
sudo nmap -sU <IP>
8. Service Version Detection
bash
Copy
Edit
sudo nmap -sV <IP>
9. OS Detection
bash
Copy
Edit
sudo nmap -O <IP>
10. Aggressive Scan
bash
Copy
Edit
sudo nmap -A <IP>
6. Common Ports & Services
Service	Port
HTTP	80
HTTPS	443
FTP	20,21
SSH	22
DNS	53
SMTP	25
POP3	110
MYSQL	3306
RDP	3389

7. Countermeasures
Block ICMP and UDP inbound

Disable unused ports

Use IDS/IPS to detect and prevent attacks

Keep OS updated

Hide system banners

8. Practicals with Screenshot Placeholders
Practical 1: fping
bash
Copy
Edit
fping -aqg 192.168.1.57/24

Practical 2: Angry IP Scanner

Practical 3: netdiscover
bash
Copy
Edit
sudo netdiscover -r 192.168.0.1/24

Practical 4: arp-scan
bash
Copy
Edit
sudo arp-scan 192.168.0.1/24

Practical 5: Nmap
Examples:

bash
Copy
Edit
nmap -sT 192.168.0.16
sudo nmap -sS 192.168.0.16
sudo nmap -sV 192.168.0.16

9. Tools for Scanning Networks
Tool Name	Type	Main Use	Website
Nmap	CLI	Port scanning, service detection, OS detection	nmap.org
Zenmap	GUI	GUI for Nmap	nmap.org/zenmap
Angry IP Scanner	GUI	Fast IP & port scanning	angryip.org
Netdiscover	CLI	ARP-based live host discovery	Pre-installed in Kali/Parrot
arp-scan	CLI	ARP-based host discovery	linux.die.net/man/1/arp-scan
fping	CLI	Fast ping sweep	fping.org
hping3	CLI	Custom packet crafting	github.com/antirez/hping

10. Websites & Online Tools
Website	Main Use	Link
Shodan	Search engine for devices	shodan.io
Censys	Internet-wide scanning	censys.io
YouGetSignal	Online port scanning	yougetsignal.com
DNSdumpster	Finds subdomains	dnsdumpster.com
SecurityTrails	DNS & IP history	securitytrails.com
