文件在windows那边编辑好之后，直接复制Linux系统下，可能会因编码问题而使汉字显示乱码。因为Windows系统下默认用GBK编码，Linux系统下默认用UTF-8编码。遇到这种情况，可以先查询文件的编码：
```bash
file name.ext
```
GBK编码在Linux系统下有时候会显示是ISO-8859编码。在Linux系统下要转换编码，可直接用系统自带的iconv命令在终端中运行：
```bash
# 将GBK文件转换为UTF-8（生成新文件）
iconv -f GBK -t UTF-8 windows_file.txt -o linux_file_utf8.txt

# 批量转换当前目录下所有.txt文件
for file in *.txt; do iconv -f GBK -t UTF-8 "$file" > "${file%.txt}_utf8.txt"; done
```
若要覆盖源文件，则在终端运行：
```bash
iconv -f GBK -t UTF-8 input_file.txt -o temp.txt && mv temp.txt input_file.txt
```
也可利用Vim编辑器进行转换，在Linux中用Vim打开文件后执行：set fileencoding=utf-8保存即可。
如果文件分散在某个文件夹内及其各级子文件夹内，可以建立shell脚本一次性处理，创建一个名为 convert_gbk_to_utf8.sh 的文件，内容如下：
```bash
#!/bin/bash

if [ -z "$1" ]; then
    echo "Usage: $0 DIRECTORY"
    exit 1
fi

DIR="$1"

find "$DIR" -type f -name "*.tex" | while read -r file; do
    iconv -f gbk -t utf-8 "$file" -o "${file}.tmp" && mv "${file}.tmp" "$file"
    echo "Converted: $file"
done
```
赋予脚本执行权限：
```bash
chmod +x convert_gbk_to_utf8.sh
```
在终端中运行命令，指定目标文件夹路径：
```bash
./convert_gbk_to_utf8.sh /path/to/texfiles
```
脚本会递归地找到所有 .tex 文件，并将其编码从 GBK 转换为 UTF-8。