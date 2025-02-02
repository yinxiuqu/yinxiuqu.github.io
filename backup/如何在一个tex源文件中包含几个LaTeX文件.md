类似overleaf这类网站，可以直接上传文件。因此，当一个LaTeX项目有多个文件时，可以一并上传，再编译。但这类网站往往需要注册，而且一个项目的编译时间是有限制的，上传的文件总的大小也有限制。

还有一类，不需要注册，对编译时间也不做限制，直接粘贴LaTeX源代码就可以编译，但是不能上传文件。这种情况如果一个项目有多个源文件，则需要将他们全部合并到一个源文件中，再粘贴到网站上进行编译。此类网站如 [https://texlive.net/run](https://texlive.net/run)

对于这类网站，可以在\begin{dodument}之前使用\RequirePackage命令导入filecontents这个包，然后利用*filecontents环境包含其他源文件，例如自定义的cls文件等。因为是在\begin{document}命令之前，所以不能用\usepackage命令，而要用\RequirePackage命令。下面是一个最简工作代码：

```latex
% !tex xelatex

% 必须添加的文件头
\RequirePackage{filecontents}
\begin{filecontents*}{myctexart.cls}
\NeedsTeXFormat{LaTeX2e}
\ProvidesClass{myctexart}[2023/10/10 Custom document class]
\LoadClass[UTF8]{ctexart}
\RequirePackage{amsthm}
\endinput
\end{filecontents*}

% 主文档
\documentclass{myctexart}

\begin{document}
测试
\end{document}