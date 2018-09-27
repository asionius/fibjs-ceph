# 对象 HttpClient
[http](../../module/ifs/http.md)客户端对象

[http](../../module/ifs/http.md)客户端对象模拟浏览器环境缓存cookie，并在访问[url](../../module/ifs/url.md)的时候携带对应的cookie，不同的[http](../../module/ifs/http.md)客户端对象是相互隔离的，提供[http](../../module/ifs/http.md)的request、get、post等方法。
用法如下：

```JavaScript
var http = require('http');
var httpClient = new http.Client();
httpClient.request('GET', 'http://fibjs.org');
```

## 继承关系
```dot
digraph {
    node [fontname="Helvetica,sans-Serif", fontsize=10, shape="record", style="filled", fillcolor="white"];

    object [tooltip="object", URL="object.md", label="{object|toString()\ltoJSON()\l}"];
    HttpClient [tooltip="HttpClient", fillcolor="lightgray", id="me", label="{HttpClient|new HttpClient()\l|cookies\ltimeout\lmaxBodySize\lenableCookie\lautoRedirect\luserAgent\lpoolSize\lpoolTimeout\l|request()\lget()\lpost()\ldel()\lput()\lpatch()\l}"];

    object -> HttpClient [dir=back];
}
```

## 构造函数
        
### HttpClient
**HttpClient 构造函数，创建一个新的HttpClient对象**

```JavaScript
new HttpClient();
```

## 成员属性
        
### cookies
**NArray, 返回[http](../../module/ifs/http.md)客户端的 [HttpCookie](HttpCookie.md) 对象列表**

```JavaScript
readonly NArray HttpClient.cookies;
```

--------------------------
### timeout
**Integer, 查询和设置超时时间 单位毫秒**

```JavaScript
Integer HttpClient.timeout;
```

--------------------------
### maxBodySize
**Integer, 查询和设置 body 最大尺寸，以 MB 为单位，缺省为 -1，不限制尺寸**

```JavaScript
Integer HttpClient.maxBodySize;
```

--------------------------
### enableCookie
**Boolean, cookie功能开关，默认开启**

```JavaScript
Boolean HttpClient.enableCookie;
```

--------------------------
### autoRedirect
**Boolean, 自动redirect功能开关，默认开启**

```JavaScript
Boolean HttpClient.autoRedirect;
```

--------------------------
### userAgent
**String, 查询和设置 [http](../../module/ifs/http.md) 请求中的浏览器标识**

```JavaScript
String HttpClient.userAgent;
```

--------------------------
### poolSize
**Integer, 查询和设置 keep-alive 最大缓存连接数，缺省 128**

```JavaScript
Integer HttpClient.poolSize;
```

--------------------------
### poolTimeout
**Integer, 查询和设置 keep-alive 缓存连接超时时间，缺省 10000 ms**

```JavaScript
Integer HttpClient.poolTimeout;
```

## 成员函数
        
### request
**发送 [http](../../module/ifs/http.md) 请求到指定的流对象，并返回结果**

```JavaScript
HttpResponse HttpClient.request(Stream conn,
    HttpRequest req) async;
```

调用参数:
* conn: [Stream](Stream.md), 指定处理请求的流对象
* req: [HttpRequest](HttpRequest.md), 要发送的 [HttpRequest](HttpRequest.md) 对象

返回结果:
* [HttpResponse](HttpResponse.md), 返回服务器响应

--------------------------
**请求指定的 [url](../../module/ifs/url.md)，并返回结果**

```JavaScript
HttpResponse HttpClient.request(String method,
    String url,
    Object opts = {}) async;
```

调用参数:
* method: String, 指定 [http](../../module/ifs/http.md) 请求方法：GET, POST 等
* url: String, 指定 [url](../../module/ifs/url.md)，必须是包含主机的完整 [url](../../module/ifs/url.md)
* opts: Object, 指定附加信息

返回结果:
* [HttpResponse](HttpResponse.md), 返回服务器响应

opts 包含请求的附加选项，支持的内容如下：

```JavaScript
{
    "query": {},
    "body": SeekedStream | Buffer | String | {},
    "json": {},
    "headers": {}
}
```

其中 body，[json](../../module/ifs/json.md) 不得同时出现。缺省为 {}，不包含任何附加信息

--------------------------
### get
**用 GET 方法请求指定的 [url](../../module/ifs/url.md)，并返回结果，等同于 request("GET", ...)**

```JavaScript
HttpResponse HttpClient.get(String url,
    Object opts = {}) async;
```

调用参数:
* url: String, 指定 [url](../../module/ifs/url.md)，必须是包含主机的完整 [url](../../module/ifs/url.md)
* opts: Object, 指定附加信息

返回结果:
* [HttpResponse](HttpResponse.md), 返回服务器响应

opts 包含请求的附加选项，支持的内容如下：

```JavaScript
{
    "query": {},
    "body": SeekedStream | Buffer | String | {},
    "json": {},
    "headers": {}
}
```

其中 body，[json](../../module/ifs/json.md) 不得同时出现。缺省为 {}，不包含任何附加信息

--------------------------
### post
**用 POST 方法请求指定的 [url](../../module/ifs/url.md)，并返回结果，等同于 request("POST", ...)**

```JavaScript
HttpResponse HttpClient.post(String url,
    Object opts = {}) async;
```

调用参数:
* url: String, 指定 [url](../../module/ifs/url.md)，必须是包含主机的完整 [url](../../module/ifs/url.md)
* opts: Object, 指定附加信息

返回结果:
* [HttpResponse](HttpResponse.md), 返回服务器响应

opts 包含请求的附加选项，支持的内容如下：

```JavaScript
{
    "query": {},
    "body": SeekedStream | Buffer | String | {},
    "json": {},
    "headers": {}
}
```

其中 body，[json](../../module/ifs/json.md) 不得同时出现。缺省为 {}，不包含任何附加信息

--------------------------
### del
**用 DELETE 方法请求指定的 [url](../../module/ifs/url.md)，并返回结果，等同于 request("DELETE", ...)**

```JavaScript
HttpResponse HttpClient.del(String url,
    Object opts = {}) async;
```

调用参数:
* url: String, 指定 [url](../../module/ifs/url.md)，必须是包含主机的完整 [url](../../module/ifs/url.md)
* opts: Object, 指定附加信息

返回结果:
* [HttpResponse](HttpResponse.md), 返回服务器响应

opts 包含请求的附加选项，支持的内容如下：

```JavaScript
{
    "query": {},
    "body": SeekedStream | Buffer | String | {},
    "json": {},
    "headers": {}
}
```

其中 body，[json](../../module/ifs/json.md) 不得同时出现。缺省为 {}，不包含任何附加信息

--------------------------
### put
**用 PUT 方法请求指定的 [url](../../module/ifs/url.md)，并返回结果，等同于 request("PUT", ...)**

```JavaScript
HttpResponse HttpClient.put(String url,
    Object opts = {}) async;
```

调用参数:
* url: String, 指定 [url](../../module/ifs/url.md)，必须是包含主机的完整 [url](../../module/ifs/url.md)
* opts: Object, 指定附加信息

返回结果:
* [HttpResponse](HttpResponse.md), 返回服务器响应

opts 包含请求的附加选项，支持的内容如下：

```JavaScript
{
    "query": {},
    "body": SeekedStream | Buffer | String | {},
    "json": {},
    "headers": {}
}
```

其中 body，[json](../../module/ifs/json.md) 不得同时出现。缺省为 {}，不包含任何附加信息

--------------------------
### patch
**用 PATCH 方法请求指定的 [url](../../module/ifs/url.md)，并返回结果，等同于 request("PATCH", ...)**

```JavaScript
HttpResponse HttpClient.patch(String url,
    Object opts = {}) async;
```

调用参数:
* url: String, 指定 [url](../../module/ifs/url.md)，必须是包含主机的完整 [url](../../module/ifs/url.md)
* opts: Object, 指定附加信息

返回结果:
* [HttpResponse](HttpResponse.md), 返回服务器响应

opts 包含请求的附加选项，支持的内容如下：

```JavaScript
{
    "query": {},
    "body": SeekedStream | Buffer | String | {},
    "json": {},
    "headers": {}
}
```

其中 body，[json](../../module/ifs/json.md) 不得同时出现。缺省为 {}，不包含任何附加信息

--------------------------
### toString
**返回对象的字符串表示，一般返回 "[Native Object]"，对象可以根据自己的特性重新实现**

```JavaScript
String HttpClient.toString();
```

返回结果:
* String, 返回对象的字符串表示

--------------------------
### toJSON
**返回对象的 JSON 格式表示，一般返回对象定义的可读属性集合**

```JavaScript
Value HttpClient.toJSON(String key = "");
```

调用参数:
* key: String, 未使用

返回结果:
* Value, 返回包含可 JSON 序列化的值

