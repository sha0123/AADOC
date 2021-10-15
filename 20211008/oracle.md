以Ghidra開啟oracle，並找到function裡的entry
![137347166-52704923-1f26-4eb8-a44e-89174497e04b](https://user-images.githubusercontent.com/91378841/137419657-c9bef48c-4a8d-4390-919e-513acb1dd0e5.png)
循線找到Decompile裡的Fun_00400c00，並進入
![137348475-4797c864-15a1-4999-8be6-46b6ad854b94](https://user-images.githubusercontent.com/91378841/137419685-9957c008-d2d5-45c2-8264-28bee30554f6.png)
在Fun_00400c00裡發現三個條件式中，發現最後一個條件式Fun_00401230中有level completed字樣
![Kali-Linux-2021 2-vmware-amd64-2021-10-15-00-48-25](https://user-images.githubusercontent.com/91378841/137361609-94480f0d-3039-419c-b63b-5d375bfd7f75.png)
因此我們的目標即是讓程式執行到此，而要滿足此條件，必須先讓uvar3不小於0
![InkedKali-Linux-2021 2-vmware-amd64-2021-10-14-23-24-_LI](https://user-images.githubusercontent.com/91378841/137362965-8148f0a6-f938-4335-afb9-912dd2b5461b.jpg)
因此使用gdb在0x400c45設立斷點(b *0x400c45)
![Kali-Linux-2021 2-vmware-amd64-2021-10-15-01-00-2](https://user-images.githubusercontent.com/91378841/137363336-b6c5f421-b2f2-467c-90b7-0a98e7e0bef4.png)
並將rax替換成比0大的數字，如此則可觸發Fun_00401230條件式解開Level.db
之後不會了...


