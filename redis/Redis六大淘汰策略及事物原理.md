## 淘汰策略

Redis数据存放在内存内，内存有可能会被使用完，为了防止内存被使用完，Redis提供了淘汰策略，当使用内存达到设置的阈值（maxmemory）时，则会触发淘汰策略（maxmemory-policy）。

- noeviction：当内存使用达到阈值的时候，所有引起申请内存的命令会报错
- allkeys-lru：在主键空间中，优先移除最近未使用的key
- volatile-lru：在设置了过期时间的主键空间中，优先移除最近未使用的key
- allkeys-random：在主键空间中，随机移除某个key
- volatile-random：在设置了过期时间的主键空间中，随机移除某个key
- volatile-ttl：在设置了过期时间的主键空间中，具有更早过期时间的key优先移除

## key失效回调机制

当key失效时，Redis可以执行客户端回调监听的方法。需要在Redis中配置notify-keyspace-events “Ex”



## 事务

Redis提供了事务机制，通过Multi、watch、exec、discard命令可以使用事务。

- Multi 开启事务
- Exec提交事务
- Watch 可以监听一个或者多个key，再提交事务之前是否有发生变化，如果发生了变化，就不会提交事务，没有发生变化才可以提交事务（乐观锁）
- discard取消提交事务

