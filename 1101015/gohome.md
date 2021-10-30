首先程式行為分析   
![1123e](https://user-images.githubusercontent.com/91378841/139539262-cf77bbdc-3919-4668-8940-3893bf93cdc6.png)   
以radare2靜態分析   
![Kali-Linux-2021 2-vmware-amd64-2021-10-30-23-16-56](https://user-images.githubusercontent.com/91378841/139539276-a77243de-abec-4e20-a04c-c05d013a5cd6.png)   
進入main看到我們的區域變數為0x20(32)，但沒看到有flag字樣
![Kali-Linux-2021 2-vmware-amd64-2021-10-30-23-19-44](https://user-images.githubusercontent.com/91378841/139539328-e3a56c96-367f-47ca-a957-2c1dfbba2f90.png)   
在前面afl的部分我們看到sym.Billyhouse進去看發現有flag字樣   
![Kali-Linux-2021 2-vmware-amd64-2021-10-30-23-20-04](https://user-images.githubusercontent.com/91378841/139539459-70457f54-4624-4da7-b06d-30ac8eb900a5.png)   
因此我們的目標則是讓程式執行到0x4006c6這部分，塞入32加上saverbp 8 個A   
![Kali-Linux-2021 2-vmware-amd64-2021-10-30-23-19-37](https://user-images.githubusercontent.com/91378841/139539525-553b62c4-25df-4245-ab00-27b94ae1a518.png)   
即可讓程式bof得到flag   
![Kali-Linux-2021 2-vmware-amd64-2021-10-30-23-20-32](https://user-images.githubusercontent.com/91378841/139539568-5acf3853-540c-48ff-9087-b49c1638beeb.png)
