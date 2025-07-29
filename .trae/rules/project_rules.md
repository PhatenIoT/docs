1.新建文件、名称可以使用单词加下划线的方式命名；
2.编写文章、md文件需要考虑内容的SEO设计,突出重点内容；公司名称、产品名称。SEO设计内容，不能直接显示在文档内容中，需要在文档的meta标签中进行配置；或隐藏在网页源码中。
3.编辑的文档代码中，如果有下载文件的相关代码地址需要添加一下方式：{
    1、在顶部加入
    ---
    login: true
    ---
    2、在页面前加入这行代码：--8<-- "common/checklogin_form.md"
    3、按照<a href="javascript:void(0);" onclick="checkLogin('/assets/download/tools_software/audacity-win-3.4.2-64bit.exe')">:material-download:</a> 这个方式，根据实际内容修改下载文件地址的代码
}
4、添加的新文件或者相关的标题首字母都需要大写
5、编辑文档，需要让显示的内容更具可读性，采用合适的markdown语法。