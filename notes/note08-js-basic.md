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















