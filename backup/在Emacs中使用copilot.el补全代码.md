最近用了vscode使用copilot插件补全代码，很丝滑。能理解我程序编码上下文的意思，推算我接下来该写哪些代码。这和DeepSeek的通过文字描述直接给出一段功能代码是不同的。因为有些代码你是必须按自己的构想手写出来，一句一句审核，很多时候并不方便用文字去向AI描述一个功能。
最不可思议的是，常常是一次性补全一大段代码，而且几乎没有错误。
其次是模仿我编码的习惯，如LaTeX里我喜欢用\overline表示共轭，用\bm表示粗体向量，补全建议时，它都是模仿这些习惯的。
第三是，在数学排版过程中，我列出代数式，它立即帮我把后面的计算步骤和计算结果都补全出来，而且是用LaTeX代码排版好。
vscode中能用了，就立即想到要在Emacs中实现。搜索了一下，还真找到了copilot.el这个插件，我安装和配置如下：
# 1.配置文件
```emacs-lisp
;; 本文件用于配置AI

;; 安装copilot.el
(use-package copilot
  :ensure t)

;; 使用copilot进行补全
(add-hook 'prog-mode-hook 'copilot-mode)
(add-hook 'LaTeX-mode-hook 'copilot-mode)
(add-hook 'pyton-mode-hook 'copilot-mode)
(add-hook 'TeX-mode-hook 'copilot-mode)


;; Tab 键接受全部补全
(define-key copilot-mode-map (kbd "<tab>") 'copilot-accept-completion)
  
;; Ctrl+→ 逐字符接受部分补全插入
(define-key copilot-mode-map (kbd "C-<right>") 'copilot-accept-completion-by-word)


;; 文件结尾
(provide 'init-ai)
```
# 2.安装 Copilot 语言服务器
```emacs-lisp
M-x copilot-install-server
```
这个过程比较久，要等它全部完成。
# 3.登录GitHub Copilot账户
 ```emacs-lisp
M-x copilot-login
```
按提示登陆GitHub账户，输入权限验证码。
这样设置后，copilot可以在elisp, python, LaTeX等语言上使用copilot补全了，效果和vscode完全一样。但是，有个小警告我想了很多办法都一直无法消除，当前模式偏移量无法找到合适值：
```emacs-lisp
Warning (copilot): copilot--infer-indentation-offset found no mode-specific indentation offset. Disable showing Disable logging
```
我尝试过手工设置偏移量，全局模式和针对各特定模式都设置过，还是有这个警告。哪位帮忙看看如何消除。