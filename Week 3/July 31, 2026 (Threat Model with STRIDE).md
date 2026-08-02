# July 31, 2026 (Threat Model with STRIDE).md

<u>What is Threat Modeling?:</u>
- **What are we protecting?**
	- system, its assets, and its attack surface
- **What can go wrong?**
	- Enumerate threats + STRIDE
- **What can be done?**
	- Choose and design mitigations
- **Did we do a good job?**
	- Validate, revisit as the system changes

<u>STRIDE Categories:</u>
- **Spoofing**
	- Pretending to be someone you are not
	- *Breaks: Authentication*
- **Tampering**
	- Changing data without permission
	- *Breaks: Integrity*
- **Repudiation**
	- Denying you did something
	- *Breaks: Non-Repudiation*
- **Info Disclosure**
	- Leaking secrets to wrong eyes
	- *Breaks: Confidentiality*
- **Denial of Service**
	- Jamming things up for everyone
	- *Breaks: Availability*
- **Elevation of Privilege**
	- Sneaking to higher access level
	- *Breaks: Authorization*

<u>STRIDE EXAMPLES:</u>
- **Spoofing:**
	- Phishing page or stolen session token impersonates a real user
	- Mitigation → Multi-Factor Authentication (MFA), Certificate Validation, Signed Session Tokens, etc.
- **Tampering:**
	- SQL injection or MITM (Man-In-The-Middle) attack modifies data in transit or in the database
	- Mitigation → Input Validation, TLS, Checksums, Signed Data
- **Repudiation:**
	- A user denies making a change, and there is no log to prove otherwise
	- Mitigation → Secure, tamper-evident audit logs with timestamps
- **Information Disclosure:**
	- A misconfigured cloud storage bucket or wordy/long error message leaks user records
	- Mitigation → Encryption at rest & in transit, least-privilege access, careful error handling
- **Denial of Service:**
	- Flood requests (DDoS = Distributed Denial of Service) or a resource-exhaustion bug knocks a service offline
	- Mitigation → Rate limiting, load balancing, DDoS protection / CDN (Content Delivery Network)
- **Elevation of Privilege:**
	- A bug (like an IDOR) lets a normal user perform admin-only actions
		- Mitigation → Least-privilege, strict server-side access checks, patching

<u>Data Flow Diagrams:</u>

<img width="1244" height="678" alt="Screenshot 2026-07-31 092113" src="https://github.com/user-attachments/assets/3654e807-bec8-4dc7-8f1f-5a73195af002" />


<u>STRIDE applied to login system:</u>

<img width="1269" height="504" alt="Screenshot 2026-07-31 092155" src="https://github.com/user-attachments/assets/679a3037-34a0-463a-87d7-d3f2869a9a67" />


