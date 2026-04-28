# 检查驱动
我的驱动位置在/lib/modules/6.1.0-28-amd64/kernel/drivers/usb/serial/ ch341.ko  如果你的系统里相应位置有这个文件，说明驱动已经装好，否则请按照 [Linux上安装CH340驱动](https://yinxiuqu.github.io/post/Linux-shang-an-zhuang-CH340-qu-dong.html) 把驱动装好。
# 添加权限
通常ubuntu和debian等系统，普通用户没有读取访问到serial设备权限。所以，虽然装了驱动，也能发现硬件，但是通过K5Web等网站无法连接设备，总是提示连接失败。可以把当前用户加入 dialout 组：
```bash
sudo usermod -aG dialout $USER
```
然后要注销一下当前用户，重新登陆。
# 登陆K5Web网站
这是个著名的刷固件的网站，可以在线直接刷。备份、检查设备、刷固件、刷字体、刷频率、教程等功能一应俱全。网址为： [https://k5.vicicode.cn/#/chirp/base](https://k5.vicicode.cn/#/chirp/base)
进入网站后，点击右上角的连接，然后先备份，其他任何不懂的，都可以看主页上的教程连接，开启你的HAM生涯吧！