# sql2Markdown
### 作用：
根据sql文件生成markdown表结构文档
代码地址：[https://github.com/xiuhongwu/sql2Markdown](https://github.com/xiuhongwu/sql2Markdown)

### 缘起：
我是公司的新人，有一次改bug涉及到数据库，表多字段多，于是问大佬有没有表结构文档，问了三遍，回答是没有！！！

记得刚进公司培训的时候，有一位大佬给的表结构文档说是根据数据库自动生成的。百度一下发现真的有这种工具，试用了三个。第一个已经忘了，不好用。

第二个叫[tablego](http://www.tablego.cn/)，Java写的，我感觉非常好，目前作者一直在更新。网址：
[http://www.tablego.cn/](http://www.tablego.cn/)

不过它是连接数据库，我本机的Mysql是免安装那种，装了Mysql Connector/ODBC Date Source Configuration，不了解这种方式，也没查，因为我想找一个由sql文件生成文档的程序，然后发现了第三个。

github地址：[AutoBuildDocFromDB](https://github.com/2liang/AutoBuildDocFromDB)
，Python写的，根据sql文件生成markdown文档，好几年了，好像后边没有维护，也有可能作者换了github帐号。

然后我就好奇，到底是怎么实现的？能不能用java自己写一个？

于是我就开始了尝试，最然python并不精通，但是实现的过程还是能通过代码看出来的。

### 思路
sql文件存储的实际就是建表语句，用记事本打开就能看到。

java IO ---> 读取以空行分段 ---> 正则表达式匹配每一段中是否有creat语句，有就存储表名，没有这一段就删掉，剩下的都是建表语句 ---> 存储在map中 ---> 对这些段匹配字段名、字段类型、字段描述，获取数据之后根据markdown语法组合 ---> 输出到文件


### 注意
1.目前的匹配规则仅仅适配我接触到的sql文件，并且仅仅是好奇写着玩，实际没有用到，可能会出现各种各样的不匹配的情况，在查看软件[tablego](http://www.tablego.cn/)的更新信息时也发现，这个软件也一直在更新适配其他情况。

2.代码很乱，后期会整理

### 截图
sql文件建表语句
![sql文件建表语句](https://img-blog.csdnimg.cn/20190912160326225.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM0MTM2NTY5,size_16,color_FFFFFF,t_70)

生成的markdown语句

![生成的markdown语句](https://img-blog.csdnimg.cn/20190912160447908.png)

效果

![效果](https://img-blog.csdnimg.cn/20190912160605930.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM0MTM2NTY5,size_16,color_FFFFFF,t_70)
