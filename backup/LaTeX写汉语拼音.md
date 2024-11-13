```LaTeX
% This document is compiled using xeLaTeX

\documentclass{ctexart}
\usepackage{xpinyin}
\xpinyinsetup{ratio=0.6}
\pagestyle{empty}

\begin{document}

1、用pinyinscope环境为一段汉字自动加注拼音，常用于编辑儿童读物。\\
\begin{pinyinscope}
列位看官：你道此书从何而来？说起根由，虽近荒唐，细按则深有趣味。
待在下将此来历注明，方使阅者\xpinyin{了}{liao3}然不惑。
\end{pinyinscope}

2、用\verb|\xpinyin|命令为单个汉字加注拼音。上例中\verb|\xpinyin{了}{liao3}|为多音字“了”单独加注拼音并指明是第三声。

3、用\verb|\xpinyin*|命令为一段汉字自动加注拼音，相当于pinyinscope的命令形式。\\
\xpinyin{长}{chang2}\\
\xpinyin*{甄士隐梦幻识通灵}\\
\xpinyin*{\xpinyin{重}{zhong4}要}

4、用\verb|\pinyin|命令单独打拼音及声调。\\
\pinyin{lv2zi}\\
\pinyin{nv3hai2zi}

此外还有一些设置，具体可以参看xpinyin宏包的文档。

\end{document}
```
编译后效果如下：
![2024-11-13 20-24-14屏幕截图](https://github.com/user-attachments/assets/a68856c5-3e0d-4d00-911e-61a2b3cb7dc9)
