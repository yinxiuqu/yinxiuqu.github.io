在编译一篇文言文资料的时候，“罍”字在Linux系统中显示是没有问题的，但是编译后的PDF文件却不显示该字，“罍”字显示为一个方框F。
```LaTeX
\documentclass{ctexart}

%\author{}
%\date{}
%\title{}

\begin{document}
%\maketitle

如``罍"（一种盛酒或水的器具）,``爨"（烧火做饭）、``孔"（表程度高的副词）。一类是古代汉语和现代汉语都很常用，但意义不完全相同的词语。

\end{document}
```
PDF显示效果如下：
![2024-11-02 17-07-53屏幕截图](https://github.com/user-attachments/assets/a14d8efe-c020-4666-ac7c-cf28b26c4acc)

打开ctex-fontset-fandol.def来发现Linux平台上的默认字体是FandolSong-Regular。更换方正书宋字体：
```LaTeX
\setCJKmainfont{FZShuSong-Z01}
```
PDF文件正常显示了“罍”字。更换后的源代码如下：
```LaTeX
\documentclass{ctexart}

%\author{}
%\date{}
%\title{}

\setCJKmainfont{FZShuSong-Z01}

\begin{document}
%\maketitle



如``罍"（一种盛酒或水的器具）,``爨"（烧火做饭）、``孔"（表程度高的副词）。一类是古代汉语和现代汉语都很常用，但意义不完全相同的词语。

\end{document}
```
PDF文件显示效果如下：
![2024-11-02 17-12-29屏幕截图](https://github.com/user-attachments/assets/8c7f6ec0-dd3d-4916-b943-eb632fd50888)