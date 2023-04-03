## 跑SQL技巧

* 合并多行： UNION / UNION ALL :  UNION会合并重复， UNION ALL不会, 可以用于合并多行

* 去掉不用的行：反选
```sql
SELECT
    t0.*
    ,t1.`(os|ab_info)?+.+` -- 去掉os和ab_info字段
    ,t2.`(os)?+.+`  -- 去掉os字段
    from table_a
```


## SQL函数
* MAX(Column)  多个取任意一个
* COALESCE(c1, c2)  多个字段中，取不为空的，如果2个都不为空，则取第一个，COALESCE(t1.column,t2.column) AS column_merge
