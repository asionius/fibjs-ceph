# 对象 EventInfo
事件信息对象，用于在事件中传递信息

## 继承关系
```dot
digraph {
    node [fontname="Helvetica,sans-Serif", fontsize=10, shape="record", style="filled", fillcolor="white"];

    object [tooltip="object", URL="object.md", label="{object|toString()\ltoJSON()\l}"];
    EventInfo [tooltip="EventInfo", fillcolor="lightgray", id="me", label="{EventInfo|operator[String]\l|code\lreason\ltype\ltarget\l}"];

    object -> EventInfo [dir=back];
}
```

## 下标操作
        
**根据事件类型返回的详细信息**

```JavaScript
readonly Value EventInfo[String];
```

## 成员属性
        
### code
**Integer, 查询事件错误编码**

```JavaScript
readonly Integer EventInfo.code;
```

--------------------------
### reason
**String, 查询事件错误信息**

```JavaScript
readonly String EventInfo.reason;
```

--------------------------
### type
**String, 查询事件类型**

```JavaScript
readonly String EventInfo.type;
```

--------------------------
### target
**Object, 查询触发事件的对象**

```JavaScript
readonly Object EventInfo.target;
```

## 成员函数
        
### toString
**返回对象的字符串表示，一般返回 "[Native Object]"，对象可以根据自己的特性重新实现**

```JavaScript
String EventInfo.toString();
```

返回结果:
* String, 返回对象的字符串表示

--------------------------
### toJSON
**返回对象的 JSON 格式表示，一般返回对象定义的可读属性集合**

```JavaScript
Value EventInfo.toJSON(String key = "");
```

调用参数:
* key: String, 未使用

返回结果:
* Value, 返回包含可 JSON 序列化的值

