在数学计算和证明过程中，常需用到箭头，有时候箭头上需要写一些说明文字、推算的依据或理由，有时候说明文字还比较长，传统的箭头不会自动伸缩长度，看起来就很不美观。这时可以考虑使用可变长度箭头：引用extarrows宏包，使用"x传统箭头命令"的形式，箭头下方文字做可选参数，箭头上方文字做必要参数。例如\xLongrightarrow[上方文字]{下方文字}等命令形式，此外还支持长等号，如\xlongequal。extarrows定义的9个可变长度命令分别如下：
* \xlongequal
* \xlongleftrightarrow
* \xLongleftarrow
* \xLongrightarrow
* \xleftrightsquigarrow
* \xrightleftrightsquigarrow
* \xleftrightsquigarrow
* \xrightleftrightsquigarrow
* \xleftrightsquigarrow