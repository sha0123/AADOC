首先程式行為分析   
![r1](https://user-images.githubusercontent.com/91378841/139539949-976f6b05-974b-4728-bd8a-93f58c03f1a7.png)   
以radare2進行靜態分析   
![Kali-Linux-2021 2-vmware-amd64-2021-10-30-23-40-57](https://user-images.githubusercontent.com/91378841/139540001-e7322f9c-c1d4-4591-97ce-37d4d16e626a.png)   
發現程式沒有地方會cat flag，因此我們找地方進行bof，以gdb動態分析vmmap查看可注入的地方   
![Kali-Linux-2021 2-vmware-amd64-2021-10-30-23-49-07](https://user-images.githubusercontent.com/91378841/139540146-2ad06767-462d-4935-adda-976612338ba4.png)   
發現是0x601000至0x602000的地方是可讀可寫可執行的地方   
因此我們的目標即是將程式塞爆，再讓程式執行到shellcode位置0x601080   
![Kali-Linux-2021 2-vmware-amd64-2021-10-30-23-59-50](https://user-images.githubusercontent.com/91378841/139540746-c2c57cd8-cd8b-49e8-969d-fc465ec7628e.png)   
即可得到flag   
![Kali-Linux-2021 2-vmware-amd64-2021-10-31-00-04-27](https://user-images.githubusercontent.com/91378841/139540754-d9393bd5-ea5d-4487-8072-ca59cccb66a7.png)   
