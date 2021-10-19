①以Ghidra打開blade程式，在Function中找到main  
②在main function中我們發現了printflag()字樣，執行條件是iVarl必須為0  
③於是我們記下該段程式的位置0x80486b3
![InkedKali-Linux-2021 2-vmware-amd64-2021-10-19-22-13-22_LI](https://user-images.githubusercontent.com/91378841/137929225-a79e7384-49c9-4ae6-80cc-bd477e744170.jpg)
以Gdb開啟blade後，將斷點設置在剛剛記下的0x80486b3
![1](https://user-images.githubusercontent.com/91378841/137932228-3fa17080-f01d-476c-857d-5a80b3b02024.png)
果不其然，該斷點確實如Ghidra內所顯示test eax,eax是相同的，然而目前的值是0xffffffff
![2](https://user-images.githubusercontent.com/91378841/137930911-2cd3571c-f67c-4cb5-b15d-70e21e467257.jpg)
那麼我們的目標就是將這個值設為0，即可符合條件
![4](https://user-images.githubusercontent.com/91378841/137931270-90f1dbf5-a3be-43dd-8ae8-7bfc24b42fa2.jpg)
設定完成後讓程式繼續執行，即得到本題的flag
![Kali-Linux-2021 2-vmware-amd64-2021-10-19-22-17-19](https://user-images.githubusercontent.com/91378841/137931566-6735d573-00b4-433b-9498-b60c06c139a4.png)
