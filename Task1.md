###  MySQL 的安装

由于项目的需要，在老师那边将MySQL直接拷贝了过来，在老师的告知下可以直接使用，所以就遵循了菜鸟教材上的教程进行操作（是几星期之前的事情）

###  SQL与MySQL

SQL：是用于访问和处理数据库的标准计算机语言

MySQL：是一种关系型的数据库，# 我听说过的非关系型数据库是MongoDB



### 项目一

创建表

```mysql
CREATE TABLE email (
ID INT NOT NULL PRIMARY KEY,
Email VARCHAR(255)
);
```

插入数据

```mysql
INSERT INTO email VALUES('1','a@b.com');
INSERT INTO email VALUES('2','c@d.com');
INSERT INTO email VALUES('3','a@b.com');
```

查找重复的电子邮箱

```
SELECT Email

FROM email 

GROUP BY email having count (Email)>1;
```

将邮箱分组到一起，然后进行查找重复的

### 项目二

创建表

```mysql
CREATE TABLE World (
name VARCHAR(50) NOT NULL,
continent VARCHAR(50) NOT NULL,
area INT NOT NULL,
population INT NOT NULL,
gdp INT NOT NULL
);
```

插入数据

```mysql
INSERT INTO World
  VALUES('Afghanistan','Asia',652230,25500100,20343000);
INSERT INTO World 
  VALUES('Albania','Europe',28748,2831741,12960000);
INSERT INTO World 
  VALUES('Algeria','Africa',2381741,37100000,188681000);
INSERT INTO World
  VALUES('Andorra','Europe',468,78115,3712000);
INSERT INTO World
  VALUES('Angola','Africa',1246700,20609294,100990000);
```

查找

```
SELECT country,populaiton,area  

FROM World

where(population>25000000 and gdp>20000000)

or area>3000000;
```

