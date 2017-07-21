# PyFrm 
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