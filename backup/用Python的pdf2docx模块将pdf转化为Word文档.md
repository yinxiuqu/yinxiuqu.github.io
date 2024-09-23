曾经为了将pdf文件转化为Word文档以便于修改，花了100多元专门购买了WPS会员，利用WPS的会员工具进行转化，效果很差，还到处是乱码。后来从网上看到利用Python转化的方法，自己测试了一下，效果居然意外的好，格式按原样保留非常到位，但是文件非常大。记录如下：
先为Python安装好模块pip install pdf2docx，然后运行几行代码：
`from pdf2docx import Coverter`
`pdf_file = 'pdf文件路径'`
`docx_file = '输出Word文件的路径'`
`cv = Converter(pdf_file)`
`cv.convert(docx_file, start=0, end=None)`
`cv.close()`