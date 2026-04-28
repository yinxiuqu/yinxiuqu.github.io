在排版一片文言文语法文章的时候，需要用小三角形在关键词下标示出来。一开始考虑用叠加方式，在关键词下方叠加图标，后来高人指点xeCJK宏包文档里有\CJKunderanysymbol命令，能添加任意图表到文字下方。命令实际上是在xeCJK的子宏包xeCJKfntef里定义的，该宏包中还定义了一系列的下划线等各种命令，这些命令相互之间又可互相嵌套。做如下代码测试：
```latex
% This document is compiled using xeLaTeX

\documentclass{ctexart}
\pagestyle{plain}
\usepackage{xeCJKfntef}
\usepackage{xcolor}

\begin{document}

%\maketitle

\noindent\CJKunderanysymbol[sep=0.1em]{0.2em}{\tiny$\triangle$}
{瞻彼阕者，虚室生白，\CJKunderline{吉祥止止}}\\
\CJKunderline{虚室生白，吉祥止止}\\
\CJKunderdblline{虚室生白，吉祥止止}\\
\CJKunderwave{虚室生白，吉祥止止}\\
\CJKsout{虚室生白，吉祥止止}\\
\CJKxout{虚室生白，吉祥止止}\\
\CJKunderline-{南朝}\CJKunderline-{梁}\CJKunderline-{劉勰}%
\CJKunderwave-{文心雕龍}\CJKunderwave-{養氣}\\
\CJKunderline*[thickness=1pt, hidden=true]{瞻彼阕者，虚室生白，吉祥止止}\\
\CJKunderline{虚室生白，\CJKunderdot{吉祥}止止}\\
\CJKunderdot{虚室生白，\CJKunderline{吉祥}止止}\\
\xeCJKsetup { underline/format = \color{red} }
\xeCJKsetup { underwave = { format = \color{red}} }
\CJKunderline[textformat=\color{blue}]{虚室生白，吉祥止止}\\
\CJKunderdot[textformat=\bfseries, format=\color{red}]{虚室生白，吉祥止止}\\

\end{document}
```
效果分别如下：
![2024-11-01 15-35-15屏幕截图](https://github.com/user-attachments/assets/a9c7abb4-d9e7-4364-a2b6-fcf103563a1a)
空格效果应该是可以作为出填空题时的工具。具体用法可参考xeCJK文档。