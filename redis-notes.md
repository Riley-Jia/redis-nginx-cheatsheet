# Redis Basic Command Cheat Sheet
# Redis 基本命令笔记

---

## 1️⃣ Start Redis Container / 启动 Redis 容器

### Run Redis normally (default port 6379)、

```bash
docker run -d --name redis-server -p 6379:6379 redis
```

### Run Redis with password

```bash
docker run -d --name redis-server -p 6379:6379 redis redis-server --requirepass <your-password>
```

## 2️⃣ Enter Redis Container

```bash
docker exec -it redis-server redis-cli
```

## 3️⃣ Stop and Remove Old Container

```bash
docker stop redis-server
docker rm redis-server
```

## 4️⃣ Password Authentication (AUTH)

```bash
# 连接后提示如下错误
(error) NOAUTH Authentication required.

# 使用 auth 命令认证
127.0.0.1:6379> auth <your-password>
```

## 5️⃣ Redis Commands (Strings + Hash + Common)

```bash
set name "Riley"
get name

# ===== Hash Commands =====
HSET <key> <field> <value>                       # 设置字段 / Set a field
HMSET <key> <field1> <value1> <field2> <value2>  # 批量设置字段 / Set multiple fields
HGET <key> <field>                               # 获取字段 / Get a field
HMGET <key> <field1> <field2>                    # 获取多个字段 / Get multiple fields
HGETALL <key>                                    # 获取所有字段和值 / Get all fields and values
HKEYS <key>                                      # 获取所有字段名 / Get all field names
HVALS <key>                                      # 获取所有字段值 / Get all field values
HDEL <key> <field>                               # 删除字段 / Delete a field
HEXISTS <key> <field>                            # 判断字段是否存在 / Check if a field exists

# ===== Common Commands =====
SELECT 0                                         # 切换到数据库 0 / Select database 0
KEYS *                                           # 查看所有键（开发环境使用）/ List all keys (dev only)
SCAN 0 MATCH * COUNT 10                          # 使用迭代方式遍历键 / Safe way to iterate keys
EXISTS <key>                                     # 判断键是否存在 / Check if key exists
TYPE <key>                                       # 查看键类型 / Check type of key
DEL <key>                                        # 删除键 / Delete a key
EXPIRE <key> <seconds>                           # 设置键过期时间 / Set key TTL
TTL <key>                                        # 查看剩余生存时间 / Get remaining TTL
DBSIZE                                           # 当前数据库键数量 / Number of keys in current DB
FLUSHDB                                          # 清空当前数据库 / Clear current DB
FLUSHALL                                         # 清空所有数据库 / Clear all DBs

```

## 6️⃣ Placeholder for Other Data Types

```bash
# ===== List (列表) =====
LPUSH <key> <value1> <value2>       # 从左推入
RPUSH <key> <value1> <value2>       # 从右推入
LPOP <key>                          # 从左弹出
LRANGE <key> 0 -1                   # 获取所有元素

# ===== Set (集合) =====
SADD <key> <member1> <member2>      # 添加元素
SMEMBERS <key>                      # 获取所有成员
SPOP <key>                          # 弹出随机元素

# ===== Sorted Set (有序集合) =====
ZADD <key> <score> <member>         # 添加元素及分数
ZRANGE <key> 0 -1                   # 按分数升序返回元素
ZSCORE <key> <member>               # 获取元素分数
```

---

_Last updated: June 12, 2025_  
_Compiled by: Riley_