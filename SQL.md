# SQL
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