# DevOps

- 代码协作: Gitlab
- 自动化安装 Cobbler
- 部署管理 SaltStack/Fabric
- 自动化监控 Zabbix
- 错误收集 Sentry
- 持续交付 Jenkins
- 日志收集查询 Elastic Stack
- 虚似化/容器化 OpenStack/Docker

## 第一期规划

**6月12日 至 6月23日**

建立标准：

- Git分支规范；
- 部署模式；

对比 Jenkins + Fabric/SaltStack/Ansible 方案；
确认配置管理+持续集成的最佳方案，可能需要自定制开发。

具体去修改项目尝试，确认最佳实践；
撰写文档和分享PT；
为其他组提供最方便的对接方案。

## 第二期规划

**6月26日 至 7月7日**

目标一：

梳理所有的在线服务，确认所有服务目前的机器配置、数据库、周边资源使用情况。
确认哪些项目需要放弃、合并、对接新标准，对接入Jenkins+Ansible管理配置中，为之后Docker容器化做准备。

目标二：

- 监控模式 Sentry + Zabbix 报警
- 日志收集 Elastic Stack 数据路由，大数据量对接 kafka/Redis

## 第三期规划
**7月10日 至 7月21日**

利用上期的成果：资源梳理清楚、 SaltStack/Ansible 资源配置管理方案。

尝试Docker等容器化方案，加速资源利用率。

本部分依赖第二期，具体需要再确认…

## Git分支规范
### 主分支 `master`

- master 为主分支，要保护它的稳定性，随时可用来上线。
- 我们不应该直接在 master 分支上直接提交代码，而是从其它分支的合并。

### 开发分支 dev

- dev 为开发分支，一般包含正在开发的所有新特性，用于测试环境部署和测试。
- 我们不应该直接在 dev 分支上直接提交代码，也不应该把未经测试的代码合并进来，应该尽量保持测试环境干净可用。
- 当 dev 太“脏”以至于不能继续测试之后，可以考虑重新从 master 拉取一次。

### 特性分支 feature-*

- _分支命名_: feature 开头的为特性分支，命名规则为 feature-some_amazing_funs-yourname-date。举例来讲，如天宇10月18日要开发一个通讯录改进的功能，可以自建分支为 feature-contacts_advance-ty-1018。
- 一般 feature 分支应仅包含一个特性，上线（合并至 master）部署验证无误后即可删除。记得及时将 feature 分支 push 至远端。
- 如果合并至 dev 或 master 时发现在 fork 此特性分支之后分支已合并了很多其它分支的提交，请先执行 git rebase，这样能提交历史更加整洁。

### 预上线分支 release-*
- _分支命名_: release- 开头的为预发布分支，命名规则为 release-date。举例来讲，如果10月18日要准备封一个预上线分支，则命名为 release-1018。
- 上线后即可删除。

### 快速修复分支 bug-*
- _分支命名_: bug- 开头的为修复分支，它的命名规则与 feature 分支类似。
- 一般我们如果发现紧急线上 bug，可以将线上代码临时回滚，从最新的 master 分支建立 bug 分支，提交修复代码、测试无误后，合并至 develop 和 master。
- 上线验证无误后，即可将 bug 分支删除。


## 服务监控

### Sentry服务端配置
错误收集记录 和 汇聚整理 平台；使用django + celery + gunicorn 开发部署。

优势：

1. 收集python traceback上下文，将错误发生时的所有变量、代码收集到平台，并且分类/合并统计。
2. 支持多种语言，配置简单（比如flask只需要在create_app处设置，自动将所有错误信息收集）。
3. 权限清楚，分项目、团队记录。
4. 使用django+gunicorn创建，完全开源，多机器扩展部署简单。

缺点：

1. 错误统计分析不足，没有界面化的时序提示
2. 出现雪崩式错误时，sentry无法承载会造成服务拥塞
3. UDP传输错误时，存在丢包现象

> https://docs.sentry.io/server/

测试部署地址：http://192.168.121.107:9000/sentry/

> 登陆用户名：madeling@wecash.net 密码：7777777

### Elastic Stack
本部分只关注elasticsearch的监控作用，数据存储分析在数据服务层关注。

- Elasticsearch
- Kibana
- Logstash
- X-Pack
- Beats
- Elasticsearch Hadoop


### 代码部署

- SaltStack
- Fabric
