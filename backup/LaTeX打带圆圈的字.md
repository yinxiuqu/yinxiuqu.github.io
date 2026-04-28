以前用LaTeX打带圆圈的数字，使用pifont包。但是这个包里的数字有限，只能10个，而且数字不能调整大小。后来用tikz为数字或文字画个圈，遇到放到缩小，经常有点偏离圆圈。总觉的打带圆圈的字不太方便，最近找到一个比较满意的宏包circledtext，记录下来备忘。示例代码如下：
```LaTeX
% 导言区
\documentclass{ctexart}
\usepackage{circledtext}
\pagestyle{empty}

% 正文区
\begin{document}

\noindent\circledtext{五}\quad
\circledtext{一佰}\quad
\circledtext[basechar=M]{999}\quad
\circledtext*{五}\quad
\circledtext*{888}\quad
\circledtextset{boxcolor=red}
\circledtext[boxtype=oo]{车}\quad
\circledtext[boxtype=Oo]{马}\quad
\circledtext[boxtype=OO]{炮}\quad
\circledtext*[boxtype=oo ]{车}\quad
\circledtext*[boxtype=Oo ]{马}\quad
\circledtext*[boxtype=OO ]{炮}\quad
\circledtext[resize=none]{10}\quad
\circledtext[resize=real]{15}\quad
\circledtext[resize=base]{20}\quad
\circledtext[xscale=0.5]{25}\quad
\circledtext[xscale=1.0]{25}\quad
\circledtext[xscale=1.5]{25}\quad
\circledtext[yscale=0.5]{35}\quad
\circledtext[yscale=1.0]{35}\quad
\circledtext[yscale=1.5]{35}\quad
\circledtext{100}\quad
\circledtext[boxlinewidth=1.0pt]{1000}\quad
\circledtext[boxlinewidth=2.0pt]{一佰三十}\quad
\circledtext[charcolor=red]{45}\quad
\circledtext[charcolor=green]{45}\quad

\end{document}
```
效果如下图：
![2024-11-25 14-56-37屏幕截图](https://github.com/user-attachments/assets/3aaa93d6-72d1-47d0-997d-ebcb972e2eb9)
