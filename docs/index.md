# PyFRM: Python智能金融风控

## 相关介绍
金融风控或风控模型核心是相关的特征处理、信用评估、反欺诈、额度管理等等数据科学或数据智能。

使用python进行数据分析，风险建模。你接下来需要使用的工具包括：

1. Python 2.x || Python3.x
2. 数据库 MySQL & MongoDB
3. Pandas & scikit-learn
4. XGBoost & LightGBM
5. Flask & RESTful
6. Hadoop & kylin & superset

PyFRM手册将一一为你介绍这些相关的工具，以及它们涉及到的工作业务。具体进阶步骤包括：

    - 工程基础:
      - 教材介绍: 工程基础/python-tutorial.md
      - 2.x VS 3.x: 工程基础/python2vs3.md
      - Git使用: 工程基础/git.md
      - 文档工具: 工程基础/docs-tools.md
      - 文件与编码 : 工程基础/python-io.md
      - Email操作 : 工程基础/python-email.md
    - 工程进阶:
      - 数据结构: 工程进阶/data-structure.md
      - 面向对象: 工程进阶/object-oriented.md
      - 控制流程: 工程进阶/control-flow.md
      - 并发技术: 工程进阶/Concurrent.md
      - 函数式编程: 工程进阶/functional-programming.md
    - 工程实践:
      - 最佳实践:
        - 实践栈说明: 最佳实践/best-practice.md
        - DevOps: 最佳实践/best-devops.md
        - 基础服务: 最佳实践/best-base-service.md
        - 数据服务: 最佳实践/best-data-service.md
        - 网络开发: 最佳实践/best-network.md
        - 数据智能: 最佳实践/best-data-insight.md
      - 编程规范 : 工程实践/python-style.md
      - 项目结构: 工程实践/project-structure.md
      - 文档管理: 工程实践/manage-docs.md
      - 设计模式: 工程实践/python-patterns.md
      - 调试测试: 工程实践/debug-test.md
      - 审核上线: 工程实践/review-release.md
    - 数据处理:
      - 关系型数据库 : 数据处理/database.md
      - NoSQL : 数据处理/nosql.md
      - SQL-Query: 数据处理/sql.md
      - Json-Query: 数据处理/json-query.md
      - MySQL实践 : 数据处理/mysql.md
      - MongoDB实践 : 数据处理/mongodb.md
      - Pandas实践 : 数据处理/python-pandas.md
    - Web开发:
      - API介绍 : Web开发/web-api.md
      - RESTful: Web开发/restful.md
      - flask实践 : Web开发/flask.md
      - API文档: Web开发/api-docs.md
      - 异步/队列服务 : Web开发/async.md
      - 前端介绍: Web开发/frontend.md
    - 业务知识:
      - 风控指标: 业务知识/risk-management.md
      - 业务结构: 业务知识/o2o-intro.md
      - 统计学基础: 业务知识/stats-intro.md
      - 征信体系: 业务知识/credit-intro.md
      - 反欺诈: 业务知识/anti-fraud.md
    - 数据科学:
      - 机器学习: 数据科学/machine-learning.md
      - 数据挖掘: 数据科学/data-mining.md
      - 模型分析: 数据科学/data-model.md
      - 模型总结: 数据科学/model_iteration_summary.md
      - XGBoost: 数据科学/xgboost.md
      - sk-learn: 数据科学/sk-learn.md

## 文档介绍
本文档使用 [mkdocs](http://www.mkdocs.org/) 编写，`pip install mkdocs` 安装mkdocs。

> 如果对 easy_install, pip, python setup.py install 这些有疑问。
> 
> 参见: [http://zengrong.net/post/2169.htm](http://zengrong.net/post/2169.htm)

**推荐markdown编写文档。**

markdown为Web博客书写而设计，目前主流网站均支持。语法介绍： [http://www.appinn.com/markdown/](http://www.appinn.com/markdown/)

**reStructuredText介绍**

Python默认的文档书写格式是reStructuredText，文档生成工具是sphinx-docs [http://www.sphinx-doc.org/en/stable/](http://www.sphinx-doc.org/en/stable/) .

对复杂科技文档书写有兴趣，建议学习。它包括了数学公式、代码高亮、功能插件齐全、多格式文件转换、对大型文档结构支持更友好。

**Pandoc**

顺便推荐格式转换工具 pandoc: [http://pandoc.org/](http://pandoc.org/)

