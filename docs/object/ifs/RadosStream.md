# 对象 RadosStream
[rados](../../module/ifs/rados.md)流操作对象，用于读写[rados](../../module/ifs/rados.md)存储

[rados](../../module/ifs/rados.md) KV存储对象,用于对[rados](../../module/ifs/rados.md)集群kv存储进行操作，可使用 [RadosIoCtx](RadosIoCtx.md) 对象创建
```
var rados = require('rados');
var cluster = new rados.Rados('clusterName', 'userName', '/path/to/myceph.conf');
cluster.connect();
var io = cluster.createIoCtx('poolName');
var s = io.open('key');
s.write('hello key');
console.log(s.readAll().toString());
```

## 继承关系
```dot
digraph {
    node [fontname="Helvetica,sans-Serif", fontsize=10, shape="record", style="filled", fillcolor="white"];

    object [tooltip="object", URL="object.md", label="{object|dispose()\lequals()\ltoString()\ltoJSON()\l}"];
    Stream [tooltip="Stream", URL="Stream.md", label="{Stream|read()\lwrite()\lclose()\lcopyTo()\l}"];
    SeekableStream [tooltip="SeekableStream", URL="SeekableStream.md", label="{SeekableStream|seek()\ltell()\lrewind()\lsize()\lreadAll()\ltruncate()\leof()\lflush()\lstat()\l}"];
    RadosStream [tooltip="RadosStream", fillcolor="lightgray", label="{RadosStream|key\l|radosStat()\lwriteFull()\lappend()\l}"];

    object -> Stream [dir=back];
    Stream -> SeekableStream [dir=back];
    SeekableStream -> RadosStream [dir=back];
}
```

## 成员属性
        
### key
**String, 查询当前key**

```JavaScript
readonly String RadosStream.key;
```

## 成员函数
        
### radosStat
**返回kv对象的状态**

```JavaScript
RadosStat RadosStream.radosStat() async;
```

返回结果:
* [RadosStat](RadosStat.md), kv对象的状态仅支持kv对象的大小和最后修改时间

--------------------------
### writeFull
**全部重新写入，如果该流里有内容，则被擦除重新写入**

```JavaScript
RadosStream.writeFull(Buffer data) async;
```

调用参数:
* data: [Buffer](Buffer.md), 将要被写入的数据

--------------------------
### append
**在原数据之后追加数据**

```JavaScript
RadosStream.append(Buffer data) async;
```

调用参数:
* data: [Buffer](Buffer.md), 将要被写入的数据

--------------------------
### seek
**移动文件当前操作位置**

```JavaScript
RadosStream.seek(Long offset,
    Integer whence);
```

调用参数:
* offset: Long, 指定新的位置
* whence: Integer, 指定位置基准，允许的值为：SEEK_SET, SEEK_CUR, SEEK_END

--------------------------
### tell
**查询流当前位置**

```JavaScript
Long RadosStream.tell();
```

返回结果:
* Long, 返回流当前位置

--------------------------
### rewind
**移动当前位置到流开头**

```JavaScript
RadosStream.rewind();
```

--------------------------
### size
**查询流尺寸**

```JavaScript
Long RadosStream.size();
```

返回结果:
* Long, 返回流尺寸

--------------------------
### readAll
**从流内读取剩余的全部数据**

```JavaScript
Buffer RadosStream.readAll() async;
```

返回结果:
* [Buffer](Buffer.md), 返回从流内读取的数据，若无数据可读，或者连接中断，则返回 null

--------------------------
### truncate
**修改文件尺寸，如果新尺寸小于原尺寸，则文件被截断**

```JavaScript
RadosStream.truncate(Long bytes) async;
```

调用参数:
* bytes: Long, 新的文件尺寸

--------------------------
### eof
**查询文件是否到结尾**

```JavaScript
Boolean RadosStream.eof();
```

返回结果:
* Boolean, 返回 True 表示结尾

--------------------------
### flush
**将文件缓冲区内容写入物理设备**

```JavaScript
RadosStream.flush() async;
```

--------------------------
### stat
**查询当前文件的基础信息**

```JavaScript
Stat RadosStream.stat() async;
```

返回结果:
* [Stat](Stat.md), 返回 [Stat](Stat.md) 对象描述文件信息

--------------------------
### read
**从流内读取指定大小的数据**

```JavaScript
Buffer RadosStream.read(Integer bytes = -1) async;
```

调用参数:
* bytes: Integer, 指定要读取的数据量，缺省为读取随机大小的数据块，读出的数据尺寸取决于设备

返回结果:
* [Buffer](Buffer.md), 返回从流内读取的数据，若无数据可读，或者连接中断，则返回 null

--------------------------
### write
**将给定的数据写入流**

```JavaScript
RadosStream.write(Buffer data) async;
```

调用参数:
* data: [Buffer](Buffer.md), 给定要写入的数据

--------------------------
### close
**关闭当前流对象**

```JavaScript
RadosStream.close() async;
```

--------------------------
### copyTo
**复制流数据到目标流中**

```JavaScript
Long RadosStream.copyTo(Stream stm,
    Long bytes = -1) async;
```

调用参数:
* stm: [Stream](Stream.md), 目标流对象
* bytes: Long, 复制的字节数

返回结果:
* Long, 返回复制的字节数

--------------------------
### dispose
**强制回收对象，调用此方法后，对象资源将立即释放**

```JavaScript
RadosStream.dispose();
```

--------------------------
### equals
**比较当前对象与给定的对象是否相等**

```JavaScript
Boolean RadosStream.equals(object expected);
```

调用参数:
* expected: [object](object.md), 制定比较的目标对象

返回结果:
* Boolean, 返回对象比较的结果

--------------------------
### toString
**返回对象的字符串表示，一般返回 "[Native Object]"，对象可以根据自己的特性重新实现**

```JavaScript
String RadosStream.toString();
```

返回结果:
* String, 返回对象的字符串表示

--------------------------
### toJSON
**返回对象的 JSON 格式表示，一般返回对象定义的可读属性集合**

```JavaScript
Value RadosStream.toJSON(String key = "");
```

调用参数:
* key: String, 未使用

返回结果:
* Value, 返回包含可 JSON 序列化的值

