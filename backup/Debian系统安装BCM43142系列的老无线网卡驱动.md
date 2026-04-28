原文地址：[https://wiki.debian.org/wl#issues](https://wiki.debian.org/wl#issues)

1. Add a "non-free" component to /etc/apt/sources.list for your Debian version, for example:

\# Debian 9 "Stretch"
deb http://deb.debian.org/debian stretch-backports main contrib non-free

\# Debian 10 "Buster"
deb http://deb.debian.org/debian buster-backports main contrib non-free

\# Debian 11 "Bullseye"
deb http://deb.debian.org/debian bullseye main contrib non-free

\# Debian 12 "Bookworm"
deb http://deb.debian.org/debian bookworm main contrib non-free-firmware non-free

2. Update the list of available packages. Install the relevant/latest linux-image, linux-headers and [broadcom-sta-dkms](https://packages.debian.org/broadcom-sta-dkms) packages:

\# apt-get update
\# apt-get install linux-image-$(uname -r|sed 's,[^-]*-[^-]*-,,') linux-headers-$(uname -r|sed 's,[^-]*-[^-]*-,,') broadcom-sta-dkms

This will also install the recommended [wireless-tools](https://packages.debian.org/wireless-tools) package. DKMS will build the wl module for your system.

3. (Optional) Rescue if install/build fails in previous step

\# apt-get install -f
\# dpkg-reconfigure broadcom-sta-dkms

4. (Optional) Check all the built DKMS kernel modules. There should be "wl.ko" in the list.

\# find /lib/modules/$(uname -r)/updates

5. Unload conflicting modules:

\# modprobe -r b44 b43 b43legacy ssb brcmsmac bcma

6. Load the wl module:

\# modprobe wl

7. [Configure](https://wiki.debian.org/WiFi/HowToUse) your wireless interface as appropriate.