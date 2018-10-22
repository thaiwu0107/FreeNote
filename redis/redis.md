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
    cluster-enabled yes
    cluster-config-file nodes.conf
    cluster-node-timeout 5000
    appendonly yes
    protected-mode no
    bind 0.0.0.0
    notify-keyspace-events Ex

## Docker + Redis Cluster
### 創建群集
    docker run --rm -it inem0o/redis-trib create --replicas 1 192.168.10.210:7001 192.168.10.210:7002 192.168.10.210:7003 192.168.10.210:7004 192.168.10.210:7005 192.168.10.210:7006 192.168.10.210:7007 192.168.10.210:7008 192.168.10.210:7009 192.168.10.210:7011 192.168.10.210:7012 192.168.10.210:7013
## Single Redis