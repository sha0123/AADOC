![image](https://user-images.githubusercontent.com/91378841/146799980-b6d86dc5-f397-46b2-842a-58b76727dee2.png)   
發現到PIE是關的
嘗試執行程式
![image](https://user-images.githubusercontent.com/91378841/146799898-3e9c3d21-b617-4830-aa28-053223a56cc4.png)   
我們看到main結尾處有cmp
![image](https://user-images.githubusercontent.com/91378841/146800453-baa2a9a9-1cba-41c7-beff-cc3f463e5383.png)   
因此嘗試送0x79487ff
```python
from pwn import *
r = process("./pwntools")
r.recvuntil(':)')
r.sendline(p32(0x79487FF))
r.interactive()
```
![image](https://user-images.githubusercontent.com/91378841/146801058-6b7d3a4f-3acb-41e4-bf79-68bf2b0f1eb8.png)   
發現到後面會是1000道數學題目，且格式為 數字 運算符 數字 = ?
於是我們撰寫code

```python
from pwn import *
r = process("./pwntools")
r.recvuntil(':)')
r.sendline(p32(0x79487FF))

r.recvline()
r.recvline()
cnt = 0
while(cnt!=1000):
        cnt += 1
        s = r.recvuntil('?')
        print(s)
        arr = s.split(b' ')
        a = int(arr[0])
        b = int(arr[2])
        op = arr[1]
        res = 0
        if(op == b'+'):
                res = a+b
        elif(op == b'-'):
                res = a-b
        elif(op == b'*'):
                res = a*b
        r.sendline(str(res))
r.interactive()
```
![image](https://user-images.githubusercontent.com/91378841/146801290-b1f56ad3-ce58-4d6a-a10e-76f1062e07a4.png)
