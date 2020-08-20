redis

redis数据库切换

```shell
#切换到第二个数据库
127.0.0.1:6379> select 1
OK

#查看数据
127.0.0.1:6379[1]> keys *
(empty array)

#存取数据
127.0.0.1:6379> set uname zhangyayun
OK
127.0.0.1:6379> get uname
"zhangyayun"
```
