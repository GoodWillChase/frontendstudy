在 [Date 方法](https://www.w3cschool.cn/jsref/jsref-obj-date.html) 章节中，你可以查看更多关于日期转换为字符串的函数：

| 方法              | 描述                                        |
| ----------------- | ------------------------------------------- |
| getDate()         | 从 Date 对象返回一个月中的某一天 (1 ~ 31)。 |
| getDay()          | 从 Date 对象返回一周中的某一天 (0 ~ 6)。    |
| getFullYear()     | 从 Date 对象以四位数字返回年份。            |
| getHours()        | 返回 Date 对象的小时 (0 ~ 23)。             |
| getMilliseconds() | 返回 Date 对象的毫秒(0 ~ 999)。             |
| getMinutes()      | 返回 Date 对象的分钟 (0 ~ 59)。             |
| getMonth()        | 从 Date 对象返回月份 (0 ~ 11)。             |
| getSeconds()      | 返回 Date 对象的秒数 (0 ~ 59)。             |
| getTime()         | 返回 1970 年 1 月 1 日至今的毫秒数。        |

---

在 [Number 方法](https://www.w3cschool.cn/jsref/jsref-obj-number.html) 章节中，你可以查看到更多关于字符串转为数字的方法：

| 方法         | 描述                               |
| ------------ | ---------------------------------- |
| parseFloat() | 解析一个字符串，并返回一个浮点数。 |
| parseInt()   | 解析一个字符串，并返回一个整数。   |

---

## 正则表达式修饰符

**修饰符** 可以在全局搜索中不区分大小写:

| 修饰符 | 描述                                                     |
| ------ | -------------------------------------------------------- |
| i      | 执行对大小写不敏感的匹配。                               |
| g      | 执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。 |
| m      | 执行多行匹配。                                           |

------

## 正则表达式模式

方括号用于查找某个范围内的字符：

| 表达式 | 描述                       |
| ------ | -------------------------- |
| [abc]  | 查找方括号之间的任何字符。 |
| [0-9]  | 查找任何从 0 至 9 的数字。 |
| (x\|y) | 查找任何以 \| 分隔的选项。 |

元字符是拥有特殊含义的字符：

| 元字符 | 描述                                        |
| ------ | ------------------------------------------- |
| \d     | 查找数字。                                  |
| \s     | 查找空白字符。                              |
| \b     | 匹配单词边界。                              |
| \uxxxx | 查找以十六进制数 xxxx 规定的 Unicode 字符。 |

量词:

| 量词 | 描述                                  |
| ---- | ------------------------------------- |
| n+   | 匹配任何包含至少一个 *n* 的字符串。   |
| n*   | 匹配任何包含零个或多个 *n* 的字符串。 |
| n?   | 匹配任何包含零个或一个 *n* 的字符串。 |

---



JavaScript提供七种不同的data types(数据类型)，它们是`undefined`（未定义）, `null`（空）, `boolean`（布尔型）, `string`（字符串）, `symbol`(符号), `number`（数字）, and `object`（对象）。 



----

## JSON



下面在重点给大家介绍JS中json数据的处理
1、 json数据结构(对象和数组)
json对象：var obj = {"name":"xiao","age":12};
json数组：var objArray = [{"name":"xiao","age":12},{"name":"xiao","age":12}];

2、 处理json数据，依赖文件有：jQuery.js

3、Note：数据传输过程中，json数据是以文本，即字符串格式形式存在；
JS语言操作的是JS对象；
所以json字符串与JS对象之间的转换是关键；

4、数据格式
Json字符串：var json_str = ‘{"name":"xiao","age":12}';
Josn对象：var obj = {"name":"xiao","age":12};
JS对象：Object {name: "xiao", age: 12}

5、类型转换
Json字符串——>JS对象，使用方法：
注明：

json_str、obj代表的是在本文子标题4中的数据类型；
obj = JSON.parse(json_str);
obj = jQuery.parseJSON(json_str);
Note:传入畸形json字符串(例如：‘{name:"xiao",age:12}')，会抛出异常；
Json字符串格式，严格格式：‘{"name":"xiao","age":12}'
JS对象——>Json字符串：
json_str = JSON. stringify(obj);



Json字符串——>JS对象; 

```json
JSON.parse('{"name":"Xiao","age":12}')
{name: "Xiao", age: 12}
jQuery.parseJSON('{"name":"Xiao","age":12}')
{name: "Xiao", age: 12}
```

JS对象——>Json字符串： 

```json
JSON.stringify({name: "Xiao", age: 12})
"{"name":"Xiao","age":12}"	
```















