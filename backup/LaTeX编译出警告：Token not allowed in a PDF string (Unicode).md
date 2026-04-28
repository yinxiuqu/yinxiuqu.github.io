编译一个结构化的源文件时，发现一系列类似下面的警告：
```LaTeX
Package hyperref Warning: Token not allowed in a PDF string (Unicode):
(hyperref)                removing `math shift' on input line 83.
```
根据编译的log文件所提示，找到对应子源文件的对应行，发现是小节标题里使用了符号$：
```LaTeX
\subsection{$Gramer$法则}
```
这样编译后的文件对应的小节标题显示没问题，是数学斜体。但是由于使用了hyperref包，在文档的标签里就不能显示这个效果，是普通字体，其他类似警告都是这个问题引起的。
参照《LaTeX 2e完全学习手册》中的方法，使用\texorpdfstring命令，将小节标题改为：
```LaTeX
\subsection{\texorpdfstring{$Gramer$}{\textit{Gramer}}法则}
```
之后再编译没有这个警告了，但是，标签里的字体仍然是普通字体没有变为斜体。