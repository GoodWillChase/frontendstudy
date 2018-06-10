## 数组



delete arr[0]; //把第一位的值改为 undefined，原数组长度不变。



for in  不保证索引顺序



- 使用`typeof`检查Infinity也会返回number。
- 注意：`typeof NaN`的返回结果是number。

- 使用 typeof 检查一个null值时，会返回object。

- 使用 type of 检查一个undefined时，会返回undefined。
- **声明**一个变量，但是没有**赋值**，此时它的值就是undefined。例如：`var a;`
- 使用`typeof`检查一个函数对象时，会返回function



- null == undefined的结果(true)
- null ===undefined的结果(false)
- 和数字运算时，10 + null结果为：10；10 + undefined结果为：NaN。

- 任何数据类型和undefined运算都是NaN;
- 任何值和null运算，null可看做0运算。



如果对非String使用parseInt()或parseFloat()，它会先将其转换为String然后再操作。

```js
var a = true;
console.log(parseInt(a));  //打印结果：NaN （因为是先将a转为字符串"true"，然后然后再操作）

var b = undefined;
console.log(parseInt(b));  //打印结果：NaN  （因为是先将b转为字符串"undefined"，然后然后再操作）

var c = 168.23;
console.log(parseInt(c));  //打印结果：168  （因为是先将c转为字符串"168.23"，然后然后再操作）
```
---



### 函数名、函数体和函数加载问题（重要，请记住）

我们要记住：**函数名 == 整个函数**。举例：

```javascript
        console.log(fn) == console.log(function fn(){alert(1)});

        //定义fn方法
        function fn(){
            alert(1)
        };
```

我们知道，当我们在调用一个函数时，通常使用`函数()`这种格式；但此时，我们是直接使用`函数`这种格式，它的作用相当于整个函数。

**函数的加载问题**：JS加载的时候，只加载函数名，不加载函数体。所以如果想使用内部的成员变量，需要调用函数。

---

## fn()  和 fn 的区别【重要】

- `fn()`：调用函数。相当于获取了函数的返回值。
- `fn`：函数对象。相当于直接获取了函数对象。

---

**变量的声明提前：**

使用var关键字声明的变量（ 比如 `var a = 1`），**会在所有的代码执行之前被声明**（但是不会赋值），但是如果声明变量时不是用var关键字（比如直接写`a = 1`），则变量不会被声明提前。

举例1：

```javascript
    console.log(a);
    var a = 123;
```

打印结果：undefined

举例2：

```javascript
    console.log(a);
    a = 123;   //此时a相当于window.a
```

程序会报错：



**函数的声明提前：**

- 使用`函数声明`的形式创建的函数`function foo(){}`，**会被声明提前**。

也就是说，它会在所有的代码执行之前就被创建，所以我们可以在函数声明之前，调用函数。

- 使用`函数表达式`创建的函数`var foo = function(){}`，**不会被声明提前**，所以不能在声明前调用。

很好理解，因为此时foo被声明了，且为undefined，并没有给其赋值`function(){}`。



在函数中，没有var声明的变量都会成为**全局变量**，而且并不会提前声明。



**提醒2：**定义形参就相当于在函数作用域中声明了变量。 ——？？？？

```
        function fun6(e) {
            console.log(e);
        }

        fun6();  //打印结果为 undefined
        fun6(123);//打印结果为123
```

## ？？

---

## new一个构造函数的过程

- 1.开辟对内存空间，创建一个新的对象
- 2.**把this设置为当前对象**
- 3.执行内部代码，设置对象属性和方法
- 4.返回新创建的对象

---



## 数组的添加和删除

（1）push()：在数组**最后面**插入项，返回数组的长度

```javascript
	数组改后的长度 = 数组.push(元素);
```

（2）pop()：取出数组中的**最后一个**元素，返回被删除的元素

```javascript
	被删除的元素 = 数组.pop();
```

（3）unshift()：在数组**最前面**插入项，返回数组的长度

数组改后的长度 = 数组.unshift(元素);

（4）shift()：取出数组中的**第一个**元素，返回被删除的元素

```javascript
	被删除的元素 = 数组.shift();
```

## 

---

题目：将一个字符串数组的元素的顺序进行反转，使用两种种方式实现。提示：第i个和第length-i-1个进行交换。

答案：

方式1：

```javascript
   function reverse(array) {
       var newArr = [];
       for (var i = array.length - 1; i >= 0; i--) {
           newArr[newArr.length] = array[i];
       }
       return newArr;
   }
```

方式2：（算法里比较常见的方式）

```javascript
   function reverse(array){
       for(var i=0;i<array.length/2;i++){
           var temp = array[i];
           array[i] = array[array.length-1-i];
           array[array.length-1-i] = temp;
       }
       return array;
   }
```

方式3：（数组自带的reverse方法）

现在我们学习了数组自带的api，我们就可以直接使用reverse()方法。

---

### 练习5

问题：编写一个方法去掉一个数组中的重复元素。

分析：创建一个新数组，循环遍历，只要新数组中有老数组的值，就不用再添加了。

答案：

```javascript
//    编写一个方法 去掉一个数组的重复元素
    var arr = [1,2,3,4,5,2,3,4];
    console.log(arr);
    var aaa = fn(arr);
    console.log(aaa);
    //思路：创建一个新数组，循环遍历，只要新数组中有老数组的值，就不用再添加了。
    function fn(array){
        var newArr = [];
        for(var i=0;i<array.length;i++){
            //开闭原则
            var bool = true;
            //每次都要判断新数组中是否有旧数组中的值。
            for(var j=0;j<newArr.length;j++){
                if(array[i] === newArr[j]){
                    bool = false;
                }
            }
            if(bool){
                newArr[newArr.length] = array[i];
            }
        }
        return newArr;
    }
```

## 

---

**练习2：**判断一个字符串中出现次数最多的字符，统计这个次数

```html
<script>
    var str2 = "smyhvaevaesmyhvae";

    //定义一个json，然后判断json中是够有该属性，如果有该属性，那么值+1;否则创建一个该属性，并赋值为1；
    var json = {};
    for (var i = 0; i < str2.length; i++) {
        //判断：如果有该属性，那么值+1;否则创建一个该属性，并赋值为1；
        var key = str2.charAt(i);
        if (json[key] === undefined) {
            json[key] = 1;
        } else {
            json[key] += 1;
        }
    }
    console.log(json);


    console.log("----------------");
    //获取json中属性值最大的选项
    var maxKey = "";
    var maxValue = 0;
    for (var k in json) {
        //        if(maxKey == ""){
        //            maxKey = k;
        //            maxValue = json[k];
        //        }else{
        if (json[k] > maxValue) {
            maxKey = k;
            maxValue = json[k];
        }
        //        }
    }
    console.log(maxKey);
    console.log(maxValue);


</script>
```

---



**补充一个知识点：**

在 js中：

- 如果想获取 `html`节点，方法是`document.documentElement`。
- 如果想获取 `body` 节点，方法是：`document.body`。

二者不要混淆了。

---

### 题目一：如何准确判断一个变量时数组类型

答案：

```javascript
    var arr1 = [];

    console.log(arr1 instanceof Array); //打印结果：true。
    console.log(typeof arr1);           //打印结果：object。提示：typeof 方法无法判断是否为数组
```

上方代码表明，只能通过 instanceof 来判断是否为数组。而 typeof 的打印结果是 object。

---

### 题目三：描述 new 一个对象的过程

（1）创建一个新对象

（2）this 指向这个新对象

（3）执行代码（对this 赋值）

（4）返回this

---

### 以函数形式调用时，this永远都是window

### 以方法的形式调用时，this是调用方法的对象



this指的是，**调用函数的那个对象**。this永远指向函数运行时所在的对象。

解析器在调用函数每次都会向函数内部传递进一个隐含的参数，这个隐含的参数就是this。

根据函数的调用方式的不同，this会指向不同的对象：【重要】

- 1.以函数的形式调用时，this永远都是window。比如`fun();`相当于`window.fun();`
- 2.以方法的形式调用时，this是调用方法的那个对象
- 3.以构造函数的形式调用时，this是新创建的那个对象
- 4.使用call和apply调用时，this是指定的那个对象

需要特别提醒的是：this的指向在函数定义时无法确认，只有函数执行时才能确定。



---

---

## var  let

首先我们知道在for循环中，异步打印循环变量得到的值是一样的，都是循环最后一次的i的值

```js
for(var i = 0;i<10;i++){
    setTimeout(function(){
        console.log(i)
    },100)
}  // 输出全是10
// 输出全是10的原因是因为i是全局变量，最后访问的都是全局变量i，而每次循环改变i的值就是改变全局变量的值，故而输出值均为10
// 之前对于这种问题的解决办法是通过闭包来实现
for(var i = 0;i<10;i++){
    (function(){
        var j = i;
        setTimeout(function(){
            console.log(j);
        },100)
    }())
}  // 输出0123456789;
```

而let呢，因为他是块级作用域，在for循环中，很明显我们是能找到一个`{}`构成的代码块的

```js
for(let i = 0;i<10;i++){
    setTimeout(function(){
        console.log(i)
    },100)
}  // 0123456789;

```

为什么使用let就成了这个样子呢，就是和let的块级作用域。解释就很简单了，因为每次循环都创建一个块级作用域，并且存上i的值，这里面的let定义的`i`值就是局部变量,所以每次循环改变的就是对局部变量赋值，访问也是根据[作用域链](http://blog.csdn.net/stoplll/article/details/61203494)规则访问局部变量`i`这样就得到了最后的结果。 

同样的，还有一个例子就是当let定义在for循环之外呢

```
let i = 0;
for(;i<10;i++){
    setTimeout(function(){
        console.log(i)
    },100)
}  // 全是10;
1234567
```

不是说好let是块级作用域么，为什么又是一个全是10，因为这里let定义的地方就是全局作用域下啊，所以这里的`i`就是全局作用域，所以代码块对`i`就没有约束能力了，因为`i`是个全局变量，局部改变它的值就是改变全局变量的值，最后打印的`i`也是访问全局变量`i`打印其值，自然都是打印的同一个值。

---

**变量的声明提前：**（变量提升）

使用var关键字声明的变量（ 比如 `var a = 1`），**会在所有的代码执行之前被声明**（但是不会赋值），但是如果声明变量时不是用var关键字（比如直接写`a = 1`），则变量不会被声明提前。

---

**函数的声明提前：**

- 使用`函数声明`的形式创建的函数`function foo(){}`，**会被声明提前**。

也就是说，它会在所有的代码执行之前就被创建，所以我们可以在函数声明之前，调用函数。

- 使用`函数表达式`创建的函数`var foo = function(){}`，**不会被声明提前**，所以不能在声明前调用。

很好理解，因为此时foo被声明了，且为undefined，并没有给其赋值`function(){}`。

---

在函数作用域也有声明提前的特性：

- 使用var关键字声明的变量，是在函数作用域内有效，而且会在函数中所有的代码执行之前被声明
- 函数声明也会在函数中所有的代码执行之前执行

因此，在函数中，没有var声明的变量都会成为**全局变量**，而且并不会提前声明。



**提醒2：**定义形参就相当于在函数作用域中声明了变量。

```
        function fun6(e) {
            console.log(e);
        }

        fun6();  //打印结果为 undefined
        fun6(123);//打印结果为123
```

---



## 常见的闭包

- 1. 将一个函数作为另一个函数的返回值
- 1. 将函数作为实参传递给另一个函数调用。

### 闭包1：将一个函数作为另一个函数的返回值

```javascript
    function fn1() {
      var a = 2

      function fn2() {
        a++
        console.log(a)
      }
      return fn2
    }

    var f = fn1();   //执行外部函数fn1，返回的是内部函数fn2
    f() // 3       //执行fn2
    f() // 4       //再次执行fn2

```

当f()第二次执行的时候，a加1了，也就说明了：闭包里的数据没有消失，而是保存在了内存中。如果没有闭包，代码执行完倒数第三行后，变量a就消失了。

上面的代码中，虽然调用了内部函数两次，但是，闭包对象只创建了一个。

也就是说，要看闭包对象创建了一个，就看：**外部函数执行了几次**（与内部函数执行几次无关）。

### 闭包2. 将函数作为实参传递给另一个函数调用

```javascript
    function showDelay(msg, time) {
      setTimeout(function() {  //这个function是闭包，因为是嵌套的子函数，而且引用了外部函数的变量msg
        alert(msg)
      }, time)
    }
    showDelay('atguigu', 2000)
```

上面的代码中，闭包是里面的funciton，因为它是嵌套的子函数，而且引用了外部函数的变量msg。



---









































