# Ubuntu-Error
- 问题描述：
  对回收站内容restore后，系统卡死，强制重启后进不了ubuntu桌面且一直只有_在黑屏左上角闪烁
- 尝试思路：
  1、recovery mode下尝试fsck、dpkr、resume，问题依旧
  2、root权限下startx
  3、查看驱动是否有误，输入```nvidia-smi```后，显示```NVIDIA-SMI has failed because it could't comuunicate with NVIDIA driver```
     按照。。。尝试```sudo apt-get dkms```和```sudo dkms install -m nvidia -v 470.103.01```后依旧failed
  4、尝试安装图形化见面
     输入```sudo apt-get install ubuntu-dedsktop```和```sudo apt-get install unity```后，发现报错：```you don't have enough free space in /var/cache/apt/archives```
     为了解决这个问题，进行了```sudo apt autoclean``` ,并参考了。。。创建了软连接
     但是再次输入```sudo apt-get install unity```后，出现新的报错```Archives directory /var/cache/apt/archives/partial is missing```，它建议我使用```sudo apt autoremove```，使用后问题依旧存在
