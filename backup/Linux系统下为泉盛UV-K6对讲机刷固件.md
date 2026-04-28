首先下载好固件保存到本地，再将泉盛UV-K6的刷频线连接到USB借口，确保你已经有CH340驱动。使用如下烧录命令烧录固件到对讲机：
```shell
sudo dd if=/path/to/firmware.bin of=/dev/ttyUSB0 bs=1M
```
其中，if 代表输入文件（固件镜像），of 代表输出文件（对讲机的设备文件，通常是 /dev/ttyUSB0 或类似的串口设备），bs 代表块大小，通常对于固件更新设置为 1M 或 4M 效果较好。确保替换 /path/to/firmware.bin 为你的固件文件实际路径，并根据需要更改 /dev/ttyUSB0 为对讲机的正确设备文件。