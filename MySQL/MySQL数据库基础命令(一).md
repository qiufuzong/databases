# 一、连接数据库

```mysql
-- 假设数据库地址在 127.0.0.1 3306 账号和密码为root
-- -h	   指定ip地址(默认127.0.0.1/localhost)
-- -P(大写) 指定端口(默认3306)
-- -u      用户名
-- -p      密码(正常是在这里进行回车，避免密码暴露,如果要输入密码不要空格)
mysql -h 127.0.0.1 -P 3306 -u root -p
mysql -h 127.0.0.1 -P 3306 -u root -proot

-- 可以不加空格
mysql -h127.0.0.1 -P3306 -uroot -proot

```





# 二、数据库操作

```mysql
-- 查看所有数据库
show databases;
SHOW DATABASES;

-- 查看单个数据库/查看数据库字符集
SHOW CREATE DATABASE database_name;

-- 新增数据库
CREATE DATABASE database_name;

-- 新增数据库 指定字符集和字符排序规则
CREATE DATABASE database_name DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;

-- 选择数据库
USE database_name;

-- 删除数据库
DROP DATABASE database_name;

-- 修改数据库编码和字符排序规则
ALTER DATABASE database_name DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci;
```





# 三、表操作（DDL）

## 1）查询表

```mysql
-- 查询所有表;
show tables;

-- 模糊查询
show tables like "%table_name%";

select TABLE_NAME  from  INFORMATION_SCHEMA.TABLES  where TABLE_SCHEMA ='dbname' and  TABLE_NAME ='tablename' ;

-- 查看创建表sql
show create table table_name;

-- 查看表字段
desc table_name;
show columns from table_name;

-- 查看表字段包括备注
show full columns from table_name;

```



## 2）创建表

```mysql
-- 创建表;
-- auto_increment 表示自增
-- primary key 表示主键
-- engine 可以指定引擎
-- charset 指定字符集
-- collate 指定字符集排序规则
create tbale table_name(
id int(1) auto_increment primary key,
name varchar(64) default '' comment '姓名'    
)engine=Innodb DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

```



## 3）修改表

```mysql
 -- 修改表名
 ALTER TABLE old_table_name RENAME TO new_table_name;
 
 -- 修改存储引擎
 alter table tableName engine=myisam;

```



## 4）表字段

### 1.新增表字段

```mysql
-- 新增表字段
alter table table_name add [cloumn] xxx varchar(32) default '' comment '新增字段，column可以省略';

-- 新增字段，位置：第一列
alter table table_name add xxx varchar(32) default '' comment '新增字段，位置是第一列';

-- 新增字段，位置：在某个字段后
alter table table_name add xxx varchar(32) default '' comment '新增字段，位置是id之后' after id;

-- 新增多个字段
alter table table_name add xxx varchar(32),add xxx2 int(2);
```

### 2.删除表字段

```mysql
-- 删除字段
alter table table_name drop [column] xxxx;

-- 删除多个字段
alter table table_name drop [column] xxxx,drop xxxx2;

```

### 3. 修改表字段

````mysql
-- 修改字段 类型/注释/默认值/位置
alter table table_name modify [column] old_column varchar(32) default null comment '修改备注' after id;

-- 修改字段名称/类型/注释/默认值/位置  (重命名)
alter table table_name change [column] old_column new_column varchar(32) default null comment '修改备注';

````



# 四、数据操作（DML）

## 1）查询

```mysql
-- 查询所有
select * from table_name;

-- 指定字段
select c1,c2 from table_name;

-- 字段别名
select c1 as 'a',c2 as 'b' from table_name;
select c1 'a',c2 'b' from table_name;

-- 条件查询（等值）
select * from table_name where name = 'xxxx';
select * from table_name where name = 'xxxx' and no = 123;

-- 模糊查询（name包含张）
select * from table_name where name like '%张%';
 
-- 模糊查询（name已张开头的）
select * from table_name where name like '张%';

-- 模糊查询（name已张结尾的）
select * from table_name where name like '%张';


```

## 2）新增

```mysql
-- 新增不指定字段
insert into table_name values (c1,c2,c3);

-- 新增指定字段
insert into table_name(c1,c2,c3) values (x1,x2,x3);

-- 批量新增
insert into table_name(c1,c2,c3) values (x1,x2,x3),(a1,a2,a3),(b1,b2,b3);

-- 新增忽略重复(ignore)
insert ignore into table_name(c1,c2,c3) values (x1,x2,x3),(a1,a2,a3),(b1,b2,b3);
```

## 3）修改

```mysql
-- 根据条件修改
update table_name set c1 = v1 where id = 1;
update table_name set c1 = v1 ,c2 = v2 ,c3 = v3 where id = 1;
```

## 4）删除

```mysql
delete from table_name where id = 1;
```

