# 对象 SQLite
sqlite 数据库连接对象

使用 [db.open](../../module/ifs/db.md#open) 或 [db.openSQLite](../../module/ifs/db.md#openSQLite) 创建，创建方式：

```JavaScript
var slite = db.openSQLite("sqlite:/path/to/db");
```

## 继承关系
```dot
digraph {
    node [fontname="Helvetica,sans-Serif", fontsize=10, shape="record", style="filled", fillcolor="white"];

    object [tooltip="object", URL="object.md", label="{object|toString()\ltoJSON()\l}"];
    DbConnection [tooltip="DbConnection", URL="DbConnection.md", label="{DbConnection|type\l|close()\lbegin()\lcommit()\lrollback()\ltrans()\lexecute()\lformat()\l}"];
    SQLite [tooltip="SQLite", fillcolor="lightgray", id="me", label="{SQLite|fileName\ltimeout\l|backup()\l}"];

    object -> DbConnection [dir=back];
    DbConnection -> SQLite [dir=back];
}
```

## 成员属性
        
### fileName
**String, 当前数据库文件名**

```JavaScript
readonly String SQLite.fileName;
```

--------------------------
### timeout
**Integer, 查询和设置数据库超时时间，以毫秒为单位**

```JavaScript
Integer SQLite.timeout;
```

--------------------------
### type
**String, 查询当前连接数据库类型**

```JavaScript
readonly String SQLite.type;
```

## 成员函数
        
### backup
**备份当前数据库到新文件**

```JavaScript
SQLite.backup(String fileName) async;
```

调用参数:
* fileName: String, 指定备份的数据库文件名

--------------------------
### close
**关闭当前数据库连接**

```JavaScript
SQLite.close() async;
```

--------------------------
### begin
**在当前数据库连接上启动一个事务**

```JavaScript
SQLite.begin() async;
```

--------------------------
### commit
**提交当前数据库连接上的事务**

```JavaScript
SQLite.commit() async;
```

--------------------------
### rollback
**回滚当前数据库连接上的事务**

```JavaScript
SQLite.rollback() async;
```

--------------------------
### trans
**进入事务执行一个函数，并根据函数执行情况提交或者回滚**

```JavaScript
Boolean SQLite.trans(Function func);
```

调用参数:
* func: Function, 以事务方式执行的函数

返回结果:
* Boolean, 返回事务是否提交，正常 commit 时返回 true, rollback 时返回 false，如果事务出错则抛出错误

func 执行有三种结果：
* 函数正常返回，包括运行结束和主动 return，此时事务将自动提交
* 函数返回 false，此时事务将回滚
* 函数运行错误，事务自动回滚

--------------------------
### execute
**执行一个 sql 命令，并返回执行结果，可根据参数格式化字符串**

```JavaScript
NArray SQLite.execute(String sql,
    ...args) async;
```

调用参数:
* sql: String, 格式化字符串，可选参数用 ? 指定。例如：'SELECT FROM TEST WHERE [id]=?'
* args: ..., 可选参数列表

返回结果:
* NArray, 返回包含结果记录的数组，如果请求是 UPDATE 或者 INSERT，返回结果还会包含 affected 和 insertId，mssql 不支持 insertId。

--------------------------
### format
**格式化一个 sql 命令，并返回格式化结果**

```JavaScript
String SQLite.format(String sql,
    ...args);
```

调用参数:
* sql: String, 格式化字符串，可选参数用 ? 指定。例如：'SELECT FROM TEST WHERE [id]=?'
* args: ..., 可选参数列表

返回结果:
* String, 返回格式化之后的 sql 命令

--------------------------
### toString
**返回对象的字符串表示，一般返回 "[Native Object]"，对象可以根据自己的特性重新实现**

```JavaScript
String SQLite.toString();
```

返回结果:
* String, 返回对象的字符串表示

--------------------------
### toJSON
**返回对象的 JSON 格式表示，一般返回对象定义的可读属性集合**

```JavaScript
Value SQLite.toJSON(String key = "");
```

调用参数:
* key: String, 未使用

返回结果:
* Value, 返回包含可 JSON 序列化的值

