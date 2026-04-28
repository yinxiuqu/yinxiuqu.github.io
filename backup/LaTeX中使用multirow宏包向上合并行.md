multirow宏包可以合并行，平时我们使用时都是使用正参数向下合并行，如果使用负的参数可以向上合并参数。示例如下：
```latex
% !tex xelatex
\documentclass[a4paper]{ctexart}
\usepackage[top=2cm, bottom=2cm, left=2cm, right=2cm]{geometry}
\usepackage{array}
\usepackage{multirow}
\usepackage{colortbl} % 必须包含的包
\usepackage{xcolor}
\usepackage{graphicx}
\definecolor{lightblue}{rgb}{0.85,0.95,1}
\definecolor{lightyellow}{rgb}{1,1,0.85}

\begin{document}
\pagestyle{empty}
\centering

{\LARGE\bfseries 九九乘法口诀表}\\[1cm]

% 主乘法表
\begin{minipage}{0.9\textwidth}
\centering
\setlength{\tabcolsep}{3mm} % 列间距
\renewcommand{\arraystretch}{1.5} % 行高

\begin{tabular}{|>{\columncolor{lightblue}}c|*{9}{>{\centering\arraybackslash}m{1.2cm}|}}
\hline
\rowcolor{lightyellow}
& 
\multicolumn{9}{c|}{\textcolor{red}{乘数}} \\
\cline{2-10}
\rowcolor{lightblue}
\cellcolor{lightyellow}
\multirow{-2}{*}{\textcolor{red}{乘数}}
& 1 & 2 & 3 & 4 & 5 & 6 & 7 & 8 & 9 \\
\hline
1 & 1 & 2 & 3 & 4 & 5 & 6 & 7 & 8 & 9 \\
\hline
2 & 2 & 4 & 6 & 8 & 10 & 12 & 14 & 16 & 18 \\
\hline
3 & 3 & 6 & 9 & 12 & 15 & 18 & 21 & 24 & 27 \\
\hline
4 & 4 & 8 & 12 & 16 & 20 & 24 & 28 & 32 & 36 \\
\hline
5 & 5 & 10 & 15 & 20 & 25 & 30 & 35 & 40 & 45 \\
\hline
6 & 6 & 12 & 18 & 24 & 30 & 36 & 42 & 48 & 54 \\
\hline
7 & 7 & 14 & 21 & 28 & 35 & 42 & 49 & 56 & 63 \\
\hline
8 & 8 & 16 & 24 & 32 & 40 & 48 & 56 & 64 & 72 \\
\hline
9 & 9 & 18 & 27 & 36 & 45 & 54 & 63 & 72 & 81 \\
\hline
\end{tabular}


\end{minipage}

\vspace{1cm}

% 改进的传统口诀格式 - 完整阶梯形式
{\large\textbf{传统口诀}}\\[0.3cm]
\begin{minipage}{0.8\textwidth}
\centering
\renewcommand{\arraystretch}{1.8} % 增加行高使阶梯更明显
\setlength{\tabcolsep}{0.5em} % 减少列间距
\begin{tabular}{l l l l l l l l l}
1×1=1 \\
1×2=2 & 2×2=4 \\
1×3=3 & 2×3=6 & 3×3=9 \\
1×4=4 & 2×4=8 & 3×4=12 & 4×4=16 \\
1×5=5 & 2×5=10 & 3×5=15 & 4×5=20 & 5×5=25 \\
1×6=6 & 2×6=12 & 3×6=18 & 4×6=24 & 5×6=30 & 6×6=36 \\
1×7=7 & 2×7=14 & 3×7=21 & 4×7=28 & 5×7=35 & 6×7=42 & 7×7=49 \\
1×8=8 & 2×8=16 & 3×8=24 & 4×8=32 & 5×8=40 & 6×8=48 & 7×8=56 & 8×8=64 \\
1×9=9 & 2×9=18 & 3×9=27 & 4×9=36 & 5×9=45 & 6×9=54 & 7×9=63 & 8×9=72 & 9×9=81 \\
\end{tabular}
\end{minipage}

\end{document}
%%% Local Variables:
%%% mode: LaTeX
%%% TeX-master: t
%%% End:
```
如果第一行时向下合并行，后面又涉及到列颜色和行颜色设置，可能会影响第一行第一列。这里是先把第一行、第一列的设置都做完，到第二行使用\multirow命令时第一个参数设置负值，向上合并行，这里设置了-2行，即向上合并两行。这样第二行第一列不会受到前面行、列颜色设置的影响。效果如下：

<img width="718" height="667" alt="Image" src="https://github.com/user-attachments/assets/edfe083a-27a0-4c19-b88c-c4e0c57002cb" />