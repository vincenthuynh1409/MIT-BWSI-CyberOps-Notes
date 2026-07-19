# July 14, 2025 (Assembly & Firmware RE)

<u>Nouns / Operands:</u>
- **Data!**
- **CPU is concerned with 3 types of data:**
	- Data we directly give it as part of the instruction
	- Data that is close at hand
	- Data in storage

<u>Verbs / Operations:</u>
- `add` = adds data together
- `sub` = subtracts data 
- `mul` = multiplies data
- `div` = divides data
- `mov` = moves data into or out of storage 
- `cmp` = compare two pieces of data with each other
- `test` = test some other properties of data

<u>Assembly:</u>
- **Assembly** = direct translation of binary code ingested by the CPU hence it is very architecture dependent
- Regardless of the many assembly dialects:
```
OPERATION
OPERATION OPERAND 
OPERATION OPERAND OPERAND
OPERATION OPERAND OPERAND OPERAND
```
> Where **OPERATION** is action/process performed, and **OPERAND** is the data being manipulated/inputs receiving action!

<u>Registers:</u>
- **Registers** = very fast, temporary stores for data!
- You get several "general purpose" registers:
	- 8085 = a, c, d, b, e, h, l
	- 8086 = ax, cx, dx, bx, **sp**, **bp**, si, di
	- x86 = eax, ecx, edx, ebx, **esp**, **ebp**, esi, edi
	- amd64 = rax, rcx, rdx, rbx, **rsp**, **rbp**, rsi, rdi, r8, r9, r10, ... , r15
	- arm = r0, r1, r2, r3, ... , r12, **r13**, **r14**
- The address of the next instruction is in the a register:
	- `eip (x86), rip (amd64), r15 (arm)`

<u>Register Size:</u>
- Registers are typically the same size as the word width of the architecture 
- On a 64-bit architecture (most) registers will hold 64 bits (8 bytes)

| 10110110 | 10101010 | 000010110 | 1010010101 | 1010101010 | 1011010011 | 11110101 | 101010101 |
| :------- | :------: | --------: | ---------- | ---------- | ---------- | -------- | --------- |

<u>Memory Endianess:</u>
- Data on most modern systems is stored backwards, in **little endian** 

`mov eax, 0xc001ca75` > sets rax to > `| c0 | 01 | ca | 75 |`
`mov rcx, 0x10000`
`mov [rcx], eax` > stores data as > `| 75 | ca | 01 | c0 |`
`mov bh, [rcx]` > reads 0x75

- Bytes are only shuffled for multi-byte stores and loads of registers to memory!
- Individual bytes NEVER have their bits shuffled!
- Yes, writes to the stack behave just like any other write to memory

<u>Setting Registers:</u>
- You load data into registers with ASSEMBLY! `mov` means **"move"!**
```Assemblty
mov rax, 0x539
mov rbx, 1337
```
- Data specified directly in the instruction like this is called "Immediate Value".
- You can also load data into partial registers:
```Assembly
mov ah, 0x5
mov al, 0x39
```

<u>Shunting Data Around:</u>
- You can also `mov` data between registers!

> NOTE: `mov` doesn't move the data, it copies it!!!

- This (below) sets `rax` and `rbx` to `0x539` (1337):
```Assembly
mov rax, 0x539
mov rbx, rax
```
- You can `mov` partials!
- This (below) sets `rax` to `0x539` and `rbx` to `0x39`
```Assembly
mov rax, 0x539
mov rbx, 0
mov bl, al
