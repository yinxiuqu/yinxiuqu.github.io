在编辑大型文件时，通常采用结构化编辑，将主源文件和各章节的子源文件分开编辑。在编辑子源文件时，想查看编译效果，通常要回到主源文件中进行编译。如果在子源文件最后插入%%% TeX-master: "../main"，双引号内输入主源文件路径位置，重启buffer后则能不切换到主源文件，直接在子源文件中编译，这样就更便利了。
此外，还看到有人添加以下一些内容：
```latex
%%% Local Variables:
%%% mode: latex
%%% TeX-master: “…/csuthesis_main”
%%% TeX-engine: xetex
%%% End:
```
还有人为了自动执行多步编译使用[Arara](https://github.com/cereda/arara)，在init-latex中添加如下设置：
```lisp
(eval-after-load "tex"
  '(add-to-list 'TeX-command-list
        '("Arara" "arara %s" TeX-run-TeX nil t :help "Run Arara.")))
```
参见[Arara integration in Emacs](http://emacs.stackexchange.com/questions/9715/arara-integration-in-emacs)。Arara是Latex的扩展包，TexLive2014默认集成。然后在需要编译的主文档顶部添加需要顺序执行的指令。比如
```latex
% arara: pdflatex
% arara: bibtex
% arara: pdflatex
% arara: pdflatex
\documentclass {article}
...
```
配置好后，编译文档时，键入C-c C-c arara即可。