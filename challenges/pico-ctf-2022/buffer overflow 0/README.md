## Description
> Smash the stack
Let's start off simple, can you overflow the correct buffer? The program is available here. You can view source here. And connect with it using:
nc saturn.picoctf.net 65355

## Writeup

`SIGSEGV`が起きるとフラグが出力されるので、適当に長い文字列を送る。

Flag: `picoCTF{ov3rfl0ws_ar3nt_that_bad_34d6b87f}`