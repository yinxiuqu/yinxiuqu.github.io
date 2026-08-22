DeepSeek刚开源DeepSeek Harness，即DSH，它是一个能让大语言模型（默认是DeepSeek，可以是其他模型）变成能干活的智能体（agent），是大模型的身体和工作台，负责把模型、工具、文件系统等所有部件连接起来，让AI能真正地执行任务。下面我按照今早我自己在我的Linux系统电脑上布置Harness的过程：

首先下载和安装nvm：
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
# 执行完毕后，重启终端或 source ~/.bashrc
```

然后，为确保使用 nvm 安装的 Node，而不是不是系统自带的，可执行以下操作：
```bash
nvm install 22.23.2
nvm use 22.23.2
```

现在已经安装和使用了 nvm，用 nvm 安装的 Node 版本，其全局安装目录位于Linux用户家目录下，不需要管理员权限（sudo）。此时再全局安装Harness，无需 sudo，也无需额外内存限制：
```bash
npm install -g @deepseek-ai/dsh
```

最后，启动Harness：
```bash
dsh web
```

系统会自动启动浏览器并打开网址：http://127.0.0.1:3080 ，第一次打开的时候，网页上会提示目前尚是测试版等警告，确认就可以进去。然后要去DeepSeek官网注册一个帐号并申请一个api key，这需要充值付费使用，申请好api key之后，把它复制到Harness网站跳出的api key的提示框里确定就可以使用了。使用时，可以先添加一个WorkSpace，即添加一个工作区，可以选择一个本地目录或者创建一个目录做工作区，以后你给Harness提供的数据、文件都放到这个文件夹里，Harness为你干活输出的文件也都保存到这个文件夹下。当然每个项目可以新建一个或几个工作区。

本地布置好我令Harness为我制作一个初中物理的波的干涉和抛物过程的机械能守恒动画，它都给我制作保存在工作区，然后检验测试了这两个视频文件发现有bug并立即修正了bug之后，重新保存了视频文件到工作区。安装的关键步骤和动画抓图如下所示：

<img width="1366" height="728" alt="Image" src="https://github.com/user-attachments/assets/706a2c21-6361-4ff8-8764-062f8216b5b9" />

<img width="1366" height="728" alt="Image" src="https://github.com/user-attachments/assets/24b3afef-ad9b-4e88-a053-bdc25808f823" />

<img width="1366" height="728" alt="Image" src="https://github.com/user-attachments/assets/cbef79a1-cbd5-477b-b4b8-2f39637522b6" />

<img width="1366" height="728" alt="Image" src="https://github.com/user-attachments/assets/42bbfbf8-1eae-4aaa-812b-478db3ecee08" />

<img width="1366" height="728" alt="Image" src="https://github.com/user-attachments/assets/ab87fc51-4d50-43c3-a3b1-ac9d74fc1b8d" />

<img width="1366" height="728" alt="Image" src="https://github.com/user-attachments/assets/2ac98dd2-9799-423b-8650-01947af7e4b1" />

