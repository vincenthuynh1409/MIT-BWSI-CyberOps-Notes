# July 10, 2026 (Microelectronics + Networking)

<u>MICROELECTRONICS - Targets of Cyber Attackers in Microelectronics:</u>
- Effects of Cyber Attacks:
	- **Disruption of business**
	- **Intellectual Property (IP) theft**
- Types of IP in Microelectronics:
	- **Process Technology** = device integration flow, process design kits (PDK), design rules, etc
	- **Fabrication Technology** = materials, process flow, processing conditions, specifications/tolerances, etc
	- **Hardware Deliverables** = processed wafers, photolithography masks, reports, etc
	- **Software Deliverables** = design tape-out files, process control plans, failure mode effects analyses, analytical results, data, etc

<u>NETWORKING - OSI Layers:</u>



<u>Address Resolution Protocol (ARP):</u>
- Part of Network Layer (3) 
	- bridges Layer 2 (Data Link Layer) and Layer 3 (Network Layer)
	- Request = "Who has 10.0.0.2? Tell 10.0.0.1"
	- Reply = "10.0.0.2 is at AA:BB:CC:DD:EE:FF"
```bash
$ arp 
```
> "arp" command = **view and manipulate the system’s Address Resolution Protocol (ARP) cache**, which stores the mappings between IPv4 addresses and physical hardware (MAC) addresses.

<u>Private IPv4 Address:</u>
- introduced to slow **IPv4 Address Allocation Exhaustion** 
- Has Security Properties:
	- **10.0.0.0/8**
	- **172.16.0.0/12**
	- **192.186.0.0/16**

<u>Network Address Translation (NAT):</u>
- **Static NAT (1:1)**
	- Each private IP corresponds to a specific public IP address
- **Dynamic NAT (1:1)**
	- Private IP receives a public IP address in round-robin pool
	- Association rotates based availability
- **Overloaded NAT (1: many)**
	- aka **PAT (Port Address Translation)**
	- IP header is modified on outbound packet to have a public Source IP and Port 
	- Public Source IP and Port belong to the NAT gateway
	- NAT Gateway keeps a table to translate the Source Port back to the private IP and Port

<u>IPv4 Attacks:</u>
- **Dotless IP Notation:**
	- Every website has an IP Address
	- IP addresses are converted from 32-bits to decimal values 
- **Given:**
	- IPv4 = a . b. c. d
	- Dotless = a * 256^3 + b * 256^2 + c * 256^1 + d * 256^0 
- EX (**Google DNS):**
	- IPv4 = https://8.8.8.8/
	- Dotless = https://134744072/

<u>Internet Control Message Protocol (ICMP):</u>
- **ICMP** = network layer protocol used by devices like routers to exchange error messages and operational status. It powers essential troubleshooting tools like `ping` and `traceroute` to verify connectivity and measure latency.
```bash
$ traceroute [IP Address or DNS]
```
> The `traceroute` command in Linux maps the exact path your data packets take to reach a destination IP or domain. It is used to troubleshoot network bottlenecks, identify latency issues, and see which specific routers are dropping your connection.

<u>Unreliable Datagram Protocol (UDP):</u>
- **UDP** = lightweight, connectionless internet protocol that prioritizes speed over reliability. By sending data packets directly without a formal connection/initial handshake or delivery confirmation, UDP minimizes latency, making it ideal for real-time applications like live video streaming, VoIP calls, and online gaming.
- Header: 
![[Screenshot 2026-07-10 105138.png]]

<u>Transmission Control Protocol (TCP):</u>
- **TCP** = networking standard that guarantees reliable, ordered, and error-checked delivery of data between applications across IP networks. Working alongside the Internet Protocol (IP), it ensures data is not lost or corrupted by organizing, tracking, and automatically retransmitting missing packets.
- Built-in error correction
- Responsible for data re-assembly and segment reordering

![[Screenshot 2026-07-10 105350.png]]

<u>TCP Attacks:</U>
- **"Teardrop Attack"** 
	- DoS (Denial of Service)
	- Attacks reassembly functionality
	- Create overlapping segments to confuse target
	- Data cannot be reassembled 
	- Reources exhausted
- **SYN Flood:**
	- Exhaust sockets of target machine with half-open connections

<u>TCP Ports:</u>
- Services are expected on particular port numbers below 1024 
	- **22 = Secure Shell (SSH)**
	- **23 = Telnet**
	- **25 = Simple Mail Transport Protocol (SMTP)**
	- **53 = Domain Name System (DNS)**
	- **80 = Hypertext Transport Protocol (HTTP)** 
	- **143 = Internet Message Access Protocol (IMAP)**
	- **443 = "Secure" HTTP (HTTPS)** 

<u>Domain Name System (DNS):</u>
- Hierarchical Distributed System
	- Elegantly handles compression of response
		- www.mit.edu
		- ist.mit.edu
		- web.mit.edu
- Best-effort protocol

<u>DNS Squatting:</u>
![[Screenshot 2026-07-10 124813.png]]

<u>Simple Mail Transport Protocol (SMTP) Agents:</u>
- **MUA (Mail User-Agent)** = client software either web/application
- **MSA (Mail Submission Agent)** = checks for errors
- **MTA (Mail Transfer Agent)** = manages movement between mail servers and MDA
- **MDA (Mail Delivery Agent)** = moves email to server-side inboxes

> Remember, we are just sending ASCII (7-bit) TEXT

<u>Simple Mail Transport Protocol (SMTP) - Mail Authentication:</u>
- **DKIM (Domain Keys Identified Mail):**
	- Applies digital DKIM signature
- **SPF (Sender Policy Framework):**
	- Checks matching IP addresses in Mail From and DNS
	- Applies to Mail-From Address Domain
		- Return-path Address (email bounce deliveries)
- **DMARC (Domain-based Message Authentication, Reporting, & Conformance):**
	- Improvement on DKIM and SPF
	- Verifies sender authenticity

> Remember, we are just sending ASCII (7-bit) TEXT

<u>Analyzing Email Headers:</U>
![[Screenshot 2026-07-10 130903.png]]

<u>HyperText Transfer Protocol (HTTP):</U>
- **Stateless Protocol:**
	- REMEMBERS nothing and FETCHES content 
	- typically uses markup languages (HTML, XML) to define content
	- replies on JavaScript + Cookies to give STATE
	- Commonly uses CSS to provide presentation
	- Methods = **GET / POST / PUT / DELETE / HEAD / TRACE / OPTIONS / CONNECT**
	- HTTP = unencrypted, Port 80 / TCP
	- HTTPS = encrypted, Port 443 / TCP
- **Apache**
	- /var/www/html/
- **Windows IIS**
	- C:\inetpub\wwwroot
- **Default Homepage defined by:**
	- index.html

![[Screenshot 2026-07-10 131418.png]]

![[Screenshot 2026-07-10 132600.png]]

<u>HTTP - JavaScript:</u>
- **In line:**
	- Single line of JavaScript
- **Embedded:**
	- Multiple lines or code-block of JavaScript in HTML code between head or body tags (below):
	- ```HTML
	  <head></head> and <body></body> 
	  ```
- **External:**
	- HTML code refers to JavaScript file elsewhere (locally on-server or remote)
	- ```HTML
	  <script src="scripts/local_script.js"></script>
	  
	  <script src="www.example.com/scripts/remote_script.js"></script>

	  ```
<u>Cryptography at (almost) every level:</u>
![[Screenshot 2026-07-10 133236.png]]

<u>Transport Layer Security (TLS):</u>
- simplifies the exchange by combining several actions into 1x step 
- Client initiates contact with a client-hello, key-share
- Server responds with a Server-hello, key-share
- Client checks certificate of Server, generate keys, done 
- Client starts requesting resources

<u>Virtual Private Network (VPN):</u>
- **Client-to-Site:**
	- Creates secure tunnel to site network
	- Receive a private IP inside site's network
- **Site-to-Site:**
	- Bridges two geographically separated networks
	- Connected through VPN Concentrator 
		- Whole network traffic funneled through
		- Sharing same private IP space
		- Sharing one logical network
		- Different egress points
		- Individually different external IP addresses

<u>Proxy Server:</u>
- **Forward Proxy:**
	- Caches web requests for clients to save bandwidth
	- Can be a security control 
		- gateway proxy to filter out web content 
	- Client use Proxy External IP Address
- **Reverse Proxy:**
	- Assists in load-balancing access to services for clients 
	- Spreads traffic across multiple geographically separated servers
	- Facilitates rapid delivery of content 
	- Usually securitizes high-volume traffic to detect DDoS (Distributed Denial of Service)
	- Used by many **Content Delivery Networks (CDNs)**
		- Cloudflare, Fastly, Akamai

<u>TOR:</u>
![[Screenshot 2026-07-10 135825.png]]


