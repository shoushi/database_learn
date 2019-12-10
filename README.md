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
  1.show index from aaa;
  2.show keys from aaa;
