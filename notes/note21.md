

### 筛选数组 `newArray[newArray.length]`

```js
var numbers = [332,45,56,234,0,567,0,67,3];
var newArray = [];
for (var i=0; i < numbers.length; i++) {
    if (numbers[i] != 0) {
        newArray[newArray.length] = numbers[i];
    }
}
```

注意 `newArray[newArray.length]` 的用法

---



如果函数不需要返回值，可以不写 return --> 函数返回 `undefined`

return 后面可以什么都不跟 --> 后面的代码不执行，返回 `undefined`

---

### 对数组进行排序 `sort`

```js
// 对数组排序---冒泡排序
function sort(array) {
	// 外层循环，控制趟数
	for (var i = 0; i < array.length - 1; i++) {
		// 假设排序好了
		isSort = true;
		// 内层循环，两两比较
		for (var j = 0; j < array.length - 1; j++) {
			if (array[j] > array[j + 1]) {
				// 没有排好序
				isSort = false;
				var temp = array[j];
				array[j] = array[j + 1];
				array[j + 1] = temp;
			}
		}
		// 判断是否排好序
		if (isSort) {
			break;
		}
	}
	return array;
}
```



---

### 输入年月日，判断这一天是今天的第几天 `Date`

```js

// 判断是否是闰年
function isRun(year) {
  var result = false;
  if (year % 4 == 0 && year % 100 != 0 || year % 400 == 0) {
    result = true;
  }
  return result;
}


function getDays(year, month, day) {
  var days = day;
  for (var i = 1; i < month - 1; i++) {
    switch (i) {
      case 1:
      case 3:
      case 5:
      case 7:
      case 8:
      case 10:
      case 12:
        days += 31;
        // 不要忘记 break ！
        break;
      case 4:
      case 6:
      case 9:
      case 11:
        days += 30;
        break;
      case 2:
        if (isRun(year)) {
          days += 29;
        } else {
          days += 28;
        }
        break;
    }
  }
  return days;
}

console.log(getDays(2018,11,8))

```



---



### 打印一个数组中所有 'a' 出现的位置 `indexOf`

```js
var arr = ['c', 'a', 'd', 'a', 't', 'e', 'a'];

//重点！！！
//index 赋值 -1，使得下面的 index + 1 可以从 0 开始。
/*
string.indexOf(searchvalue,start)
searchvalue	   必需。规定需检索的字符串值。
start	         可选的整数参数。规定在字符串中开始检索的位置。它的合法取值是 0 到 string Object.length - 1。如省略该参数，则将从字符串的首字符开始检索。
*/

var index = -1;
do {
    //注意 index + 1 的用法
    index = arr.indexOf('a', index + 1);
    if (index !== -1) {
        console.log(index);
    }
} while (index !== -1);
```



---

### 取消a标签的默认行为 

```js
   <a id="link" href="http://www.baidu.com">百度</a>
   <script>
     var link = document.getElementById('link');
     link.onclick = function () {
       alert('点击我了');

       // 取消a标签的默认行为（跳转到href）
       return false;
     }

```



---





























































