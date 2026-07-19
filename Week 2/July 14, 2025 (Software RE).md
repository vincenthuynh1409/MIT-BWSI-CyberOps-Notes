# July 14, 2025 (Software Reverse Engineering).md

<u>Buffer Overflows:</u>
- **C language** does NOT check that writes are within bounds
- **Buffer Overflow** = occurs when data is written OUTSIDE of the space allocated for the buffer!

> **"Buffers"** are just an array that stores data!

<u>Buffer Overflow Example:</u>
```C
void foo(char *str) {
	char buffer[16];
	strcpy(buffer, str);
}

void main() {
	char buf[256];
	memset(buf, 'A', 255);
	buf[255] = '\x00';
	foo(buf);
}
```
> **So, what's happening?**
> 
> - so in `foo()`, `buffer[16]` is created, meaning it's buffer can hold 16 characters
> - and in `main()`, `buf[256]` is created, and it is larger
> - `memset()` fills memory, so in  `memset(buf, 'A', 255)`, every byte becomes the letter A:
> 	- `AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA...` (255 times)!
> - then, `buf[255] = '\0';` adds the "null" terminator, so the string becomes:
> 	- `AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA...\0`
> 	- Length: 255 A's
> - then, `foo(buf);`, meaning this HUGE string of A's is passed into `foo()`!
> - so, `strcpy(buffer, str);` copies all 255 char into a 16-byte buffer, and since `strcpy()` does not check destination size, it keeps writing past the end of `buffer`
> - finally, buffer overflow occurs:
> 
> Before:
> | buffer (16 bytes) |  other stack data |  return address |
> 
> After:
| AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA... |
              ↑ Overwrites nearby memory

> The extra data can overwrite important stack data, including the **return address**. This often causes the program to **crash**, and on vulnerable systems it could potentially allow an attacker to redirect the program's execution.

<img width="631" height="332" alt="Screenshot 2026-07-14 125234" src="https://github.com/user-attachments/assets/50958112-3c1f-42ab-91a6-eebc51ae3728" />

<u>What is an Operating System?:</u>
- Program that acts as an intermediary between a user of a computer and the computer hardware!
- **Goals:**
	- Execute user programs and make solving user problems easier
	- Make the computer system convenient to use
	- Use the computer hardware in an efficient manner
	- Provide protection and security
- EX: Linux, Windows, MacOS, etc

<img width="563" height="332" alt="Screenshot 2026-07-14 125540" src="https://github.com/user-attachments/assets/c1ce653e-77e0-464a-982b-12788a18f535" />


<img width="629" height="341" alt="Screenshot 2026-07-14 125752" src="https://github.com/user-attachments/assets/45ed2db9-8299-4a5c-a4f3-04130e27d811" />


<u>Principles of Protection:</u>
- Must consider granularity of protection:
	- **coarse-grained privilege** management is easier, simpler, but least privilege now done in large chunks
		- EX: Unix processes either have abilities of user or root
	- **fine-grained management** more complex, more overhead, but more protective
		- File ACL lists, role-based access control (RBAC)
- Domain can be user, process, procedure

<u>Permissions in Linux:</u>
- Permissions restrict access to files and directories
- View with `$ ls -l`
	- `|rwx|rwx|rwx|` > permissions for user, group, and other
- Change with `$ chmod <entity> <+/-> <permissions> <file/directory>`

| Permission | File Action | Directory Action       | `chmod` Action |
| ---------- | ----------- | ---------------------- | -------------- |
| Read       | View        | List Contents          | `r`            |
| Write      | Edit        | Create or Remove Files | `w`            |
| Execute    | Run         | Access Directory       | `x`            |

| Restriction | Description                               | `chmod` Action |
| ----------- | ----------------------------------------- | -------------- |
| User        | User Assigned Ownership of File/Directory | `u`            |
| Group       | Primary Group of Owner                    | `g`            |
| Other       | Everyone Else                             | `o`            |

<u>Privilege Separation in Linux:</u>
- `root` = account associated with the superuser
	- FULL access to ALL files and commands
	- May invoke privileged operations
	- Runs at the same privilege level as the operating system
- **Non-root accounts** restricted to:
	- full access to home directory
	- Restricted access (Read, Write, Execute) to other parts of the filesystem
	- May only invoke unprivileged operations
- `sudo
	- Requires user password
	- Runs the command as root (if user is allowed to)

<u>Fully-Automated Analysis:</u>
- **Fully automated analysis** is the process of extracting, processing, and evaluating data or physical samples using software, algorithms, or machinery with **zero manual intervention**, and in cybersecurity, using software, algorithms, and artificial intelligence to monitor, inspect, and evaluate security events, code, or network traffic without human intervention.
- Why?
	- **Sanitation:**
		- Detonate inside a controlled sandbox or VM
	- **Effortless Analysis:**
		- Upload & GO!
	- **Save Time on Common Malware:**
		- Download stage-n artifacts
		- Observe & Collect IOCs
	- **Resource Constraints:**
		- Available personnel
		- Job roles and functions
		- Dedicated funding
		- Hardware


