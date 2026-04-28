texlive里有个国际音标的宏包tipa，能打出各个国际音标。但是国际音标数量较多，而常用的是英语DJ音标（第15版）。为便于使用，这里将DJ音标从国际音标中单独整理出来如下：
```LaTeX
% 导言区
\documentclass{ctexart}
\usepackage{tipa}
\pagestyle{empty}

%\title{My First Document}
%\author{LoongTeX}
%\date{\today}

% 正文区
\begin{document}
%\maketitle

\textipa{[/\textprimstress \textsecstress " () A: O: 3: i: u: 2 6 @ I U e \ae{} eI aI OI I@ e@ U@ @U aU p t k T f s S ts tS tr h b d g D v z Z dz dZ dr r m n N l j w i u/]}
\end{document}
```
 编译后如下：
![2024-11-12 07-49-21屏幕截图](https://github.com/user-attachments/assets/fac8e183-c29c-44b7-aa24-78a224ab15f6)
