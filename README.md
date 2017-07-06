# fibjs-ceph
This repository store fibjs-for-ceph binary file and document. It offer rados object store api and rbd block device manage api. Refer to document for detail.

# download
```
git clone https://github.com/asionius/fibjs-ceph.git
```
# install
```
cd fibjs-ceph
sh installer-linux-20170706
```
# test
```
fibjs rados_test.js
```
# src code
```
https://github.com/asionius/fibjs/tree/librbd
```
# example
- rados
```
 var rados = require('rados');
 var cluster = new rados.Rados('clusterName', 'userName', '/path/to/myceph.conf');
 cluster.connect();
 var io = cluster.createIoCtx('poolName');
 var s = io.open('key');
 s.write('hello key');
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
- cd html
- open index.html in browser
