### 项目三

建表并且查找超过或等于5名学生的课

```mysql
CREATE TABLE courses(
student VARCHAR(64) NOT NULL,
class VARCHAR(20)
);

INSERT INTO courses VALUES('A','Math');
INSERT INTO courses VALUES('B','English');
INSERT INTO courses VALUES('C','Math');
INSERT INTO courses VALUES('D','Biology');
INSERT INTO courses VALUES('E','Math');
INSERT INTO courses VALUES('F','Computer');
INSERT INTO courses VALUES('G','Math');
INSERT INTO courses VALUES('H','Math');
INSERT INTO courses VALUES('I','Math');
INSERT INTO courses VALUES('A','Math');

SELECT class
FROM courses
GROUP BY class
HAVING COUNT(DISTINCT student)>=5
```

###  项目四

创建表之后交换f和m的值，要求使用一个更新查询，并且没有中间临时表

```mysql
CREATE TABLE salary(
id INT NOT NULL PRIMARY KEY,
name VARCHAR(20) NOT NULL,
sex CHAR NOT NULL,
salary int
);
INSERT INTO salary VALUES(1,'A','m',2500);
INSERT INTO salary VALUES(2,'B','f',5500);
INSERT INTO salary VALUES(3,'C','m',5000);
INSERT INTO salary VALUES(4,'D','f',1500);
INSERT INTO salary VALUES(5,'E','f',2000);
UPDATE salary
SET sex = 
CASE
WHEN sex='f' THEN 'm'
WHEN sex='m' THEN 'f'
ELSE sex
END;
SELECT * FROM salary;
```

