
# 一、SQL 是什么（一句话懂）
SQL = 用来**从数据库里“查数据、筛选数据、汇总数据”**的语言。
你以后做城市治理、公共政策、问卷调查、面板数据，都一定会用到。



# 二、最核心万能句式（背会这 1 条就够用 80%）

SELECT 你要的列
FROM 表名
WHERE 筛选条件
GROUP BY 分组
ORDER BY 排序;



# 三、逐行超简单解释（社科版）

## 1. SELECT —— 选什么字段

SELECT city, year, policy, outcome

- 想查全部：`SELECT *`
- 想改名字：`SELECT outcome AS policy_result`

## 2. FROM —— 从哪张表里查

FROM urban_policy_data


## 3. WHERE —— 筛选条件（最常用）

WHERE year >= 2020
  AND city = 'Beijing'
  AND policy_value > 0

常用符号：
- `=` 等于
- `>` 大于
- `<` 小于
- `>=` 大于等于
- `AND` 同时满足
- `OR` 满足一个就行

## 4. GROUP BY —— 分组统计（做论文表格必备）

SELECT city, AVG(outcome) AS avg_result
FROM urban_data
GROUP BY city

常用聚合函数：
- `COUNT(*)` 计数
- `AVG( )` 平均值
- `SUM( )` 求和
- `MAX( )` 最大值
- `MIN( )` 最小值

## 5. ORDER BY —— 排序

ORDER BY year DESC, city ASC

- `DESC` 从大到小
- `ASC` 从小到大（默认）



# 四、直接能用的【政治学/城市治理示例】


## 示例1：筛选某城市、某年份政策数据

SELECT city, year, policy_type, outcome
FROM urban_policy_data
WHERE city = 'Shanghai'
  AND year BETWEEN 2018 AND 2023
ORDER BY year DESC;


## 示例2：按城市分组，看平均政策效果

SELECT city,
       COUNT(*) AS total_policies,
       AVG(outcome) AS avg_effect,
       MAX(outcome) AS max_effect
FROM urban_policy_data
GROUP BY city
ORDER BY avg_effect DESC;


## 示例3：多条件筛选 + 去重

SELECT DISTINCT policy_type
FROM urban_policy_data
WHERE year >= 2020
  AND outcome > 0.5;


---

# 五、最容易犯的 5 个错误（避坑指南）
1. 字符串必须用单引号 `'北京'`，不能双引号
2. `WHERE` 必须在 `GROUP BY` 前面
3. `SELECT` 里的聚合函数，不能放 `WHERE` 里
4. 语句最后最好加 `;`
5. 字段名不要用中文、不要用空格

---

# 六、学习路线
1. 第1阶段：`SELECT + FROM + WHERE`
2. 第2阶段：`GROUP BY + 聚合函数`
3. 第3阶段：`ORDER BY + DISTINCT`
4. 第4阶段：`JOIN` 多表连接（进阶）

