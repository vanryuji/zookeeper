# Overview
zookeeper cluster 구축<br>
구조는 아래와 같음<br>
![alt text](architecture.png)

# Environments
* openjdk 11
* zookeeper 3.4

# Cluster setup
### Configuration
```shell
# server1, server2, server3 모두 적용
# 자세한 configure 내용은 https://zookeeper.apache.org/doc/r3.4.14/zookeeperAdmin.html#sc_configuration 참조

# conf/zoo.cfg file
tickTime=2000
initLimit=10
syncLimit=5
dataDir=/tmp/zookeeper
clientPort=2181
server.1=server1:2888:3888
server.2=server2:2888:3888
server.3=server3:2888:3888
```

### myid
```shell
# server1
echo 1 > /tmp/zookeeper/myid

# server2
echo 2 > /tmp/zookeeper/myid

# server3
echo 3 > /tmp/zookeeper/myid
```

### Start
```shell
# server1, server2, server3 모두 적용

./bin/zkServer.sh start-foreground conf/zoo.cfg
```




# Reference
* https://zookeeper.apache.org/doc/r3.4.14/
