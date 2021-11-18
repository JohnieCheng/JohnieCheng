# 日期相关sql

## 一. 根据当前时间获取三天前截止到此分秒的数据（以当前时分秒进行过滤）

```sql
select
    hco.created_date_time
from
    house_custom_order hco
where
    hco.created_date_time between (select now() - interval '3 day') and (select now())
```



## 二.根据当前时间获取到三天前凌晨的数据(不以当前的时分秒进行过滤)

```sql
select
    hco.created_date_time
from
    house_custom_order hco
where
    hco.created_date_time >= to_timestamp(SUBSTRING (to_char( now( ), 'yyyy-MM-dd hh24:MI:ss') from 1 for 10), 'yyyy-MM-dd') - interval '3 day'

```

