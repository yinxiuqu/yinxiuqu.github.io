Linux系统下使用Emacs编辑、编译LaTeX文档，常用auctex插件。我到处抄了一些关于auctex的配置，位置在[https://github.com/yinxiuqu/.emacs.d/blob/master/lisp/init-latex.el](https://github.com/yinxiuqu/.emacs.d/blob/master/lisp/init-latex.el)。其中一些快捷键如下：

1. C-c C-c 编译
2. C-c C-v 预览
3. C-c C-a 编译并预览
4. C-c C-e 插入环境（\begin{}……\end{}）
5. C-c C-s 插入层次（section, paragraph等）
6. C-c C-j或M-[RET] 插入条目
7. C-c C-f C-b粗体（\textbf）：字体相关指令都以C-c C-f 开头
8. C-c `  下一个错误
9. C-c C-l 查看编译log
10. C-c C-p C-p 实时preview LaTeX全文的效果
11. C-c C-p C-e 实时preview 光标所在的代码环境块内的效果
12. C-c C-p C-c C-d 移除当前文档内的全部preview效果
13. C-c = 在另一个buffer中显示文档的目录