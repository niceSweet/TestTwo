1.create sequence  user_id start  with  10 increment by 1 maxvalue 200  minvalue 1000  //自动增长
2.create index user_id_index on user_tableName(id)  tablespace schooltbs;   //
3.sqlplus  "/as sysdba"                     //使用sys用户登录到数据库；
4.conn username/password                     //切换到其它用户下；
5.create  user username identified by password   //创建用户为username  密码为password
6.grant  connect ,resource to username;         //授权；
7.alter table table_name   add(字段名称，数据类型);      //添加类
8.alter table table_name set unuserd column       //删除表中一列；
9.alter table table_name  rename column oldcolumn   to  newcolumb;    //修改列名
10.rename   table_name1  to  table_name2        //修改表名；
11.alter table  table_name  modify(字段名称   新的字段类型)     //修改表字段；
12.alter  table table_name    add  constraint  约束名  约束内容；//添加约束；
