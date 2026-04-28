## 题目需求
从 user_profile 表中查询指定字段，筛选条件：
1. university = '山东大学' 且 gpa > 3.5
2. 或 university = '复旦大学' 且 gpa > 3.8

## 解题思路
- 选取字段：device_id, gender, age, university, gpa
- 数据表：user_profile
- 多条件组合：用 AND / OR 区分并列和或关系
- 最后根据 device_id 升序排序

## SQL 代码
```sql
SELECT device_id, gender, age, university, gpa
FROM user_profile
WHERE (university = '山东大学' AND gpa > 3.5)
   OR (university = '复旦大学' AND gpa > 3.8)
ORDER BY device_id;
