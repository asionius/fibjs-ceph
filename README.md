# fibjs-rados_bin_and_doc
Fibjs for librados, this repository offer fibjs executable binary file via a .sh format file. You can use fibjs to act as a librados client connecting to ceph rados cluster. 

# download
```
	git clone https://github.com/asionius/fibjs-rados_bin_and_doc.git
```
# install
```
	cd fibjs-rados_bin_and_doc
	sh installer-linux-20170614
```
# test
```
	fibjs rados_test.js
```
# example
```
 var rados = require('rados');
 var cluster = new rados.Rados('clusterName', 'userName', '/path/to/myceph.conf');
 cluster.connect();
 var io = cluster.createIoCtx('poolName');
 var s = io.open('key');
 s.write('hello key');
 console.log(s.readAll().toString());
```
# document
- cd html
- 双击index.html
