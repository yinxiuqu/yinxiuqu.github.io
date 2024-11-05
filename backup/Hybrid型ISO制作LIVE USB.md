原文地址：[https://www.debian.org/releases/stable/amd64/ch04s03.zh-cn.html](https://www.debian.org/releases/stable/amd64/ch04s03.zh-cn.html)
# 4.3为从 U 盘引导准备文件
为了准备 U 盘，推荐使用一台正在运行的支持 USB 的 GNU/Linux 系统。当前的 GNU/Linux 系统会在您插入 U 盘的时候自动识别。如果没有，您应该确认 usb-storage 内核模块是否已经被加载。U盘插入后，它将被映射到名为 /dev/sdX的设备，其中的X是 a-z 的字母。您可以通过在插入U盘前后运行 lsblk命令来查看U盘被映射到哪个设备名。（查看dmesg命令的输出（以root用户运行）也是一种方法。）要写入信息，您需要先关闭U盘的写保护开关。
  **警告**
采用这种方法将销毁设备上已有的任何内容！请确认您使用了正确的 U 盘设备名。如果搞错，比如写成硬盘，将造成该设备上的所有信息丢失。
## 4.3.1使用混合 CD/DVD 映像制作 U 盘
针对此架构的Debian安装映像是采用isohybrid技术创建的，这意味着它们可以被直接写入U盘，这是非常简单的制作安装介质的方法。只需为U盘选择一个大小合适的映像（如 netint、CD或DVD-1）。参阅 [第4.1节 “官方的 Debian GNU/Linux 安装映像”](https://www.debian.org/releases/stable/amd64/ch04s01.zh-cn.html)) 获取安装映像。
您选中的安装映像应该被直接写入U盘，覆盖它当前的内容。例如，使用已有的GNU/Linux系统，映像文件可以参照下面方法写入U盘，写之前请确认U盘已经卸载：
`# cp debian.iso /dev/sdX`
`# sync`
对大多数用户来说，简单地把安装映像写入 U 盘已经够用。如果您有特殊需求，请阅读此[维基页面](https://wiki.debian.org/DebianInstaller/CreateUSBMedia)。
在其它操作系统上如何做的信息可以在[Debian CD FAQ](https://www.debian.org/CD/faq/index.en.html#write-usb)中找到。
**重要**
映像必须写入整个盘设备上而不是分区上，例如/dev/sdb而不是/dev/sdb1。不要使用unetbootin的工具，它会更改映像。