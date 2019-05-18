### 项目七

#### 创建表

```mysql
DROP TABLE IF EXISTS `employee`;
CREATE TABLE `employee` (
  `Id` int(11) NOT NULL,
  `Name` varchar(255) NOT NULL,
  `Salary` int(11) NOT NULL,
  `DepartmentId` int(11) NOT NULL,
  PRIMARY KEY (`Id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

DROP TABLE IF EXISTS `department`;
CREATE TABLE `department` (
  `Id` int(11) NOT NULL,
  `Name` varchar(255) NOT NULL,
    PRIMARY KEY (`Id`)
)ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

插入数据

```mysql
INSERT INTO Employee VALUE('1','Joe','70000','1');
INSERT INTO Employee VALUE('2','Henry','80000','2');
INSERT INTO Employee VALUE('3','Sam','60000','2');
INSERT INTO Employee VALUE('4','Max','90000','1');

INSERT INTO Department VALUE('1','IT');
INSERT INTO Department VALUE('2','Sales');
```

查找

```mysql
SELECT
      d.Name AS Department,
      e.Name AS Employee,
      e.Salary AS Salary
      FROM
      Employee AS e, 
      Department AS d  
      WHERE e.DepartmentId = d.Id AND
      e.Salary >= (SELECT MAX(Salary) FROM Employee WHERE DepartmentId=d.Id)  
ORDER BY Salary DESC;
```



### 项目八

创建表

```mysql
CREATE TABLE seat(
id INT ,
student VARCHAR(20)
)
#插入数据
INSERT INTO seat VALUE('1','Abbot');
INSERT INTO seat VALUE('2','Doris');
INSERT INTO seat VALUE('3','Emerson');
INSERT INTO seat VALUE('4','Green');
INSERT INTO seat VALUE('5','Jeames');
```

```mysql
SELECT *
FROM (
--          遇到偶数往上移一个位置
            SELECT id-1 AS id,student
            FROM seat
            WHERE id%2=0
 
            UNION
--          遇到奇数往下移一个位置
 
            SELECT id+1 AS id,student
            FROM seat
            WHERE id%2=1 AND (id+1)<=(SELECT COUNT(*) FROM seat)
 
            UNION
--          处理最后一个位置，这里只考虑奇数情况，保持不变（偶数已经在第一步里处理了）
            SELECT id AS id,student
            FROM seat
            WHERE id%2=1 AND(id+1)>(SELECT COUNT(*) FROM seat)
            ) AS c1
ORDER BY id ASC;
```

### 项目九

```mysql
CREATE TABLE scores(
ID INT,
Score FLOAT);

INSERT INTO scores VALUE('1','3.50');
INSERT INTO scores VALUE('2','3.65');
INSERT INTO scores VALUE('3','4.00');
INSERT INTO scores VALUE('4','3.85');
INSERT INTO scores VALUE('5','4.00');
INSERT INTO scores VALUE('6','3.65');

SELECT score,(SELECT COUNT(DISTINCT score)
                                FROM scores
                                WHERE score>=s.score) AS ran_k
FROM scores AS  s
ORDER BY score DESC;
```