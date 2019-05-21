# 中级SQL
## 连接表达式
### 连接条件
JOIN...ON...
```sql
SELECT * FROM 
user JOIN user_info 
ON user.user_info = user_info.user_info_id;
# 连接两个表，查询出用户所有信息
```
上面的查询等价于:
```sql
SELECT * FROM user,user_info
WHERE user.user_info = user_info.user_info_id
```
### 外连接
- 左外连接：只保留