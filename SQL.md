## 跑SQL技巧

* 条件查询 & 分类统计
```sql
SELECT  STR_TO_MAP(abc)
        ,COUNT(DISTINCT did)
FROM    table1
WHERE   ds = '20230402'
AND     info = 'xxxx'
GROUP BY STR_TO_MAP(abc)
```
* case when使用
```sql
在使用CASE WHEN语句时，是否需要结合GROUP BY子句取决于你的查询需求。
如果你想对查询结果进行分组，并在每个组中应用不同的条件逻辑，那么你需要结合GROUP BY子句和CASE WHEN语句来实现。
以下是一个示例，展示了如何在GROUP BY子句中使用CASE WHEN语句：
SELECT category, 
       SUM(CASE WHEN price > 100 THEN 1 ELSE 0 END) AS high_price_count,
       SUM(CASE WHEN price <= 100 THEN 1 ELSE 0 END) AS low_price_count
FROM products
GROUP BY category;
```
* IF() 和 DISTINCT 结合 巧妙用法，快速分类计数
```sql
SELECT  COUNT(DISTINCT IF((arg = 'cccc'),user_id,NULL)) AS expo_uv
        ,COUNT(DISTINCT 
              IF((arg = 'aaaa'),user_id,NULL)
        ) AS click_uv
FROM    table_a
WHERE   xxxxxxxxxxx
```

* 条件查询，count统计
```sql
SELECT COUNT(DISTINCT did, IF(a=b,TRUE, NULL)) FROM table1
```
* 合并多行： UNION / UNION ALL :  UNION会合并重复， UNION ALL不会, 可以用于合并多行
* 去掉不用的行：反选
```sql
SELECT
    t0.*
    ,t1.`(os|ab_info)?+.+` -- 去掉os和ab_info字段
    ,t2.`(os)?+.+`  -- 去掉os字段
    FROM table_a
```


## SQL函数
* MAX(Column)  多个取任意一个
* COALESCE(c1, c2)  多个字段中，取不为空的，如果2个都不为空，则取第一个，COALESCE(t1.column,t2.column) AS column_merge
* 去极值：PERCENT_RANK() OVER (partition by bucket_info ORDER BY cm_pay_amt DESC ) as myrank
```sql
SELECT
    bucket_info,
    SUM(pay_amt) payAll,
    COUNT(
        DISTINCT order_id,
        IF(myrank > 0.001, TRUE, NULL)
    ) ordernum2,
    COUNT(
        DISTINCT uesr_id,
        IF(myrank > 0.001, TRUE, NULL)
    ) buyuv2,
    SUM(IF(myrank > 0.001, pay_amt, 0)) payall_2
FROM
    (
        select
            bucket_info,
            uesr_id,
            order_id,
            pay_amt,
            PERCENT_RANK() OVER (
                partition by bucket_info
                ORDER BY
                    pay_amt DESC
            ) as myrank
        FROM
            table_1
    )
```
