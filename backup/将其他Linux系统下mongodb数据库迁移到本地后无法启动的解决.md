将其他Linux系统下mongodb数据库迁移到本地，或者将本地Linux系统下mongodb数据库迁移位置，无法启动的解决办法：
首先，数据库文件转移后，要先把所有者改成mongodb；
其次，在mongodb配置文件上设置或修改数据保存的目录位置；
最后，将数据库文件里的mongodb.lock、WiredTiger.lock两个文件删除。如果仍无法重启服务，可将/tmp/mongodb-27017.sock等文件删除，即可重新启动服务。