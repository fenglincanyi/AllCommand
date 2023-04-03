跑SQL技巧
* 合并多行： UNION / UNION ALL :  UNION会合并重复， UNION ALL不会, 可以用于合并多行

* 去掉不用的行：反选
```sql
SELECT
    t0.*
    ,t1.`(os|ab_info)?+.+` -- 去掉os和ab_info字段
    ,t2.`(os)?+.+`  -- 去掉os字段
    from table_a
```
