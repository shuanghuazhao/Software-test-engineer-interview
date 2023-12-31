[](#anchor_1)

[](#anchor_2)1\. 什么是数据库？
------------------------

数据库 (Database) 是按照数据结构来组织、存储和管理数据的仓库

[](#anchor_3)2\. 什么是关系型数据库，主键，外键，索引分别是什么？
-----------------------------------------

关系型数据库是由多张能互相联接的二维行列表格组成的数据库

主关键字 (primary key) 是表中的一个或多个字段，它的值用于唯一地标识表中的某一条记录

外键表示了两个关系之间的相关联系。以另一个关系的外键作主关键字的表被称为主表，具有此外键 的表被称为主表的从表。外键又称作外关键字

在关系数据库中，索引是一种单独的、物理的对数据库表中一列或多列的值进行排序的一种存储结构，它是某个表中一列或若干列值的集合和相应的指向表中物理标识这些值的数据页的逻辑指针清单

[](#anchor_4)3\. 写出表的增删改查 SQL 语法
--------------------------------

表的创建：`create table 表名 (列名 1 类型 约束，列 2 类型 约束…)`

表的删除：`drop table 表名`

表的更改（结构的更改，不是记录的更新）：`alter table 表名 add|drop 列名|约束名`

插入记录：`insert into 表名… values …`

更新记录：`update 表名 set 列名 = 值 where 条件`

删除记录：`delete from 表名 where 条件`

[](#anchor_5)4\. SQL 的表连接方式有哪些？
-------------------------------

SQL 中连接按结果集分为：内连接，外连接，交叉连接

内连接：inner join on，两表都满足的组合。内连接分为等值连接，不等连接，自然连接。等值连接：两表中相同的列都会出现在结果集中。

自然连接：两表中具体相同列表的列会合并为同一列出现在结果集中。

外连接：分为左（外）连接，右（外）连接，全连接

左（外）连接：A left (outer) join B, 以 A 表为基础，A 表的全部数据，B 表有的组合，没有的为 null。

右（外）连接：A right(outer) join B, 以 B 表为基础，B 表的全部数据，A 表有的组合，没有的为 null。

全连接：A full (outer) join 两表相同的组合在一起，A 表有，B 表没有的数据（显示为 null），同样 B 表有，A 表没有的显示为 null。

交叉连接：cross join, 就是笛卡尔乘积。

[](#anchor_6)5\. 表的连接查询方式有哪些，有什么区别？
-----------------------------------

交叉连接即笛卡儿乘积，是指两个关系中所有元组的任意组合

使用内连接时，如果两个表的相关字段满足连接条件，就从这两个表中提取数据并组合成新的记录 自连接是一种特殊的内连接，它是指相互连接的表在物理上为同一张表，但可以在逻辑上分为两张表 外连接是只限制一张表中的数据必须满足连接条件，而另一张表中的数据可以不满足连接条件的连接 方式

[](#anchor_7)6\. 什么三范式？
-----------------------

1NF: 表中的字段都是单一属性，不再可分。

2NF：在 1NF 的基础上，表中所有的非主属性都必须完全依赖于任意一组候选键，不能仅依赖于候选键中的某个属性。

3NF：在 2NF 的基础上，表中所有的属性都不依赖其他非主属性。

简单的说就是：1NF 表示每个属性不可分割，2NF 表示非主属性不存在对主键的部分依赖，3NF 表示不存在非主属性对主键的依赖传递。

[](#anchor_8)7\. SQL 的 select 语句完整的执行顺序？
----------------------------------------

1.  from 子句组装来自不同数据源的数据；
2.  where 子句基于指定的条件对记录行进行筛选；
3.  group by 子句将数据划分为多个分组；
4.  使用聚集函数进行计算；
5.  使用 having 子句筛选分组；
6.  计算所有的表达式；
7.  select 的字段；
8.  使用 order by 对结果集进行排序。

[](#anchor_9)8\. 说一下 Mysql 数据库存储的原理？
------------------------------------

储存过程是一个可编程的函数，它在数据库中创建并保存。它可以有 SQL 语句和一些特殊的控制结构组成。当希望在不同的应用程序或平台上执行相同的函数，或者封装特定功能时，存储过程是非常有用的。数据库中的存储过程可以看做是对编程中面向对象方法的模拟。它允许控制数据的访问方式。

存储过程通常有以下优点：

1.  存储过程能实现较快的执行速度
2.  存储过程允许标准组件是编程。
3.  存储过程可以用流程控制语句编写，有很强的灵活性，可以完成复杂的判断和较复杂的运算。
4.  存储过程可被作为一种安全机制来充分利用。
5.  存储过程能够减少网络流量

[](#anchor_10)9\. 事务的特性？
------------------------

1.  原子性 (Atomicity)：事务中的全部操作在数据库中是不可分割的，要么全部完成，要么均不执行。
2.  一致性 (Consistency)：几个并行执行的事务，其执行结果必须与按某一顺序串行执行的结果相一致。
3.  隔离性 (Isolation)：事务的执行不受其他事务的干扰，事务执行的中间结果对其他事务必须是透明的。
4.  持久性 (Durability)：对于任意已提交事务，系统必须保证该事务对数据库的改变不被丢失，即使数 据库出现故障

[](#anchor_11)10\. 简述什么是存储过程和触发器？
---------------------------------

存储过程：是数据库中的一个对象，Transact-SQL 语句的预编译集合，这些语句在一个名称下存储并作为一个单元进行处理。（可以理解为 C 语言中的函数，有参数、返回值等函数特性）

触发器是一种特殊类型的存储过程，当使用下面的一种或多种数据修改操作在指定表中对数据进行修改时，触发器会生效：UPDATE、INSERT 或 DELETE。

[](#anchor_12)11\. 什么是数据库索引？
----------------------------

数据库索引，是数据库管理系统中一个排序的数据结构，以协助快速查询、更新数据库表中数据。索引的实现通常使用 B\_TREE。B\_TREE 索引加速了数据访问，因为存储引擎不会再去扫描整张表得到需要的数据；相反，它从根节点开始，根节点保存了子节点的指针，存储引擎会根据指针快速寻找数据。

[](#anchor_13)12\. 数据库怎么优化查询效率？
-------------------------------

1.  储存引擎选择：如果数据表需要事务处理，应该考虑使用 InnoDB，因为它完全符合 ACID 特性。如果不需要事务处理，使用默认存储引擎 MyISAM 是比较明智的
2.  分表分库，主从。
3.  对查询进行优化，要尽量避免全表扫描，首先应考虑在 where 及 order by 涉及的列上建立索引
4.  应尽量避免在 where 子句中对字段进行 null 值判断，否则将导致引擎放弃使用索引而进行全表扫描
5.  应尽量避免在 where 子句中使用！= 或<>操作符，否则将引擎放弃使用索引而进行全表扫描
6.  应尽量避免在 where 子句中使用 or 来连接条件，如果一个字段有索引，一个字段没有索引，将导致引擎放弃使用索引而进行全表扫描
7.  Update 语句，如果只更改 1、2 个字段，不要 Update 全部字段，否则频繁调用会引起明显的性能消耗，同时带来大量日志
8.  对于多张大数据量（这里几百条就算大了）的表 JOIN，要先分页再 JOIN，否则逻辑读会很高，性能很差。

[](#anchor_14)13\. 你用的 Mysql 是哪个引擎，各引擎之间有什么区别？
----------------------------------------------

主要 MyISAM 与 InnoDB 两个引擎，其主要区别如下：InnoDB 支持事务，MyISAM 不支持，这一点是非常之重要。事务是一种高级的处理方式，如在一些列增删改中只要哪个出错还可以回滚还原， 而 MyISAM 就不可以了；

MyISAM 适合查询以及插入为主的应用，InnoDB 适合频繁修改以及涉及到安全性较高的应用；

InnoDB 支持外键，MyISAM 不支持；

MyISAM 是默认引擎，InnoDB 需要指定； InnoDB 不支持 FULLTEXT 类型的索引；

InnoDB 中不保存表的行数，如 select count() from table 时，InnoDB；需要扫描一遍整个表来计算有多少行，但是 MyISAM 只要简单的读出保存好的行数即可。注意的是，当 count() 语句包含 where 条件时 MyISAM 也需要扫描整个表；

对于自增长的字段，InnoDB 中必须包含只有该字段的索引，但是在 MyISAM 表中可以和其他字段一起建立联合索引；清空整个表时，InnoDB 是一行一行的删除，效率非常慢。MyISAM 则会重建表；

InnoDB 支持行锁（某些情况下还是锁整表，如 update table set a=1 where user like '%lee%'

[](#anchor_15)14\. 如何对查询命令进行优化？
-------------------------------

1.  应尽量避免全表扫描，首先应考虑在 where 及 order by 涉及的列上建立索。
2.  应尽量避免在 where 子句中对字段进行 null 值判断，避免使用！= 或<>操作符，避免使用 or 连接条件，或在 where 子句中使用参数、对字段进行表达式或函数操作，否则会导致权标扫描
3.  不要在 where 子句中的“=”左边进行函数、算术运算或其他表达式运算，否则系统将可能无法正确使用索引。
4.  使用索引字段作为条件时，如果该索引是复合索引，那么必须使用到该索引中的第一个字段作为条件 时才能保证系统使用该索引，否则该索引将不会被使用。
5.  很多时候可考虑用 exists 代替 in。f. 尽量使用数字型字段。
6.  尽可能的使用 varchar/nvarchar 代替 char/nchar。
7.  任何地方都不要使用 select from t ，用具体的字段列表代替“”，不要返回用不到的任何字段。尽量使用表变量来代替临时表。
8.  避免频繁创建和删除临时表，以减少系统表资源的消耗。
9.  尽量避免使用游标，因为游标的效率较差。
10.  在所有的存储过程和触发器的开始处设置 SET NOCOUNT ON ，在结束时设置 SETNOCOUNT OFF。m. 尽量避免大事务操作，提高系统并发能力。
11.  尽量避免向客户端返回大数据量，若数据量过大，应该考虑相应需求是否合理。

[](#anchor_16)15\. 数据库的优化？
--------------------------

1.  优化索引、SQL 语句、分析慢查询；
2.  设计表的时候严格根据数据库的设计范式来设计数据库；
3.  使用缓存，把经常访问到的数据而且不需要经常变化的数据放在缓存中，能节约磁盘 IO
4.  优化硬件；采用 SSD，使用磁盘队列技术 (RAID0,RAID1,RDID5) 等
5.  采用 MySQL 内部自带的表分区技术，把数据分层不同的文件，能够提高磁盘的读取效率；
6.  垂直分表；把一些不经常读的数据放在一张表里，节约磁盘 I/O；
7.  主从分离读写；采用主从复制把数据库的读操作和写入操作分离开来；
8.  分库分表分机器（数据量特别大），主要的原理就是数据路由；
9.  选择合适的表引擎，参数上的优化
10.  进行架构级别的缓存，静态化和分布式；
11.  不采用全文索引；
12.  采用更快的存储方式，例如 NoSQL 存储经常访问的数据。

[](#anchor_17)16\. Sql 注入是如何产生的，如何防止？
-------------------------------------

程序开发过程中不注意规范书写 sql 语句和对特殊字符进行过滤，导致客户端可以通过全局变量 POST 和 GET 提交一些 sql 语句正常执行。产生 Sql 注入。

下面是防止办法：

1.  过滤掉一些常见的数据库操作关键字，或者通过系统函数来进行过滤。
2.  在 PHP 配置文件中将 Register_globals=off; 设置为关闭状态
3.  SQL 语句书写的时候尽量不要省略小引号 (tab 键上面那个）和单引号
4.  提高数据库命名技巧，对于一些重要的字段根据程序的特点命名，取不易被猜到的
5.  对于常用的方法加以封装，避免直接暴漏 SQL 语句
6.  开启 PHP 安全模式：Safe_mode=on;
7.  打开 magic\_quotes\_gpc 来防止 SQL 注入
8.  控制错误信息：关闭错误提示信息，将错误信息写到系统日志。
9.  使用 mysqli 或 pdo 预处理。

[](#anchor_18)17\. NoSQL 和关系数据库的区别？
-----------------------------------

1.  SQL 数据存在特定结构的表中；而 NoSQL 则更加灵活和可扩展，存储方式可以省是 JSON 文档、哈希表或者其他方式。
2.  在 SQL 中，必须定义好表和字段结构后才能添加数据，例如定义表的主键 (primary key)，索引 (index), 触发器 (trigger), 存储过程 (stored procedure) 等。表结构可以在被定义之后更新，但是如果有比较大的结构变更的话就会变得比较复杂。在 NoSQL 中，数据可以在任何时候任何地方添加，不需要先定义表。
3.  SQL 中如果需要增加外部关联数据的话，规范化做法是在原表中增加一个外键，关联外部数据表。而在 NoSQL 中除了这种规范化的外部数据表做法以外，我们还能用如下的非规范化方式把外部数据直接放到原数据集中，以提高查询效率。缺点也比较明显，更新审核人数据的时候将会比较麻烦。
4.  SQL 中可以使用 JOIN 表链接方式将多个关系数据表中的数据用一条简单的查询语句查询出来。NoSQL 暂未提供类似 JOIN 的查询方式对多个数据集中的数据做查询。所以大部分 NoSQL 使用非规范化的数据存储方式存储数据。
5.  SQL 中不允许删除已经被使用的外部数据，而 NoSQL 中则没有这种强耦合的概念，可以随时删除任何数据。
6.  SQL 中如果多张表数据需要同批次被更新，即如果其中一张表更新失败的话其他表也不能更新成功。这种场景可以通过事务来控制，可以在所有命令完成后再统一提交事务。而 NoSQL 中没有事务这个概念，每一个数据集的操作都是原子级的。
7.  在相同水平的系统设计的前提下，因为 NoSQL 中省略了 JOIN 查询的消耗，故理论上性能上是优于 SQL 的 。

[](#anchor_19)18\. MySQL 与 MongoDB 本质之间最基本的差别是什么
------------------------------------------------

差别在多方面，例如：数据的表示、查询、关系、事务、模式的设计和定义、速度和性能。MongoDB 是由 C++ 语言编写的，是一个基于分布式文件存储的开源数据库系统。在高负载的情况下，添加更多的节点， 可以保证服务器性能。

MongoDB 旨在为 WEB 应用提供可扩展的高性能数据存储解决方案。

MongoDB 将数据存储为一个文档，数据结构由键值 (key=>value) 对组成。MongoDB 文档类似于 JSON 对象。字段值可以包含其他文档，数组及文档数组。

MongoDB 是一个面向文档的数据库，目前由 10gen 开发并维护，它的功能丰富齐全，所以完全可以替代 MySQL。

与 MySQL 等关系型数据库相比，MongoDB 的优点如下：

1.  弱一致性，更能保证用户的访问速度。
2.  文档结构的存储方式，能够更便捷的获取数据。
3.  内置 GridFS，支持大容量的存储。
4.  内置 Sharding。
5.  第三方支持丰富。（这是与其他的 NoSQL 相比，MongoDB 也具有的优势）
6.  性能优越：

MongoDB 本身它还算比较年轻的一个产品，所以它的问题，就是成熟度肯定没有传统 MySQL 那么成熟稳定。所以在使用的时候： 尽量使用稳定版，不要在线上使用开发版，这是一个大原则；

另外一点，备份很重要，MongoDB 如果出现一些异常情况，备份一定是要能跟上。除了通过传统的复制的方式来做备份，离线备份也还是要有，不管你是用什么方式，都要有一个完整的离线备份。 往往最后出现了特殊情况，它能帮助到你；另外，MongoDB 性能的一个关键点就是索引，索引是不是能有比较好的使用效率，索引是不是能够放在内存中，这样能够提升随机读写的性能。如果你的索 引不能完全放在内存中， 一旦出现随机读写比较高的时候，它就会频繁地进行磁盘交换，这个时候， MongoDB 的性能就会急剧下降， 会出现波动。 另外，MongoDB 还有一个最大的缺点，就是它占用的空间很大，因为它属于典型空间换时间原则的类型。那么它的磁盘空间比普通数据库会浪费一些，而且到目前为止它还没有实现在线压缩功能，

在 MongoDB 中频繁的进行数据增删改时，如果记录变了，例如数据大小发生了变化，这时候容易产生一些数据碎片，出现碎片引发的结果，一个是索引会出现性能问题。 另外一个就是在一定的时间后，所占空间会莫名其妙地增大，所以要定期把数据库做修复，定期 重新做索引，这样会提升 MongoDB 的稳定性和效率。在最新的版本里，它已经在实现在线压缩，估计应该在 2.0 版左右，应该能够实现在线压缩，可以在后台执行现在 repair DataBase 的一些操作。 如果那样，就解决了目前困扰我们的大问题。

[](#anchor_20)19\. Mysql 数据库中怎么实现分页？
------------------------------------

`select * from table limit (start-1)*limit,limit;`

其中 start 是页码，limit 是每页显示的条数。

[](#anchor_21)20\. Mysql 数据库的操作？
--------------------------------

修改表 \- 修改字段，重命名版：

alter table 表名 change 原名新名类型及约束；

alter table students change birthday birth datetime not null; 修改表 - 修改字段，不重名版本：

alter table 表名 modify 列名类型和约束；

alter table students modify birth date not null;

全列插入：insert into 表名 values(...) insert into students values(0,"郭靖", 1,"内蒙","2017-6");

部分插入：值的顺序与给出的列顺序对应： insert into students(name, birthday) values("黄蓉","2017-8");

修改：update 表名 set 列 1= 值 1，列 2= 值 2.。where update students set gender=0, homwtown="古墓"， where id = 5;

备份：mysqldump -uroot -p 数据库名 > python.sql;

恢复：mysql -uroot -p 数据库名< python.sql;

[](#anchor_22)21\. 优化数据库？提高数据库的性能？
----------------------------------

1.  对语句的优化
    
    1.  用程序中，保证在实现功能的基础上，尽量减少对数据库的访问次数；通过搜索参数，尽量
    2.  减 少对表的访问行数，最小化结果集，从而减轻网络负担；能够分开的操作尽量分开处理，提高每次的响应速度；在数据窗口使用 SQL 时，尽量把使用的索引放在选择的首列；算法的结构尽量简单；
    3.  在查询时，不要过多地使用通配符如 SELECT * FROM T1 语句，要用到几列就选择几列如：SELECT COL1,COL2 FROM T1；
    4.  在可能的情况下尽量限制尽量结果集行数如：SELECT TOP 300 COL1,COL2,COL3 FROMT1, 因为某些情况下用户是不需要那么多的数据的。
    5.  不要在应用中使用数据库游标，游标是非常有用的工具，但比使用常规的、面向集的 SQL 语句需要更大的开销；按照特定顺序提取数据的查找。
2.  避免使用不兼容的数据类型
    
    例如 float 和 int、char 和 varchar、binary 和 varbinary 是不兼容的。数据类型的不兼容可能使优化器无法执行一些本来可以进行的优化操作。例如：
    
    SELECT name FROM employee WHERE salary > 60000
    
    在这条语句中，如 salary 字段是 money 型的，则优化器很难对其进行优化，因为 60000 是个整型数。我们应当在编程时将整型转化成为钱币型，而不要等到运行时转化。若在查询时强制转换，查询速 度会明显减慢。
    
3.  避免在 WHERE 子句中对字段进行函数或表达式操作。
    
    若进行函数或表达式操作，将导致引擎放弃使用索引而进行全表扫描。
    
4.  避免使用 != 或 <>、IS NULL 或 IS NOT NULL、IN ，NOT IN 等这样的操作符
    
5.  尽量使用数字型字段
    
6.  合理使用 EXISTS,NOT EXISTS 子句。
    
7.  尽量避免在索引过的字符数据中，使用非打头字母搜索。
    
8.  分利用连接条件
    
9.  消除对大型表行数据的顺序存取
    
10.  避免困难的正规表达式
    
11.  使用视图加速查询
    
12.  能够用 BETWEEN 的就不要用 IN
    
13.  DISTINCT 的就不用 GROUP BY
    
14.  部分利用索引
    
15.  能用 UNION ALL 就不要用 UNION
    
16.  不要写一些不做任何事的查询
    
17.  尽量不要用 SELECT INTO 语句
    
18.  必要时强制查询优化器使用某个索引
    
19.  虽然 UPDATE、DELETE 语句的写法基本固定，但是还是对 UPDATE 语句给点建议：
    
    1.  尽量不要修改主键字段。
    2.  当修改 VARCHAR 型字段时，尽量使用相同长度内容的值代替。
    3.  尽量最小化对于含有 UPDATE 触发器的表的 UPDATE 操作。
    4.  避免 UPDATE 将要复制到其他数据库的列。
    5.  避免 UPDATE 建有很多索引的列。
    6.  避免 UPDATE 在 WHERE 子句条件中的列。

[](#anchor_23)22\. 什么是数据的完整性？
-----------------------------

数据完整性指的是存储在数据库中的数据的一致性和准确性。 完整性分类：

1.  实体完整性：主键值必须唯一且非空。（主键约束）
2.  引用完整性（也叫参照完整性）：外键要么为空，要么引用主表中存在的记录。（外键约束）。
3.  用户自定义完整性：针对某一具体关系数据库中的约束条件。

[](#anchor_24)23\. 存储过程和函数的区别？
------------------------------

相同点：存储过程和函数都是为了可重复的执行操作数据库的 sql 语句的集合。

1.  存储过程和函数都是一次编译，就会被缓存起来，下次使用就直接命中已经编译好的 sql 语句，不需要重复使用。减少网络交互，减少网络访问流量。

不同点：标识符不同，函数的标识符是 function，存储过程是 proceduce。

1.  函数中有返回值，且必须有返回值，而过程没有返回值，但是可以通过设置参数类型 (in,out) 来实 现多个参数或者返回值。
2.  存储函数使用 select 调用，存储过程需要使用 call 调用。
3.  select 语句可以在存储过程中调用，但是除了 select..into 之外的 select 语句都不能在函数中使用。
4.  通过 in out 参数，过程相关函数更加灵活，可以返回多个结果。

[](#anchor_25)24\. 怎么进行 SQL 的查询优化？
----------------------------------

1.  从表连接的角度优化：尽量使用内连接，因为内连接是两表都满足的行的组合，而外连接是以其 中一个表的全部为基准。
2.  尽量使用存储过程代替临时写 SQL 语句：因为存储过程是预先编译好的 SQL 语句的集合，这样可以减少编译时间。
3.  从索引的角度优化：对那些常用的查询字段简历索引，这样查询时值进行索引扫描，不读取数据 块。
4.  还有一些常用的 select 优化技巧：
    1.  只查询那些需要访问的字段，来代替 select *
    2.  将过滤记录越多的 where 语句向前移：在一个 SQL 语句中，如果一个 where 条件过滤的数据库记录越多，定位越准确，则该 where 条件越应该前移。

[](#anchor_26)25\. 索引的作用，聚集索引与非聚集索引的区别
--------------------------------------

索引是一个数据库对象，使用索引，可以是数据库程序无须对整个数据进行扫描，就可以在其中找到目标数据，从而提高查找效率。索引的底层采用的是 B 树。

聚集索引：根据记录的 key 再表中排序数据行。

非聚集索引：独立于记录的结构，非聚集所以包含的 key，且每个键值项都有指向该简直的数据行的指针。

聚集索引与非聚集索引的区别：

1.  聚集索引的物理存储按索引排序，非聚集所以的物理存储不按索引排序。
2.  聚集索引插入，更新数据的速度比非聚集索引慢，单查询速度更快。
3.  聚集索引的叶级结点保存的是时间的数据项，而非聚集结点的叶级结点保存的是指向数据项 的指针。
4.  一个表只能有一个聚集索引（因为只有一种排序方式），但可以有多个非聚集索引。
