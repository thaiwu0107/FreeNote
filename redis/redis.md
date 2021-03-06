# Redis設定
## Redis Cluster
### 開啟Redis
    redis-server /usr/local/etc/redis/cluster/7001/7001.conf;
    redis-server /usr/local/etc/redis/cluster/7000/7000.conf;

### 使用Redis
    redis-cli -c -h 192.168.10.106 -p 6379

### 創建群集
    ./redis-trib.rb create --replicas 1 192.168.10.103:6379 192.168.10.104:7002 192.168.10.105:6379 192.168.10.106:6379

### 修復節點
    ./redis-trib.rb fix 192.168.10.106:6379

### 查詢所有node資訊
    cluster nodes

### 刪除這個節點所有資料
    Flushall

### redis設定
    port REDIS_PORT
    timeout 20
    tcp-keepalive 300
    save 60 1
    save 30 30000
    maxclients 180000
    appendonly no
    repl-diskless-sync no
    repl-ping-replica-period 40
    repl-timeout 80
    repl-disable-tcp-nodelay yes
    repl-diskless-sync-delay 0
    repl-ping-slave-period 40
    cluster-enabled yes
    cluster-config-file nodes.conf
    cluster-node-timeout 30000
    cluster-slave-validity-factor 20
    cluster-replica-validity-factor 100
    client-output-buffer-limit normal 0 0 0
    client-output-buffer-limit slave 0 0 0
    client-output-buffer-limit pubsub 0 0 0

## Docker + Redis Cluster
### 創建群集
    docker run --rm -it inem0o/redis-trib create --replicas 1 192.168.10.210:7001 192.168.10.210:7002 192.168.10.210:7003 192.168.10.210:7004 192.168.10.210:7005 192.168.10.210:7006 192.168.10.210:7007 192.168.10.210:7008 192.168.10.210:7009  192.168.10.166:7001 192.168.10.166:7002 192.168.10.166:7003 192.168.10.166:7004 192.168.10.166:7005 192.168.10.166:7006 192.168.10.166:7007 192.168.10.166:7008 192.168.10.166:7009 192.168.10.180:7001 192.168.10.180:7002 192.168.10.180:7003 192.168.10.180:7004 192.168.10.180:7005 192.168.10.180:7006 192.168.10.180:7007 192.168.10.180:7008 192.168.10.180:7009