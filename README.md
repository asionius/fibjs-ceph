# fibjs-ceph
This repository store fibjs-for-ceph binary file and document. It offer rados object store api and rbd block device manage api. Refer to document for detail.

This project use all rados & rbd async io apis to write and read with ceph osds, it will not block the thread which act as a powerful engine to dispatch fibers which actually carry on the logical calculation. Thus, you can write high performance http server using fibjs natural high concurrency feature, to offer radosgw with high availability.

# download
```
git clone https://github.com/asionius/fibjs-ceph.git
```
# install
```
cd fibjs-ceph
chmod +x fibjs-for-ceph-linux-x64-v0.19
cp ./fibjs-for-ceph-linux-x64-v0.19 /usr/local/bin/fibjs
```
# test
```
fibjs rados_test.js
```
# src code

[https://github.com/asionius/fibjs/tree/librbd](https://github.com/asionius/fibjs/tree/librbd)

# example
- rados
```
 var rados = require('rados');
 var cluster = new rados.Rados('clusterName', 'userName', '/path/to/myceph.conf');
 cluster.connect();
 var io = cluster.createIoCtx('poolName');
 var s = io.open('key');
 s.write('hello key');
 s.rewind();
 console.log(s.readAll().toString());
```
- rbd
```
 var rados = require('rados');
 var cluster = new rados.Rados('clusterName', 'userName', '/path/to/myceph.conf');
 cluster.connect();
 var io = cluster.createIoCtx('poolName');
 var img = io.openImage('imgName');
 img.write('hello image');
 img.rewind();
 console.log(img.read(11).toString());
```

# document
- refer to docs/module/ifs/rados.md