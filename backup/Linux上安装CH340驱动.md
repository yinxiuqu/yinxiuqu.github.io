最近给泉盛UV-K6刷频，安装刷频线后，不能识别，于是寻找和安装了Linux系统下的CH340驱动。
# 插入硬件
先插入硬件看是否正常，插入后在Linux终端运行如下操作查看硬件信息：
```shell
lsusb
```
正常的话，应该看到USB的VID等信息。并且在系统/dev/文件夹下能看到类似"ttyCH341USBx"的设备。
# 驱动下载
驱动从南京沁恒微电子股份有限公司官网下载，[https://www.wch.cn/downloads/CH341SER_LINUX_ZIP.html](https://www.wch.cn/downloads/CH341SER_LINUX_ZIP.html)
# 驱动安装
解压缩后，从Linux终端进入解压缩后的/driver/文件夹。运行如下操作：
```shell
make
```
如果正常运行的话，会产生一个名为"ch341.ko"的文件。
# 临时载入驱动
接下来，如果你只想每次连接CH340设备的时候才载入驱动，可以如下操作：
```shell
sudo make load
```
连接结束后，运行如下操作卸载驱动：
```shell
sudo make unload
```
# 永久载入驱动
如果想让CH340驱动永久运行在系统上，可以如下操作：
```shell
sudo make install
```
如果要永久卸载CH340驱动，可以如下操作：
```shell
sudo make uninstall
```