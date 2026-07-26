# July 20, 2026 (Transduction)

**Processors, memory, CPUs, and DIMMs** are central hardware components in **confidential computing** and physical hardware security, where modern exploits target the data path between the chip and physical sticks. 

> Note: **"Transduction"** typically refers to energy conversion or genetic transfer, but in this hardware-security context, it aligns with data transit and processing across the memory bus

Hardware Security Roles:
- **CPU (Central Processing Unit):** Acts as the root of trust, containing secure enclaves (like Intel SGX or AMD SEV) and hardware engines that generate encryption keys.
- **Processors / Memory Controllers:** Integrated controllers inside the processor encrypt plaintext data before it leaves the CPU pins and decrypt it on return, preventing bus-snooping.
- **DIMM (Dual In-line Memory Module):** The physical RAM stick plugged into the motherboard; while traditionally vulnerable to cold-boot or physical removal attacks, it is shielded in secure architectures by holding only ciphertext.

<u>GSMem - RF via Memory Accesses:</u>
- **GSMem** is a sophisticated malware technique designed to exfiltrate data from physically isolated, air-gapped computers over cellular frequencies by modulating memory bus activity into electromagnetic radiation. It uses specific memory instructions and multichannel memory architectures to turn the hardware into a wireless transmitter intercepted by a nearby mobile phone
	- Example Below:

<img width="647" height="361" alt="Screenshot 2026-07-20 101321" src="https://github.com/user-attachments/assets/37cd6626-b0e1-4df5-b788-57cff1de0d00" />


<u>RAMBLE:</u>
 - **RAMBLE** is a severe side-channel attack that allows an attacker to steal sensitive data directly from a computer’s physical memory (DRAM). While previous memory attacks used the famous **Rowhammer vulnerability** to write or alter data, RAMBleed leverages it to read

<img width="650" height="364" alt="Screenshot 2026-07-20 101415" src="https://github.com/user-attachments/assets/ade739ea-d19c-47da-8b85-28f78a048155" />


<u> Inside DRAM:</u>

<img width="538" height="325" alt="Screenshot 2026-07-20 101502" src="https://github.com/user-attachments/assets/2a5594f0-7a50-46e3-ae94-dcb6621e4454" />


- Inside a **DRAM (Dynamic Random-Access Memory)** chip, cybersecurity concerns primarily center around physical hardware vulnerabilities and electrical leakage between microscopic components. Key areas of focus include **Rowhammer**, **charge leakage**, and **sense amplifiers**.

- Architecture and Physical Vulnerabilities:
	- **Memory Cells:** Millions of tiny capacitor and transistor pairs store individual bits as an electrical charge. Because capacitors naturally leak electricity, they require constant refreshing. []
	- **Rowhammer Effect:** Rapidly and repeatedly reading a specific row of memory (the "aggressor row") generates electrical disturbances that cause charge leakage in neighboring rows, flipping bit values from 0 to 1 or vice versa. []
	- **Side-Channel Exploits:** Attacks like RAMBleed exploit these hardware-induced bit flips to covertly read sensitive data—such as cryptographic keys or other processes—across logical security boundaries on the same physical chip.

<img width="637" height="359" alt="Screenshot 2026-07-20 101514" src="https://github.com/user-attachments/assets/7da2c739-a97f-4a82-99d5-ee17e258b0e2" />


- **A DRAM** cell is the smallest unit of computer memory, consisting of exactly one transistor and one capacitor (known as a 1T1C cell) to store a single bit of data.
	- **The Capacitor**: Stores the actual data as an electrical charge. A fully charged state typically represents a binary **1**, while an uncharged state represents a binary **0**.
	- **The Transistor**: Acts as an electronic switch. It controls access to the capacitor, opening or closing the path to read or write data

<u>PowerHammer:</u>
- **PowerHammer** is a specialized covert data exfiltration attack that steals data from isolated, "air-gapped" computers using electrical power lines. By rapidly changing a computer's CPU workload, malware alters its power consumption to send hidden signals through power cables.

<img width="431" height="326" alt="Screenshot 2026-07-20 101741" src="https://github.com/user-attachments/assets/3179a5aa-0040-47de-8f92-45ffc7e8b112" />


<u>Light Commands:</u>
- **Light Commands** refer to a novel class of security exploits where attackers use invisible, amplitude-modulated laser light beamed at smart device microphones to silently inject remote voice commands.

<img width="646" height="355" alt="Screenshot 2026-07-20 102127" src="https://github.com/user-attachments/assets/fde47bf2-e18c-4487-9b05-5d0a9b16ef04" />


