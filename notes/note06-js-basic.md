**注意**: javascript作为一种脚本语言可以放在html页面中任何位置，但是浏览器解释html时是按先后顺序的，所以前面的script就先被执行。比如进行页面显示初始化的js必须放在head里面，因为初始化都要求提前进行（如给页面body设置css等）；而如果是通过事件调用执行的function那么对位置没什么要求的。

---





## JS中如何输出空格

在写JS代码的时候，大家可以会发现这样现象:

**document.write("   1      2                3  ");**

**结果:** **1 2 3**

无论在输出的内容中什么位置有多少个空格，显示的结果好像只有一个空格。

这是因为浏览器显示机制，**对手动敲入的空格，将连续多个空格显示成1个空格**。

**解决方法:**

\1. 使用输出html标签`&nbsp;`来解决

 **`document.write("&nbsp;&nbsp;"+"1"+"&nbsp;&nbsp;&nbsp;&nbsp;"+"23");`**

 **结果:**  1    23

\2. 使用CSS样式来解决

`document.write("<span style='white-space:pre;'>"+"  1        2    3    "+"</span>");`



 **结果:**  1       2     3    

 在输出时添加“white-space:pre;”样式属性。这个样式表示"**空白会被浏览器保留**"

---

​		

## JavaScript-提问（prompt 消息对话框）

**prompt**弹出消息对话框,通常用于询问一些需要与用户交互的信息。弹出消息对话框（包含一个确定按钮、取消按钮与一个文本输入框）。

**语法:**

```
prompt(str1, str2);
```

**参数说明：**

```
str1: 要显示在消息对话框中的文本，不可修改
str2：文本框中的内容，可以修改
```

**返回值:**

```
1. 点击确定按钮，文本框中的内容将作为函数返回值
2. 点击取消按钮，将返回null
```

看看下面代码:

```
var myname=prompt("请输入你的姓名:");
if(myname!=null)
  {   alert("你好"+myname); }
else
  {  alert("你好 my friend.");  }
```

---



**操作符之间的优先级（高到低）:**

算术操作符 → 比较操作符 → 逻辑操作符 → "="赋值符号



---








