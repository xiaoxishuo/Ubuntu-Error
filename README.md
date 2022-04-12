# Ubuntu-Error
- ###问题描述：  
  对回收站内容restore后，系统卡死，强制重启后进不了ubuntu桌面且一直只有_在黑屏左上角闪烁
- ###尝试思路：  
  1、recovery mode下尝试fsck、dpkr、resume，问题依旧  
  2、root权限下startx https://blog.csdn.net/nikoong/article/details/54235130  
  3、查看驱动是否有误，输入```nvidia-smi```后，显示```NVIDIA-SMI has failed because it could't comuunicate with NVIDIA driver```，  尝试```sudo apt-get dkms```和```sudo dkms install -m nvidia -v 470.103.01```后依旧failed( https://blog.csdn.net/xiaojinger_123/article/details/121161446)   
  ![572544909345025619](https://user-images.githubusercontent.com/50411703/162889562-960bb182-ce07-4c7f-8bc0-3dd3d22b7c54.jpg)

  4、尝试安装图形化见面  
     输入```sudo apt-get install ubuntu-dedsktop```和```sudo apt-get install unity```后，发现报错：```you don't have enough free space in /var/cache/apt/archives```  
     ![71567273962937700](https://user-images.githubusercontent.com/50411703/162889530-d541be13-48fe-46fe-a55e-d6ca6033419c.jpg)

     为了解决这个问题，进行了```sudo apt autoclean``` ,并参考了https://blog.csdn.net/t46414704152abc/article/details/116234182 创建了软连接    
  5、但是再次输入```sudo apt-get install unity```后，出现新的报错```Archives directory /var/cache/apt/archives/partial is missing```，它建议我使用```sudo apt autoremove```，使用后问题依旧存在  
![689123203101357802](https://user-images.githubusercontent.com/50411703/162889402-2c34c70d-814b-4687-ba83-09fffdb6730e.jpg)
