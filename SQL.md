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
