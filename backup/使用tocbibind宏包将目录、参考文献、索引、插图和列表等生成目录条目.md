参考原文地址：[https://www.latexstudio.net/hulatex/package/content-2.htm](https://www.latexstudio.net/hulatex/package/content-2.htm)

LaTeX编译pdf文件时，目录自身不会添加到目录，参考文献、索引、插图和列表等也不会自动加入到目录中，可以使用tocbibind宏包将这些项的标题和页码自动加入目录。该宏包还有以下选项可以取消对应的项进入目录：
| 选项 | 作用 |
|:------|:------|
| notbib | 取消参考文献标题 |
| notindex | 取消索引标题 |
| nottoc | 取消目录标题 |
| notlot | 取消表格目录标题 |
| notlof | 取消图形目录标题 |
| numbib | 参考文献标题加序号 |
| numindex | 索引标题加序号 |
| none | 取消宏包所有功能 |