# mysql学习过程

## 1课前操作和基础信息
电脑上本来就有mysql8.4。同时因为觉得打字和终端操作还得练，所以选择凭gitbash完成操作。（才不是懒得下workbench）

## 2运行顺序
确定已经有名为bookshop的专用库（不是的话要改名），且命令行窗口根目录在sql文件夹以后，执行一次以下命令并输入mysql密码（是的如果用bash要输三次这是正常的 暂时没想到怎么优化）（还有cmd版本的命令优化是抄ds的 我cmd没基础（）不过两版都测试过的）。  
然后把最后的输出与queries.sql里的注释比较。  
注意：会把原authors和books清空。

bash版本：
```
mysql -u root -p --default-character-set=utf8mb4 bookshop < schema.sql;mysql -u root -p --default-character-set=utf8mb4 bookshop < seed.sql;mysql -u root -p --default-character-set=utf8mb4 bookshop < queries.sql;
```

cmd版本：
```
( type schema.sql & type seed.sql & type queries.sql ) | mysql -u root -p --default-character-set=utf8mb4 bookshop
```

## 3解释主键与外键 和验证的边界条件

## （有点啰嗦 可以不看）课中碎碎念

数据库的概念还挺好接受的，所以就边听边记一点语法，或者记一点像“有主键的表要先建”的思路。
就是终端输入一旦出错就很难受。虽然能成功从终端导入导出文件，但我还是先在vscode里面写吧。等等seed查询是什么，不太懂啊要查一下。哦原来是说sql文件名。  
竟然还给预设数据，这么好。但为什么没在发的文件里面找到 哎算了有截图就够了。  
等等我还没有搞懂这个AS的语法。  
这个UPDATE SET 频频写错啊。哦原来表名要放UPDATE后面。

如果要描述整个过程和部分语法的话：

1 建库（设置语言和编码）  
2 建表（根据实际业务逻辑设置字段限制）  
（以下为语法）  
3 INSERT INTO db/table() + VALUES()放数据  
4 SELECT FROM 查询 注意：
  
- 应该减少无序查询和无脑*
- BETWEEN AND 两边界必须是小在前，且这个区间两边都是闭的  
  
5 UPDATE table +SET更新  
6 DELETE FROM  
7 JOIN ON 表与表之间的引用关系匹配  
8 WHERE 写条件过滤
