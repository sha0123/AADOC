首先分析pass的程式行為   
![Kali-Linux-2021 2-vmware-amd64-2021-10-30-22-25-11](https://user-images.githubusercontent.com/91378841/139537196-db354dc2-e372-452c-adac-6455085f9862.png)  
以radare2做靜態分析，發現有0x4與0x20區域變數
![Kali-Linux-2021 2-vmware-amd64-2021-10-30-22-24-34](https://user-images.githubusercontent.com/91378841/139537719-b1fc2dc7-eb34-4b97-ab68-4b3bcf71269c.png)
我們的目標則是在可輸入的地方塞爆產生bof，0x20-0x4=32-4=28，因此寫出以下code
![Kali-Linux-2021 2-vmware-amd64-2021-10-30-23-01-15](https://user-images.githubusercontent.com/91378841/139538541-94c4fe55-df24-4c20-b83d-66575c76d72f.png)
即可得出flag
![Kali-Linux-2021 2-vmware-amd64-2021-10-30-23-03-12](https://user-images.githubusercontent.com/91378841/139538631-fe0047b4-a34f-44b7-b229-7a7a87f9c1e0.png)
