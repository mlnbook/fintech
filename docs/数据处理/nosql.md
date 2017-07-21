##NOSQL
在了解NoSQL之前，首先要先说明下数据库的设计模型&理念。

NoSQL列表: [http://nosql-database.org/](http://nosql-database.org/)

### ACID模型
关系数据库的ACID模型拥有 高一致性 + 可用性；但很难分区部署来提供多部署的容灾可靠性：

- Atomicity原子性：一个事务中所有操作都必须全部完成，要么全部不完成。
- Consistency一致性. 在事务开始或结束时，数据库应该在一致状态。
- Isolation隔离层. 事务将假定只有它自己在操作数据库，彼此不知晓。
- Durability. 一旦事务完成，就不能返回。
- 跨数据库事务：2PC (two-phase commit)， 2PC is the anti-scalability pattern (Pat Helland) 是反可伸缩模式的，JavaEE中的JTA事务可以支持2PC。因为2PC是反模式，尽量不要使用2PC，使用BASE来回避。

### BASE模型
互联网不断发展，海量数据越来越多，之后发展出了BASE模型：

- BASE模型反ACID模型，完全不同ACID模型，牺牲高一致性，获得可用性或可靠性：
- Basically Available基本可用。支持分区失败(e.g. sharding碎片划分数据库)
- Soft state软状态 状态可以有一段时间不同步，异步。
- Eventually consistent最终一致，最终数据是一致的就可以了，而不是时时高一致。

BASE思想的主要实现有

1. 按功能划分数据库
2. sharding碎片

BASE思想主要强调基本的可用性，如果你需要High 可用性，也就是纯粹的高性能，那么就要以一致性或容错性为牺牲，BASE思想的方案在性能上还是有潜力可挖的。
Ps, 这时期开始，Mysql的外键和强一致性越来越多被弃用；但不妨碍Mysql作为开源数据库高可用性和部署便宜…

### CAP理念
2000年时，分布式领域CAP理论被提出：

- Consistency(一致性), 数据一致更新，所有数据变动都是同步的
- Availability(可用性), 好的响应性能
- Partition tolerance(分区容错性) 可靠性

> 定理：任何分布式系统只可同时满足二点，没法三者兼顾。
>
> 忠告：架构师不要将精力浪费在如何设计能满足三者的完美分布式系统，而是应该进行取舍。

现在NoSQL运动丰富了拓展了BASE思想，可按照具体情况定制特别方案，比如忽视一致性，获得高可用性等等，NOSQL应该有下面两个流派：

1. Key-Value存储，如Amaze Dynamo等，可根据CAP三原则灵活选择不同倾向的数据库产品。
2. 领域模型 + 分布式缓存 + 存储 （Qi4j和NoSQL运动），可根据CAP三原则结合自己项目定制灵活的分布式方案，难度高。

这两者共同点：都是关系数据库SQL以外的可选方案，逻辑随着数据分布，任何模型都可以自己持久化，将数据处理和数据存储分离，将读和写分离，存储可以是异步或同步，取决于对一致性的要求程度。

不同点：NOSQL之类的Key-Value存储产品是和关系数据库头碰头的产品BOX，可以适合非Java如PHP RUBY等领域，是一种可以拿来就用的产品；而领域模型 + 分布式缓存 + 存储是一种复杂的架构解决方案，不是产品，但这种方式更灵活，更应该是架构师必须掌握的。

现在Nosql发展到一定规模，但应该不可能替代关系型数据库，只是相互补助。
同时海量数据存储、大数据分析以及之后的人工智能相关的研究都越加清晰…

行业的海量存储解决了、挖掘分析正在发展，智能化刚刚在概念中前行…

## NoSQL数据库类型

NoSQL可以大体上分为4个种类：Key-value、Document-Oriented、Column-Family Databases以及 Graph-Oriented Databases。下面就一览这些类型的特性：

### 键值（Key-Value）数据库

键值数据库就像在传统语言中使用的哈希表。你可以通过key来添加、查询或者删除数据，鉴于使用主键访问，所以会获得不错的性能及扩展性。

产品：Riak、Redis、Memcached、Amazon’s Dynamo、Project Voldemort

有谁在使用：GitHub （Riak）、BestBuy （Riak）、Twitter （Redis和Memcached）、StackOverFlow （Redis）、 Instagram （Redis）、Youtube （Memcached）、Wikipedia（Memcached）

适用的场景

储存用户信息，比如会话、配置文件、参数、购物车等等。这些信息一般都和ID（键）挂钩，这种情景下键值数据库是个很好的选择。

不适用场景

1. 取代通过键查询，而是通过值来查询。Key-Value数据库中根本没有通过值查询的途径。

2. 需要储存数据之间的关系。在Key-Value数据库中不能通过两个或以上的键来关联数据。

3. 事务的支持。在Key-Value数据库中故障产生时不可以进行回滚。

### 面向文档（Document-Oriented）数据库

面向文档数据库会将数据以文档的形式储存。每个文档都是自包含的数据单元，是一系列数据项的集合。每个数据项都有一个名称与对应的值，值既可以是简单的数据类型，如字符串、数字和日期等；也可以是复杂的类型，如有序列表和关联对象。数据存储的最小单位是文档，同一个表中存储的文档属性可以是不同的，数据可以使用XML、JSON或者JSONB等多种形式存储。

产品：MongoDB、CouchDB、RavenDB

有谁在使用：SAP （MongoDB）、Codecademy （MongoDB）、Foursquare （MongoDB）、NBC News （RavenDB）

适用的场景

1. 日志。企业环境下，每个应用程序都有不同的日志信息。Document-Oriented数据库并没有固定的模式，所以我们可以使用它储存不同的信息。

2. 分析。鉴于它的弱模式结构，不改变模式下就可以储存不同的度量方法及添加新的度量。

不适用场景

在不同的文档上添加事务。Document-Oriented数据库并不支持文档间的事务，如果对这方面有需求则不应该选用这个解决方案。

### 列存储（Wide Column Store/Column-Family）数据库

列存储数据库将数据储存在列族（column family）中，一个列族存储经常被一起查询的相关数据。举个例子，如果我们有一个Person类，我们通常会一起查询他们的姓名和年龄而不是薪资。这种情况下，姓名和年龄就会被放入一个列族中，而薪资则在另一个列族中。

产品：Cassandra、HBase

有谁在使用：Ebay （Cassandra）、Instagram （Cassandra）、NASA （Cassandra）、Twitter （Cassandra and HBase）、Facebook （HBase）、Yahoo!（HBase）

适用的场景

1. 日志。因为我们可以将数据储存在不同的列中，每个应用程序可以将信息写入自己的列族中。

2. 博客平台。我们储存每个信息到不同的列族中。举个例子，标签可以储存在一个，类别可以在一个，而文章则在另一个。

不适用场景

1. 如果我们需要ACID事务。Vassandra就不支持事务。

2. 原型设计。如果我们分析Cassandra的数据结构，我们就会发现结构是基于我们期望的数据查询方式而定。在模型设计之初，我们根本不可能去预测它的查询方式，而一旦查询方式改变，我们就必须重新设计列族。

### 图（Graph-Oriented）数据库

图数据库允许我们将数据以图的方式储存。实体会被作为顶点，而实体之间的关系则会被作为边。比如我们有三个实体，Steve Jobs、Apple和Next，则会有两个“Founded by”的边将Apple和Next连接到Steve Jobs。

产品：Neo4J、Infinite Graph、OrientDB

有谁在使用：Adobe （Neo4J）、Cisco （Neo4J）、T-Mobile （Neo4J）

适用的场景

1. 在一些人际/社交关系性强的数据中

2. 推荐引擎。如果我们将数据以图的形式表现，那么将会非常有益于推荐的制定

不适用场景

图数据库的适用范围很小，因为很少有操作涉及到整个图。

## NewSQL

NewSQL是指这样一类新式的关系型数据库管理系统，针对OLTP（读-写）工作负载，追求提供和NoSQL系统相同的扩展性能，且仍然保持ACID和SQL等特性。

1. 支持SQL
2. 具有分布式可扩展性
3. 支持事务执行四要素/ACID Transaction
4. 高可用

本质就是关系型数据库在新时代开始集成了NoSQL的功能。出现一些新出现的数据库，想让自己区分于关系型数据库而提出的概念。目前暂时没有非常成功的大规模商业级应用。