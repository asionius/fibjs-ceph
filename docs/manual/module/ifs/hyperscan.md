# 模块 hyperscan
快速检索模块，提供正则急速匹配搜索方案

引用方法:
```
var hs = require('hyperscan');
var reg = hs.compile('hello.*world', 'gims');
var res = reg.scan('hello world');
console.log(res);
```
或者
```
var hs = require('hyperscan');
var reg = hs.compile(['hello.*world', '^中文$''], ['gims', '']);
var res = reg.scan('hello world');
console.log(res);
```

## 静态函数
        
### compile
**创建一个 hyperscan 正则对象，参见 [HsRegExp](../../object/ifs/HsRegExp.md)**

```JavaScript
static HsRegExp hyperscan.compile(String pattern,
    String flag = "");
```

调用参数:
* pattern: String, 正则字符串
* flag: String, 正则匹配模式 支持"i"(不区分大小写)、"m"(多行匹配)、"g"(全文匹配)、"s"('.'可以匹配换行符'\n')、"8"(utf-8编码)、"W"(unicode编码)

返回结果:
* [HsRegExp](../../object/ifs/HsRegExp.md), hyperscan正则对象

--------------------------
**使用数组创建一个 hyperscan 正则对象，用于并行匹配正则，参见 [HsRegExp](../../object/ifs/HsRegExp.md)**

```JavaScript
static HsRegExp hyperscan.compile(Array patterns,
    Array flags = []);
```

调用参数:
* patterns: Array, 正则字符串数组
* flags: Array, 正则匹配模式数组 支持"i"(不区分大小写)、"m"(多行匹配)、"g"(全文匹配)、"s"('.'可以匹配换行符'\n')、"8"(utf-8编码)、"W"(unicode编码)

返回结果:
* [HsRegExp](../../object/ifs/HsRegExp.md), hyperscan正则对象

