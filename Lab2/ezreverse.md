首先執行程式發現不會有任何反應   
![Kali-Linux-2021 2-vmware-amd64-2021-10-25-23-00-49](https://user-images.githubusercontent.com/91378841/138722623-7b9dd222-609b-4ed6-9448-06b00f8c8873.png)   
再任意輸入數值發現該程式會被刪除   
![Kali-Linux-2021 2-vmware-amd64-2021-10-25-23-01-26](https://user-images.githubusercontent.com/91378841/138722631-d83b7bab-d8cb-4c3e-b2bf-2ea3f9406880.png)   
我們以radare2分析該程式會發現這段疑似flag地方以及刪除程式的地方   
![Kali-Linux-2021 2-vmware-amd64-2021-10-25-23-16-21](https://user-images.githubusercontent.com/91378841/138723027-c05d12f4-29ad-43fd-a628-c0ffdfe1ed66.png)   
故以angr設法讓程式執行到0x400945並避免執行到0x400967   
![Kali-Linux-2021 2-vmware-amd64-2021-10-25-23-09-16](https://user-images.githubusercontent.com/91378841/138724239-74b70f25-104b-4aa7-bb32-fbb663365e66.png)   
於是我們便解出flag!   
![Kali-Linux-2021 2-vmware-amd64-2021-10-25-22-50-09](https://user-images.githubusercontent.com/91378841/138724350-a9b0492c-8fd6-428a-8bd2-e79c4bcc6b78.png)
