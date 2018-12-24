数据库操作
1.use databasename     //切换数据库；
2.drop databasename    //删除数据库；
3.show tables          //显示当前数据库的所有表；
4.describe tablename   // 消失当前数据库的某个表的具体信息；
5.show databases       //显示所有数据库；
授权：
1.revoke all privileges on *.* from root@"%"; 
2.delete from user where user="root" and host="%";
3.flush privileges;

1.alter table t1 rename t2;   //将t1表重命名为t2；
2.mysqldump -h host -u root -p dbname >dbname_backuo.sql;   //数据库备份；

一些不常用的命令
1.select version();     //显示mysql的版本；
2.help select:          //查看select帮助；
3.show status;          //查看mysql的详细使用情况；

对数据库表的操作
1.show tables;  //显示所选数据库的所有数据表；
2.create table table_name(     //创建数据库；
id  int not null primary key auto_increment,    //auto_increment自增约束
age float not null default 0,                   //default 0   数值约束
name  varchar(20)  unique,                      //unique  唯一约束，不能重复
comeTime datae  not null default CURRENT_TIMESTAMP,
(1)class_id int references  class(id)    ,          //外键约束
//(2)userid  int not null,
//constraint fk_user_role foreign key(userid) references user(id)
);
3.desc tablename;      //查看当前数据库表结构；
4.drop table table_name;  //删除数据表；

插入删除
1.insert into table_name(columnName,columnName,...)  values(values,values,...);   //插入数据
2.insert into table_name(columnName,columnName,...) values(values,values,...),(values,values,...),()....;
3.insert into table_name1(column1,column2...) select column1,column2... from table_name2
//colunm1,colunm2数据类型及数据类型长度都必须相同；
删除数据
1.truncate table table_name;     //保留数据表的结构，清空其数据；
2.delete from table_name;     //删除表中所有数据；
3.delete from table_name where  条件  ;    删除指定条件的数据；
更新数据
1.update table_name  set 列名称 = values where 条件；   //更新数据；

修改表alter
1.alter table table_name drop column column_name;//删除某列；
2.alter table table_name modify column column_name new_type;    //修改某列的数据类型；
3.alter table table_name change  old_columnName   new_columnName  new_type;    //修改某列的名字和类型；
4.alter table tableName drop foreign key keyName;      //删除外键约束；keyName时外键别名；

查询语句select
1.不匹配：  <>  ,  !=
SELECT id FROM table_name WHERE id <> 1003
2.select column form table_name where id BETWEEN value1  AND value2;  //范围选择；
3.select column from table_name  where filed IS null;  //空值检查；
4.select * from table_name where  sql1  and sql2;    // sql1, sql2;同时满足；
5.select * from table_name where  sql1  or sql2;     //sql1,sql2 满足一个就好了；
6.允许and和or结合,但是优先处理and操作
7.select * from table_name where column in(value1,value2);   //括号的每个值都匹配；
8.select * from wms_respository where repo_id  REGEXP '[0-9]';   //select 条件也支持正则表达式；


已经建好的表的约束
1.alter table table_name add constraint 约束名  foreign key table_name(column)  references  主键表名(column_id);
2.SELECT * FROM INFORMATION_SCHEMA.KEY_COLUMN_USAGE;  //查看所有约束
