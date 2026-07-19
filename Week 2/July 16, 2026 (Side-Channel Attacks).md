# July 16, 2026 (Side-Channel Attacks)

**Side-channel attacks** target the physical or architectural implementation of a system rather than the cryptographic algorithms themselves. 
- Attackers extract sensitive data—like passwords or encryption keys—by observing indirect, unintended side-effects of computation, such as fluctuations in power consumption, processing time, electromagnetic radiation, or acoustic emissions.
- Implementation of an algorithm can leak facts about its operations
	- How much power does it draw, and when?
	- How long does it take?

<u>Networking Side-Channels:</u>
- What's given away by completely encrypted network traffic:
	- Whom you are talking
	- When sending data
	- How big is each packet

<u>Acoustic Side-Channels:</u>
- What's given away by the noise of your keyboard:
	- Which finger you using
	- What's the timing between keypresses

<u>Attacking Key Storage in Memory:</u>

<img width="623" height="329" alt="Screenshot 2026-07-16 104128" src="https://github.com/user-attachments/assets/5612ca1e-3e9e-4e94-b2c6-f57c3a779246" />


<u>Example DES Attack:</u>

<img width="547" height="376" alt="Screenshot 2026-07-16 104636" src="https://github.com/user-attachments/assets/fca0360c-6997-49de-8187-5edb3ab53c2a" />


<u>Example - Multiplication:</u>

<img width="695" height="359" alt="Screenshot 2026-07-16 104800" src="https://github.com/user-attachments/assets/b4403cc2-ee6b-41c8-947e-bb5cfa987fe3" />


<u>Differential Analysis:</u>

<img width="546" height="350" alt="Screenshot 2026-07-16 104909" src="https://github.com/user-attachments/assets/76479c43-092c-461e-bfb0-d776dc0fc22e" />


> **Differential analysis** refers to advanced statistical methods used to extract secret cryptographic keys from physical hardware. 
> - By analyzing how a device's power consumption or electromagnetic radiation correlates with the data it processes, attackers can bypass mathematical security without altering the underlying code.

<u>Example "known-ciphertext" Attack:</u>

<img width="698" height="350" alt="Screenshot 2026-07-16 105141" src="https://github.com/user-attachments/assets/771167ec-a340-494e-8505-6e0d1fea8693" />


<u>AES Review:</u>

<img width="698" height="392" alt="Screenshot 2026-07-16 105332" src="https://github.com/user-attachments/assets/9d406268-4ed4-4735-a48d-b9cfc01bc436" />


<u>AES Final Round:</u>

<img width="701" height="358" alt="Screenshot 2026-07-16 105709" src="https://github.com/user-attachments/assets/b225aa6a-09b3-4bf9-938f-56a00046761d" />


<u>Known-Ciphertext DPA Attack on AES:</u>

<img width="635" height="331" alt="Screenshot 2026-07-16 123759" src="https://github.com/user-attachments/assets/75621273-d5db-4ee8-b9da-bf2a7e261791" />


