# 模块 rados
rados模块

使用方法：
```
var rados = require('rados');
```

## 静态函数
        
### create
**创建一个rados cluster, 用于连接rados服务器集群 参见 [RadosCluster](../../object/ifs/RadosCluster.md)**

```JavaScript
static RadosCluster rados.create(String clusterName,
    String userName,
    String confPath) async;
```

调用参数:
* clusterName: String, 指定要连接的集群的名称
* userName: String, 指定连接者的用户名
* confPath: String, 指定配置文件路径

