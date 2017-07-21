# 4. 网络编程

- HTTP协议/RESTful
- Web开发
- TCP/UDP协议
- WebScoket

- CDN服务(暂无)
- DNS服务(暂无)
- 负载均衡(Nginx/云平台)
（交给运维解决，但研发需要了解和提出需求）

## 第一期规划

**6月12日 至 6月23日**

1. 梳理对HTTP协议和RESTful的理解，建立内部的RESTful风格标准
2. 以Flask为核心，确认内部的Flask-rest框架，并兼容SQL/ORM/MongoDB等数据库对接

## 第二期规划

**6月26日 至 7月7日**

1. 添加API的参数格式校验系统
2. 理解Authentication认证，理解 Token/OAuth等用户认证模式，添加认证体系
3. API和管理后台一样，添加角色和权限体系
4. 优化API的工程结构，建立像Ruby on Rails或Django-rest-framework一样的资源中心代码简洁的模式
5. 添加API服务的性能测试，上线之前要做性能评估

## 第三期规划
**7月10日 至 7月21日**

1. 梳理对TCP/UPD的使用，建立标准的数据路由、数据传输服务；如果内部有需要，可以使用Thrift
2. 梳理对实时性服务的需求，建立WebScoket或其他方案的实时服务
3. 梳理对文件系统/消息系统的需求
