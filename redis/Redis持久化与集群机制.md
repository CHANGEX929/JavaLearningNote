## MySQL与Redis数据一致性问题

- 手动刷新缓存。
- 在对数据进行修改操作时，同时操作数据库。
  - 先删除redis数据，再更新数据库
  - 先更新数据库，再更新redis
- 采用mq订阅mysql binlog日志文件增量同步到Redis中，保证数据最终一致（alibaba开源框架canal）。



## Redis持久化机制

- Redis的持久化机制有两种：AOF、RDB（默认），RDB采用定时持久化机制，但是服务器异常宕机后数据可能会丢失；AOF是基于数据日志操作实现的持久化，操作频率高，可以保证数据不丢失，但是增加服务的压力，同时会降低Redis的效率。

### RDB数据同步实现原理

![RDB数据同步方](redis/photo/RDB数据同步方案.png)



