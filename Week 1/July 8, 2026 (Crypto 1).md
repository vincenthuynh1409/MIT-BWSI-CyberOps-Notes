# July 6, 2026 (Cryptography Day 1)

<u>Cryptography Outline:</u>
- **Getting Confidentiality**
- **Getting Integrity**
- **Getting Authenticity and Scalability**
- **Threats to Cryptography**
- **References**

**Alice** and **Bob** (placeholders for cryptography)
**Eve** (eavesdropper / MITM) 

<img width="698" height="382" alt="Screenshot 2026-07-08 091512" src="https://github.com/user-attachments/assets/8921c375-f7e2-422f-a171-94ac38b53ce7" />

**Permutation** = mapping from one ordering of a set to another

<u>Keyed Permutations:</u>
- Function that takes an additional argument (**"key"**) that determines the permutation
	- same KEY used forward and backwards → **Symmetrical Cryptography**
- Example:
	- **Caesar Cipher:**
		- Input = 26 characters of the alphabet (a-z)
		- Key = amount to shift the alphabet

<img width="292" height="185" alt="Screenshot 2026-07-08 204806" src="https://github.com/user-attachments/assets/a83baf34-1784-418c-8120-11ba6c85a07c" />

<u>Advanced Encryption Standard (AES):</u>
- Type of Keyed Permutation on 128-bit blocks of data!
- Block cipher
- Input = 128 bits 
- Key = 128, 192, or 256 bits
	- Use 256! 

<img width="263" height="185" alt="Screenshot 2026-07-08 205010" src="https://github.com/user-attachments/assets/4d72678b-cc20-49b6-b4a7-499a0e7437e1" />

<u>Handling Larger Messages:</u>
- **Block cipher modes** determine how to compose a block cipher
- **Electronic Code Block (ECB)** just uses the cipher, one block at a time

<img width="545" height="228" alt="Screenshot 2026-07-08 205242" src="https://github.com/user-attachments/assets/72208e70-ef1c-495d-aa24-3db23601a403" />

> Breaks the long message apart? uses same key for each part (above)

**ECB mode leaks information** :(

<img width="507" height="290" alt="Screenshot 2026-07-08 205504" src="https://github.com/user-attachments/assets/2064b9b5-d574-4997-b66f-8302af72d5ee" />

**Cyber Block Chaining:**

<img width="548" height="295" alt="Screenshot 2026-07-08 205916" src="https://github.com/user-attachments/assets/fd07f4c2-9cbc-442b-a413-6e45924aeb79" />

> Basically, its a chain, like a path. You cannot proceed with the next encryption without doing the first encryption and on and on. 

**Mallory** = malicious modder placeholder guy

<u>Getting Integrity:</u>
- **Hash function** (or **checksum function**) maps a large message to a fixed length 
- Input = infinite
- Output = fixed-length string

<u>CRC vs. "Noisy Wire":</u>
- Indicates that a problem has occurred
	- **Parity mismatch**
	- **CRC mismatch**

<img width="697" height="388" alt="Screenshot 2026-07-08 092843" src="https://github.com/user-attachments/assets/ae685bc3-6630-4db4-9673-572e1d86d00d" />


<u>Attacking Parity and CRC:</u>
- CRC and Parity are good against random errors
- Neither is adequate against malicious errors
- Requirement = collision resistance and preimage resistance

<u>Secure Hash Algorithm (SHA-2 or SHA-3):</u>
- **Secure Hash Algorithm**
	- Input = infinite 
	- Output = 384 bits
- Condensed Information representation
- Cryptographic hash function
	- **Preimage resistance** = one way, cannot infer input from output
	- **Collision resistance** = won't find inputs with matching outputs (best attack is brute force)
- Does not thwart Mallory on its own
	- Mallory can modify message and recompute hash

<u>Message Authentication Code (MAC):</u>
- Keyed-hash **message authentication code (HMAC)** includes a key that Mallory does not know in the hash computation 

<u>MAC vs. Mallory:</u>
- Message cannot be edited in undetectable manner 
- Required pre-placed keys 
- Provides authenticity, after a fashion, given that you know with whom you share a key 

<u>Limits of Shared Keys:</u>
- Number of keys gets outta control 

<u>Asymmetric Cryptography</u>:
- Two keys in the pair are generated together, at the same time
- EX: **Elliptic Curve Cryptography (ECC)**

<img width="692" height="384" alt="Screenshot 2026-07-08 093920" src="https://github.com/user-attachments/assets/db69188d-89e2-4eca-a6c3-c5644a66b9cb" />

- **"Public" and "Secret" Key**
- Public can go to New York Times lol

<img width="702" height="383" alt="Screenshot 2026-07-08 094221" src="https://github.com/user-attachments/assets/30c35f2f-dae5-4cf5-90ba-87e58f56bb42" />

<u>PKI:</u>
- **Public Key Infrastructure (PKI)**
- Trusting one issuing organization (EX: DoD)
- Holds a **Certificate**, which is a message digitally signed by the issuing organization:
	- Your public key
	- Your name, rank, address
- The Cert now associates an identity with a key, given that the recipient trusts the certificate issuer!

<u>Key Wrapping:</u>
- Mitigates the performance hit of asymmetric cryptography when encrypting large messages 
	- Pick random symmetric key, and encrypt the message with it
	- Encrypt the symmetric key with the asymmetric key
- EX: send "War and Peace" to chuck

<u>Types of Attacks:</u>
- Insider threat
- Brute force (but takes 2^255 tries)
- Cryptanalysis attacks the algorithm's mathematics 
	- Frequency
	- Linear and differential cryptanalysis
- Attacks on physical implementation

<u>What is Steganography?</u>
- art of hiding data in plain sight
- embedding secret messages inside a cover text

<img width="645" height="361" alt="Screenshot 2026-07-08 103026" src="https://github.com/user-attachments/assets/db245f39-0132-49c9-bd7a-97a463fb94b1" />

> **M/L Significant Bits** = changing the bits (0s and 1s) to barely change the color but it is actually changed, concealing the secret message
