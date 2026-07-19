# July 14, 2025 (Software Reverse Engineering).md

<u>Buffer Overflows:</u>
- C language does NOT check that writes are within bounds
- Buffer Overflow = occurs when data is written OUTSIDE of the space allocated for the buffer!

> "Buffers" are just an array that stores data!

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
