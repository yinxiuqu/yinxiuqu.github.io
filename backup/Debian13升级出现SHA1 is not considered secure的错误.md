前面在安装emacs的copilot插件时安装了NodeSource里的构件，最近每次系统升级时提示：
```
警告： 无法下载 https://deb.nodesource.com/node_22.x/dists/nodistro/InRelease  Sub-process /usr/bin/sqv returned an error code (1), error message is: Signing key on 6F71F525282841EEDAF851B42F59B5F99B1BE0B4 is not bound:            No binding signature at time 2026-06-25T23:32:49Z   because: Policy rejected non-revocation signature (PositiveCertification) requiring second pre-image resistance   because: SHA1 is not considered secure since 2026-02-01T00:00:00Z
```
问deepseek，说这个错误是由于Debian13(Trixie)的安全策略升级导致的。Debian Trixie默认使用新的sqv(Sequoia PGP)工具来验证APT仓库的签名。出于安全考虑，sqv从2026年2月1日起正式拒绝接受使用SHA-1算法签名的GPG密钥。NodeSource之前的仓库签名密钥中包含了SHA-1签名，因此触发了此安全策略并被拦截。 解决方法很简单，删除nodesource老的配置和密钥，重新添加NodeSource 22.x官方仓库：
```bash
sudo rm -f /etc/apt/sources.list.d/nodesource.list
sudo rm -f /etc/apt/keyrings/nodesource.gpg
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
```
