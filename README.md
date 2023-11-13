# pwn

## Environments
- [Ubuntu 22.04](environments/ubuntu22.04/Dockerfile)

## Exploits
| Challenge (A-Z)                                                                             | Keyword                                                          |
| ------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| [Cyber Security Rumble 2022: pwnmeplx](challenges/CyberSecurityRumble2022/pwnmeplx/)        | ROP                                                              |
| [picoCTF 2021: Here's a LIBC](challenges/picoCTF2021/Here's%20a%20LIBC/)                    | ROP, libc leak, one gadget                                       |
| [picoCTF 2021: Stonks](challenges/picoCTF2021/Stonks/)                                      | UFS, stack dump                                                  |
| [picoCTF 2022: buffer overflow 0](challenges/picoCTF2022/buffer%20overflow%200/)            | BOF, `gets`                                                      |
| [picoCTF 2022: function overwrite](challenges/picoCTF2022/function%20overwrite/)            | negative value, write-what-where, array bounds, function pointer |
| [picoCTF 2022: ropfu](challenges/picoCTF2022/ropfu/)                                        | ROP, shellcode                                                   |
| [picoCTF 2022: RPS](challenges/picoCTF2022/RPS/)                                            | `strstr`                                                         |
| [picoMini by redpwn: clutter-overflow](challenges/picoMini%20by%20redpwn/clutter-overflow/) | BOF, `gets`                                                      |
| [ROP Emporium: 1. ret2win (x64)](challenges/ROPEmporium/1_ret2win-x64/)                     | ROP                                                              |
| [ROP Emporium: 2. split (x64)](challenges/ROPEmporium/2_split-x64/)                         | ROP, `system`                                                    |
| [ROP Emporium: 3. callme (x64)](challenges/ROPEmporium/3_callme-x64/)                       | ROP                                                              |
| [ROP Emporium: 4. write4 (x64)](challenges/ROPEmporium/4_write4-x64/)                       | ROP, write-what-where                                            |
| [ROP Emporium: 5. badchars (x64)](challenges/ROPEmporium/5_badchars-x64/)                   | ROP, write-what-where, bad chars                                 |
| [ROP Emporium: 6. fluff (x64)](challenges/ROPEmporium/6_fluff-x64/)                         | ROP, write-what-where, `bextr`, `xlatb`, `stosb`                 |
| [ROP Emporium: 7. pivot (x64)](challenges/ROPEmporium/7_pivot-x64/)                         | ROP, stack pivot                                                 |
| [ROP Emporium: 8. ret2csu (x64)](challenges/ROPEmporium/8_ret2csu-x64/)                     | ROP, ret2csu                                                     |

Note
- BOF: Buffer Overflow
- ROP: Return-Oriented Programming
- UFS: Uncontrolled Format String
