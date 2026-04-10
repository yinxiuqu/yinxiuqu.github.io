升级到debian 13之后，每次需要以超级管理员身份sudo执行命令时，要很久才提示输入密码。在debian中文论坛上有网友回复，是否将自己主机名输入到/etc/hosts。想到去年因为不能访问github而去修改了/etc/hosts，当时完全复制粘贴了网上的hosts文件，把本地主机名映射到127.0.1.1给覆盖掉了，补充进去后果然以sudo执行命令时验证密码的功能瞬间就跳出来了。

```bash

# IPv4 核心条目
127.0.0.1       localhost
127.0.1.1       your-hostname

# IPv6 核心条目
::1             ip6-localhost ip6-loopback
fe00::0         ip6-localnet
ff00::0         ip6-mcastprefix
ff02::1         ip6-allnodes
ff02::2         ip6-allrouters

将 your-hostname 替换为你的主机名。