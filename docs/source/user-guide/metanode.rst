元数据节点
=================

元数据节点是由多个元数据分片(meta partition)和基于multiRaft的对应个数的raft实例组成；
每个元数据分片(meta partition)都是一个inode范围，且包含两个内存BTrees： inode BTree
和dentry BTree。

.. csv-table:: Properties
   :header: "配置项", "类型", "描述", "是否必须"
 
   "role", "字符串", "进程角色： *metanode*", "是"
   "listen", "字符串", "监听和接受请求的端口", "是"
   "prof", "字符串", "调试和管理员API接口", "是"
   "logLevel", "字符串", "日志级别，默认: *error*", "否"
   "metadataDir", "字符串", "元数据快照存储目录", "是" 
   "logDir", "字符串", "日志存储目录", "是", 
   "raftDir", "字符串", "raft wal日志目录",  "是", 
   "raftHeartbeatPort", "字符串", "raft心跳通信端口", "是" 
   "raftReplicaPort", "字符串", "raft数据传输端口", "是" 
   "consulAddr", "字符串", "prometheus注册接口", "否" 
   "exporterPort", "字符串", "prometheus获取监控数据端口", "否" 
   "masterAddrs", "字符串", "master服务地址", "是"



样例:

.. code-block:: json

   {
        "role": "metanode",
        "listen": "9021",
        "prof": "9092",
        "logLevel": "debug",
        "metadataDir": "/export/cfs/metanode_meta",
        "logDir": "/export/Logs/cfs/metanode",
        "raftDir": "/export/cfs/metanode_raft",
        "raftHeartbeatPort": "9093",
        "raftReplicaPort": "9094",
        "consulAddr": "http://consul.prometheus-cfs.local",
        "exporterPort": 9511,
        "masterAddrs": [
            "192.168.31.173:80",
            "192.168.31.141:80",
            "192.168.30.200:80"
        ]
    }
