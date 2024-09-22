原文地址：[https://forums.debiancn.org/t/topic/3828](https://forums.debiancn.org/t/topic/3828)
1、下载live dvd的镜像 [http://mirrors.163.com/debian-cd/12.0.0-live/amd64/iso-hybrid/debian-live-12.0.0-amd64-cinnamon.iso 8](http://mirrors.163.com/debian-cd/12.0.0-live/amd64/iso-hybrid/debian-live-12.0.0-amd64-cinnamon.iso)
2、插入U盘，并且用命令sudo fdisk -l 查询U盘的位置，例如：
Disk /dev/sdb：31.25 GiB，33554432000 字节，65536000 个扇区
3、卸载U盘：sudo umount /dev/sdb
4、格式化U盘（选择一种格式）：
$ sudo mkfs.ext4 /dev/sdb # 格式化为ext4分区
$ sudo mkfs.ext3 /dev/sdb # 格式化为ext3分区
$ sudo mkfs.ext2 /dev/sdb # 格式化为ext2分区
$ sudo mkfs.ntfs /dev/sdb # 格式化为ntfs分区，速度有点慢
$ sudo mkfs.vfat -F 32 /dev/sdb # 格式化为fat32分区
5、将当前目录的ISO镜像烧入USB
$ sudo dd if=debian-live-12.0.0-amd64-cinnamon.iso of=/dev/sdb bs=4M status=progress
其中，bs为块大小，可以为512k/1M/2M/4M，status=progress为显示状态。