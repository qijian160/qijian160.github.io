---
title: 2019年10月8日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---
## redis       
        String（字符串）
        string 是 redis 最基本的类型，你可以理解成与 Memcached 一模一样的类型，一个 key 对应一个 value。
        string 类型是二进制安全的。意思是 redis 的 string 可以包含任何数据。比如jpg图片或者序列化的对象。
        string 类型是 Redis 最基本的数据类型，string 类型的值最大能存储 512MB。
        Hash（哈希）用来存java对象的
        hset 鍵名  字段名  值
        相当于redis中的对象一样,
        hget 键名 字段名
        获取键下的某个字段的值
        同时定义多个值哈希表的key中
        hmset 键名 字段名1 值1 字段名2 值2
        同时获取多个值哈希表的key中
        hmget 键名 字段名1 字段名2

        hgetall命令:可以查看hash表中某个键名下的所有字段名和字段值
        hgetall 键名
        hdel命令:删除某个键下的字段
        hdel 键 字段名1 字段名2
        hkeys命令:返回某个hash表的键下的所有字段
        hkeys 键名
        hvals命令:返回某个hash表的键下的所有字段值
        hvals 键名
        hexists命令:返回的键下的字段名是否存在
        hexists 键 字段名

        none类型:表示键不存在
        list类型:表示列表
        lpush与rpush命令:将一个或多个值添加到列表当中,l是从左添加,r是从右添加
        lpush 表名 a b c
        查看表内容的时候显示的顺序是c b a
        lrange命令:是从左开始截取元素
        lrange 键 开始值 到第几个元素结束的值
        如果开始值和结束值是负数则就会是从尾部开始取值
        如果想查看全部值则用 lrange 键 0 -1
        lindex命令:指定下标取值
        lindex 键名 下表值
        llen命令:返回键中的所有值的长度
        llen 键名
        lrem命令:删除对应指定数量与命令中的值对应的值
        lrem 键名 删除数量 要删除的值
        这里删除数量这是为正数时候就会在首部向下删除,如果负数则会从尾部想上删除
        lrem 键名 0 要删除的值       代表删除列表中所有和该值对应的值
        lset命令:指定下标设置值(下标必须是已存在值的下标)
        lset 键名 下标值  值
        linsert命令:将数据插入到指定的参考值之后或之前
        linsert 键名 before或after 参考值 值
        参考值就是列表当中现有的值,
        before表示在参考值之前
        after表示在参考值之后
        set类型:集合
        集合中的成员是唯一的并且是无序的
        sadd命令:将一个或多个元素添加到key当中,如果已经存在的元素将被忽略
        sadd 键名 值1 值2
        在用smembers命令查看值的时候是值2在前  值2  值1的顺序存储的
        smembers命令:查看一个集合当中所有的值
        smembers 键名
        sismember命令:判断元素是否是集合key的成员
        是集合成员返回1 不是集合成员返回0
        sismember 键  值
        scard命令:获取集合中的元素数量
        scard 键
        srem命令:删除集合key中一个或多个元素,不存在的元素将被忽略
        srem 键 元素1 元素2
        srandmember命令:在集合中随机抽取一个或多个元素
        srandmember 键  取值个数
        取值个数为正数代表取出的值是唯一的
        取值个数为负数代表取出的值可以重复
        spop命令:随机在集合中删除一个
        spop 键
        sinter命令:取两个集合的交集就是看两个集合有没有相同的元素
        sinter 集合1 集合2
        sdiff命令:取两个集合的差集就是两个集合不一样的地方

        zset类型:有序集
        zset的每个元素都会关联一个分数,(分数可以重复),redis通过分数来为集合中的成员从小到大排序
        zadd命令:添加一个或多个元素到有序集合中
        zadd key 分数 值1 分数 值2
        例子:zadd 表名 1 a 2 b 3 c 4 d
        zrange命令:显示一个或多个有序集合中的元素
        zrange key 开始值 结束值
        这里只显示元素而不显示分数,如果想让其显示分数则需要使用withscores
        zrevrange命令:显示key中指定区域内的成员,其中成员的位置按scores降序排序
        zrem命令:删除一个或多个元素
        zrem key 元素1 元素2
        zcard命令:返回key中的元素个数
        zcard key
        zrangebyscore命令:获取有序集合中分数的一个区间的所有值,进行递增排序
        zrangebyscore key min max [withscores] [limit]
        例子:获取分数2000到4000的数据
        zrangebyscore key 2000 4000 withscores
        例子:获取分数2000到4000的数据但是不包括4000
        zrangebyscore key 2000 (4000 withscores
        例子:获取工资小于5000的
        zrangebyscore key -inf 5000 withscores
        例子:获取工资大于4000的
        zrangebyscore key 4000 +inf withscores
        例子:获取工资大于4000的第一条元素
        zrangebyscore key 4000 +inf withscore limit 0 1
        zrevrangebyscore命令:获取有序集合中分数的一个区间的所有值,进行递减排序
        zrevrangebyscore key min max [withscores] [limit]
        例子:获取分数2000到4000的数据
        zrevrangebyscore key 2000 4000 withscores
        例子:获取分数2000到4000的数据但是不包括4000
        zrevrangebyscore key 2000 (4000 withscores
        例子:获取工资小于5000的
        zrevrangebyscore key -inf 5000 withscores
        例子:获取工资大于4000的
        zrevrangebyscore key 4000 +inf withscores
        例子:获取工资大于4000的第一条元素
        zrevrangebyscore key 4000 +inf withscore limit 0 1
        zcount命令:获取一个区间内的元素数量
        zcount key 开始区间 结束区间