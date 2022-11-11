## Description
>Here's a program that plays rock, paper, scissors against you. I hear something good happens if you win 5 times in a row.
Connect to the program with netcat:
`$ nc saturn.picoctf.net 53865`
The program's source code with the flag redacted can be downloaded here.

## Writeup
`strstr(player_turn, loses[computer_turn])`の部分にバグ。部分文字列に勝つ手が含まれていれば良い。
`rockpaperscissors`を5回送ればいい。

Flag: `picoCTF{50M3_3X7R3M3_1UCK_B69E01B8}`