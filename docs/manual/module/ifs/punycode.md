# 模块 punycode
punycode 国际化域名转换模块

Punycode 是由 RFC 3492 定义的主要用于国际化域名的字符编码方案。因为 URL 中主机名限制只能是 ASCII 字符，包括非 ASCII 字符的主机名必须使用 punycode 算法转化为ASCII。

使用方法：

```JavaScript
var punycode = require('punycode');
```

## 静态函数
        
### encode
**将一个 Unicode 字符串转化为等价的只含有 ASCII 字符的 Punycode 字符串**

```JavaScript
static String punycode.encode(String domain);
```

调用参数:
* domain: String, 给定Unicode 字符串

返回结果:
* String, 返回编码后的只含有 ASCII 字符的 Punycode 字符串

--------------------------
### decode
**将一个 Punycode 字符串转化为等价的 Unicode 字符串**

```JavaScript
static String punycode.decode(String domain);
```

调用参数:
* domain: String, 给定Unicode 字符串

返回结果:
* String, 返回解码后的 Unicode 字符串

