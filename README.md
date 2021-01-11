# Day1
JDK安装：https://www.oracle.com/java/technologies/javase-downloads.html
Neo4j安装：https://neo4j.com/download-center/
配置好JDK和Neo4j的环境变量
 
先试试是否安装成功了：java -version

启动:neo4j.bat console
第一次启动有默认用户名和密码：neo4j neo4j 
 

Neo4j增删改查：

增：
增加一个节点
create (n:Person {name:'我',age:31})
带有关系属性
create (p:Person{name:"我",age:"31"})-[:包工程{金额:10000}]->(n:Person{name:"好大哥",age:"35"})

删
create (n:Person {name:'TYD',age:31})
match (n:Person{name:"TYD"}) delete n
删除关系
match (p:Person{name:"我",age:"31"})-[f:包工程]->(n:Person{name:"好大哥",age:"35"})
 delete f

改：
加上标签
match (t:Person) where id(t)=789 set t:好人return t
加上属性
match (a:好人) where id(a)=789 set a.战斗力=200 return a
修改属性
match (a:好人) where id(a)=789 set a.战斗力=500 return a

查：(查操作太多啦，直接参考neo4j例子就好)
match (p:Person) - [:包工程] -> (n:Person) return p,n

快速清空数据库：
MATCH (n)
DETACH DELETE n
