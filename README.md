# database_learn 数据库学习笔记
## 平衡二叉树
### 优点：
  1. 通过左右旋实现相对平衡。
  2. 解决二叉树过高导致效率过低。
### 缺点：
  1. 高度过高，导致IO次数过多；
  2. 只有两个分支，所需数据少，以页作为基础单位，一次IO操作，加载的数据过少。
## B-树：
### 优点：
  1. 绝对平衡树。
  2. n(关键字)+1的度
## B+树：
  1. 关键字和度1：1，关键字左闭合。
  2. 数据区全部存储在叶子节点，关键字保存关键字数据更多。
  3. 叶子节点最后一个数据指向下一个节点第一个数据，基于索引扫库更便捷。
  4. 性能稳定，全部在叶子节点命中。
## mysql常用语句：
  1. show status like 'uptime'; //查询数据库启动时间
  2. show status like 'com_select';//查询数据库select 语句
  3. show [session|global] status like ... //session 默认当前窗口，global表示从mysql创建开始计算。
  4. shou status like 'connections'; //查看当前连接数
  5. show status like ''slow_queries//显示慢查询次数
## 定位慢查询：
### 默认10s为一个慢查询。
  show variables like 'long_query_time';
  set long_query_time=1;
  delimiter ;  //修改“；”表示的意义。
## 启动慢查询记录日志

## sql优化：

## 添加索引：

## 查询索引:
  1. show index from aaa;
  2. show keys from aaa;
  1. show status like 'Header_read%';//查询索引使用率
      + Header_read_key 越高越好，表示使用索引次数多
      + Header_read_rnd_next 越低越好
## 如何选择mysql存储引擎
  1. Myisam,对事务要求不高，同时以查询和添加为主的情况。
  2. INNODB,对事务要求高，数据重要。
  2. Memory，数据变化频繁，不需要入库，查询、修改频繁。
## Myisam引擎,INNODB引擎的区别
  1. 事务安全，Myisam不支持事务。
  1. 查询添加速度，Myisam速度快。
  3. Myisam支持全文索引。
  4. Myisam为表锁，INNODB为行锁。
  5. Myisam不支持外键。
## 水平分割
  通过一定的策略将表__离散__(通过对某一值取模分表)的分割开来，减少表的体量，提高查询效率。
## 垂直分割
  将不需要的字段等分割出来，新建一个表保存，注意表的关联性。
## 读写分离
  1. 将写操作（insert,update,delete）同读操作（select）分离，写操作查询master数据库、读操作访问slave数据库。
  2. master复制备份多份slave数据库。
  3. 轮询机制或者其他决定访问哪个salve数据库，实现负载均衡。
  4. 写的操作很多的话不适合这种集群方式。
  5. 数据库优化都会加索引，但是加了索引对查询有优化，但是会影响写入，因为写入数据会更新索引。所以做了主从之后，我们可以单独的针对从库(读库)      做索引上的优化，而主库(写库)可以减少索引而提高写的效率。
  
  
