# PyFrm 
## 文档介绍
本文档使用 [mkdocs](http://www.mkdocs.org/) 编写，`pip install mkdocs` 安装mkdocs。

> 如果对 easy_install, pip, python setup.py install 这些有疑问。
> 
> 参见: [http://zengrong.net/post/2169.htm](http://zengrong.net/post/2169.htm)

**推荐markdown编写文档。**

markdown为Web博客书写而设计，目前主流网站均支持。语法介绍： [http://www.appinn.com/markdown/](http://www.appinn.com/markdown/)

## 本地使用
git clone项目后，进入项目目录，启动命令：

* `mkdocs serve` - 启动本地访问服务访问手册。

> 如果你还不熟悉 git，请查阅:
> 
> [Git教学](http://dylandy.github.io/Easy-Git-Tutorial/)
> 
> [Git备忘单](https://services.github.com/on-demand/downloads/zh_CN/github-git-cheat-sheet/)

其他常用命令：

* `mkdocs new [dir-name]` - 创建新文档项目.
* `mkdocs build` - 构建html本地站点.
* `mkdocs gh-deploy` - 发布到github
* `mkdocs help` - 帮助文档.

主要介绍技术使用及流程规范，**请勿**将密码、核心业务、关键算法等写入本文档。欢迎补充说明。

### **未安装** mkdocs 查看文档：

1. 进入 site 目录

	> cd site
2. 启动 python 本地文件服务

	> python3 执行 python -m http.server 9080
	>
	> python2 执行 python -m SimpleHTTPServer 9080
	>
	> 访问本地网页 [http://127.0.0.1:9080](http://127.0.0.1:9080)