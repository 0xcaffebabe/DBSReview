# 初级SQL
## SQL查询语言概览
- 数据定义语言（DDL）
- 数据操纵语言（DML）
- 完整性
- 视图定义
- 事务控制
- 嵌入式SQL和动态SQL
- 授权
## SQL数据定义
### 基本类型
- char(n):固定长度的字符串（会追加空格）
- varchar(n):可变长度的字符串
- int：整数类型
- smallint：小整数类型（和机器相关）
- numeric(p,d):定点数，p位数，d位小数
- real，double，precision：浮点数与双精度浮点数，精度与机器相关
- float(n)：精度至少为n位的浮点数
### 基本模式定义
create table 命令的通用形式
```sql
CREATE TABLE r
(
    A1 D1,
    A2 D2,
    AN DN,
    <完整性约束1>,
    <完整性约束K>
);
```
示例：
```sql
CREATE TABLE department(
    dept_name VARCHAR(20),
    building VARCHAR(15),
    budget NUMERIC(12,2),
    PRIMARY KEY(dept_name)
);
```
#### 完整性约束：
- PRIMARY KEY：取值唯一
- FOREIGN KEY:外键约束
- NOT NULL :非空约束
## SQL查询的基本结构
### 单关系查询
示例：
```sql
SELECT name FROM instructor
```
- distnct 去除重复元组
- SELECT子句还可进行加减乘除运算
- WHERE子句选出满足条件的元组
### 多关系查询
示例：
```sql
SELECT name,instructor.dept_name,building
FROM instructor , department
WHERE instructor.dept_name = department.dept_name
```
典型的SQL查询语句形式：
```sql
SELECT A1,A2,A3,...,AN
FROM R1,R2,...,RN
WHERE P
```
笛卡尔积：
表1：
name|age
----|----
小明|15
小红|16
表2：
grade|school
----|----
5|中心小学
6|中心小学

两张表的笛卡尔积是：
name|age|grade|school
----|----|----|----
小明|15|5|中心小学
小红|16|6|中心小学
小明|15|6|中心小学
小红|16|5|中心小学
### 自然连接
```sql
SELECT name,instructor.dept_name,building
FROM instructor , department
WHERE instructor.dept_name = department.dept_name
```
上面那条SQL可以简化成下列形式：
```sql
SELECT name,instructor.dept_name,building
FROM instructor NATURAL JOIN department
```
### 附加的基本运算
### 更名运算
AS 关键字：可以修改列名
### 字符串运算
- upper()
- lower()
- trim()
LIKE 关键字：
- %表示匹配任何字符（包括什么都没有）
- _表示匹配一个字符
示例：
```sql
SELECT name FROM user WHERE name LIKE 'user%' 
# 查找用户名以user开头的用户
```
escape :用来标志逃逸字符
```sql
LIKE 'ab\\cd%' escape '\' #匹配所有以ab\cd开头的字符串
```
SQL1999 中提供了similar to操作，语法类似于正则表达式
### SELECT子句中的属性说明
可以用*代表所有列
### 排列元组的显示次序
ORDER BY 子句
- DESC 降序
- ASC 升序
```sql
SELECT name,age FROM student ORDER BY age DESC
# 根据学生的年龄进行降序排序
```
### WHERE 子句谓词
BETWEEN ... AND ...
```sql
money BETWEEN 9000 AND 10000
```
等价于
```sql
money >= 9000 AND money <= 10000
```
NOT BETWEEN ... AND ...
上面的取反
