Emacs编辑器是个古老编辑器，肯怕比开源操作系统Linux历史更悠久。我从2000年左右开始使用Linux系统时，Emacs就是一直系统自带的编辑器之一，用习惯了。近年来vscode也用，但能用Emacs的时候我尽量用Emacs，因为那套快捷键已经渗入骨髓也习惯了。

前面我在Emacs编辑器上配置使用copilot.el进行代码补全，非常好用，唯一缺点就是每个月免费补全次数太少了，只有2000次，补全建议不管是否采用均计算免费次数，几天就用完了，而付费要10美元每月，补全代码不按用量付费。一直想支持国产大模型，前期在vscode上一直用智谱插件免费补全代码，但没有Emacs的插件。最近看到很多人推荐Emacs通过minuet.el插件使用DeepSeek进行代码补全，试用之后效果很好，准确率较高，还提供多个补全建议供选择，补全速度也较快，基本满足我的代码补全需求。我的安装和配置方法如下：

首先去DeepSeek官网上申请一个app keys，将其复制。打开系统的shell配置文件，如我的系统中是~/.bashrc，将api keys写入其中：
```bash
export DEEPSEEK_API_KEY="sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"   # 替换为你的真实密钥
```
保存后，执行以下命令使配置生效：
```bash
source ~/.bashrc   # 我用的是 bash
```

然后在Emacs的配置文件中添加如下elisp语句，下载插件和做好配置：
```elisp
;; minuet 相关的设置

;; 从shell中抓取环境变量
(use-package exec-path-from-shell
  :ensure t
  :config
  ;; 指定需要抓取的环境变量
  (add-to-list 'exec-path-from-shell-variables "DEEPSEEK_API_KEY")
  ;; 初始化抓取
  (exec-path-from-shell-initialize))

;; 配置 minuet
(use-package minuet
  :ensure t
  :hook (prog-mode . minuet-auto-suggestion-mode)
  :bind (("M-i" . #'minuet-show-suggestion)          ; 手动触发补全
         :map minuet-active-mode-map                 ; 补全建议显示时的快捷键
         ("M-p" . #'minuet-previous-suggestion)      ; 上一个建议
         ("M-n" . #'minuet-next-suggestion)          ; 下一个建议
         ("M-a" . #'minuet-accept-suggestion-line)   ; 接受当前行
         ("M-A" . #'minuet-accept-suggestion)        ; 接受整个建议
         ("M-e" . #'minuet-dismiss-suggestion))      ; 取消建议
  :init
  ;; 如果你希望自动补全，可以在这里添加钩子
  ;; (add-hook 'prog-mode-hook #'minuet-auto-suggestion-mode)
  :config

  ;; 获取环境变量中的api keys:
  (setq minuet-openai-api-key (getenv "DEEPSEEK_API_KEY"))
  
  ;; 1. 设置 provider 为 openai-fim-compatible (这是默认值，但显式设置更安全)
  (setq minuet-provider 'openai-fim-compatible)

  ;; 2. ★★★ 关键修正：使用 minuet-set-optional-options 来设置参数 ★★★
  (minuet-set-optional-options minuet-openai-fim-compatible-options
    :max_tokens 128)  ; 增加最大补全长度

  ;; 3. 其他通用设置
  (setq minuet-request-timeout 5)          ; 请求超时时间（秒）
  (setq minuet-auto-suggestion-debounce-delay 0.3)) ; 自动补全触发延迟
```

然后重启Emacs就可使用，具体用法已经在上述配置文件注释中写明。上面配置文件中我没有将api keys写入其中，因为我的Emacs配置文件夹被我同步到github仓库中的，如果api keys写入其中那就在网上公开了。具体使用情况如下图所示，其中（1/3）表示有3个补全建议，可以根据上面配置文件设置的快捷键进行上、下翻：

<img width="1366" height="728" alt="Image" src="https://github.com/user-attachments/assets/77a23b48-5af6-4900-8ecd-3c466649b7a8" />

