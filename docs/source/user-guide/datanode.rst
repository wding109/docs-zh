数据节点
========

启动数据节点
---------------------

通过执行CFS的二进制文件并用“-c”参数指定的配置文件来启动一个DATANODE进程。

.. code-block:: bash

   nohup cfs-datanode -c datanode.json &


配置参数
--------------

.. csv-table:: Properties
   :header: "关键字", "参数类型", "描述", "是否必要"

   "role", "string", "Role必须配置为“datanode”", "是"
   "port", "string", "数据节点作为服务端启动TCP监听的端口", "是"
   "localIP", "string", "数据节点作为服务端选用的IP", "否"
   "prof", "string", "数据节点提供HTTP接口所用的端口", "是"
   "logDir", "string", "调测日志存放的路径", "是"
   "logLevel", "string", "调测日志的级别。默认是error", "否"
   "raftHeartbeat", "string", "RAFT发送节点间心跳消息所用的端口", "是"
   "raftReplica", "string", "RAFT发送日志消息所用的端口", "是"
   "raftDir", "string", "RAFT调测日志存放的路径。默认在二进制文件启动路径", "否"
   "consulAddr", "string", "监控系统的地址", "否"
   "exporterPort", "string", "监控系统的端口", "否"
   "masterAddr", "string slice", "集群管理器的地址", "是"
   "rack", "string", "机架号", "否"
   "disks", "string slice", "磁盘挂载路径:最大ERROR次数:最小剩余空间", "是"

**举例：**

.. code-block:: json

   {
       "role": "datanode",
       "port": "6000",
       "prof": "6001",
       "logDir": "/export/Logs/datanode",
       "logLevel": "debug",
       "raftHeartbeat": "9095",
       "raftReplica": "9096",    
       "raftDir": "/export/Logs/datanode/raft",
       "consulAddr": "http://consul.prometheus-cfs.local",
       "exporterPort": 9512,    
       "masterAddr": [
           "10.196.30.200:80",
           "10.196.31.141:80",
           "10.196.31.173:80"
       ],
       "rack": "main",
        "disks": [
           "/data0:107374182400",
           "/data1:107374182400"
       ]
   }

