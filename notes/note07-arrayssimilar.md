## 任务

请在index.html文件中，编写arraysSimilar函数，实现判断传入的两个数组是否相似。具体需求：

1. 数组中的成员类型相同，顺序可以不同。例如[1, true] 与 [false, 2]是相似的。

2. 数组的长度一致。

3. 类型的判断范围，需要区分:String, Boolean, Number, undefined, null, 函数，日期, window.

当以上全部满足，则返回"判定结果:通过"，否则返回"判定结果:不通过"。

---

```html
<!DOCTYPE HTML>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=gb18030">
    <title>Untitled Document</title>
    
</head>
<body>
    <script type="text/javascript">   
        /*
         * param1 Array 
         * param2 Array
         * return true or false
         */
        function arraysSimilar(arr1, arr2){
        
        }
    </script>
    <script src="testData.js"></script>
</body>
</html>
```



```js
var result=function(){
    //以下为多组测试数据
            var cases=[{
                    arr1:[1,true,null],
                    arr2:[null,false,100],
                    expect:true
                },{
                    arr1:[function(){},100],
                    arr2:[100,{}],
                    expect:false
                },{
                    arr1:[null,999],
                    arr2:[{},444],
                    expect:false
                },{
                    arr1:[window,1,true,new Date(),"hahaha",(function(){}),undefined],
                    arr2:[undefined,(function(){}),"okokok",new Date(),false,2,window],
                    expect:true
                },{
                    arr1:[new Date()],
                    arr2:[{}],
                    expect:false
                },{
                    arr1:[window],
                    arr2:[{}],
                    expect:false
                },{
                    arr1:[undefined,1],
                    arr2:[null,2],
                    expect:false
                },{
                    arr1:[new Object,new Object,new Object],
                    arr2:[{},{},null],
                    expect:false
                },{
                    arr1:null,
                    arr2:null,
                    expect:false
                },{
                    arr1:[],
                    arr2:undefined,
                    expect:false
                },{
                    arr1:"abc",
                    arr2:"cba",
                    expect:false
                }];
            
    //使用for循环, 通过arraysSimilar函数验证以上数据是否相似，如相似显示“通过”,否则"不通过",所以大家要完成arraysSimilar函数,具体要求，详见任务要求。    
            for(var i=0;i<cases.length;i++){
                if(arraysSimilar(cases[i].arr1,cases[i].arr2)!==cases[i].expect) {
                    document.write("不通过！case"+(i+1)+"不正确！arr1="+JSON.stringify(cases[i].arr1)+", arr2="+JSON.stringify(cases[i].arr2)+" 的判断结果不是"+cases[i].expect);
                    return false;
                }                
            }
            return true;
            
        }();
    document.write("判定结果:"+(result?"通过":"不通过"));
```



----



### 参考一：

```html
<!DOCTYPE HTML>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=gb18030">
    <title>Untitled Document</title>
    
</head>
<body>
    <script type="text/javascript">   
        /*
         * param1 Array 
         * param2 Array
         * return true or false
         */
        function arraysSimilar(arr1, arr2){
            if(arr1 instanceof Array && arr2 instanceof Array){
                var key1 = [],key2 = [],len = arr1.length,len2=arr2.length;
                // 数组的长度相等判断
                if(len!=len2){return false;}
                // 类型相同判断
                if(len){
                    // 获取类型列表
                    for(var i= 0;i<len;i++){
                        // 数组1的类型列表字串
                        var item1 = arr1[i], typeFirst = typeOf(item1);
                        if(key1.join().indexOf(typeFirst)<0){
                            key1.push(typeFirst);
                        }
                        
                        // 数组2的类型列表字串
                        var item2 = arr2[i],typeSecond = typeOf(item2);
                        if(key2.join().indexOf(typeSecond)<0){
                            key2.push(typeSecond);
                        } 
                    }
                    key1 = key1.sort();
                    key2 = key2.sort();
                    // 类型字串比较
                    if(key1.join() == key2.join()){
                        return true;
                    }else{
                        return false;
                    }
                }else{
                    // 空数组相等
                    return true;
                }
            }else{
                // 非数组
                return false;
            }

        }
        
        /**
         * 类型判断方法
         * param item 
         * return type(string,function,boolean,number,undefined,null,window,Date,Array,object)
         */
        function typeOf(item){
            var type = typeof item;
            if(type != "object"){
                // 判断基本类型string,function,boolean,number,undefine
            }else if(item === null){
                // check null
                type = "null";
            }else if(item === window){
                // check window
                type ="window";
            }else{
                // 判断object类型object,date,array
                if(item instanceof Date){
                    type = "date";
                }else if(item instanceof Array){
                    type = 'array';
                }else{
                    type = 'object';
                }
            }
            return type;
        }
    </script>
    <script src="testData.js"></script>
</body>
</html>
```



---

### 参考二：



```html
<!DOCTYPE HTML>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=gb18030">
    <title>Untitled Document</title>
    
</head>
<body>
    <script type="text/javascript">   
        // 判断边界
        function arraysSimilar(arr1, arr2){
            if (!(arr1 instanceof Array)||!(arr2 instanceof Array)) {
                return false;
            }
        // 判断长度
        if (arr1.length !== arr2.length) {return false;}

        var i=0;
            n = arr1.length;
            countMap1 = {};
            countMap2 = {};
            t1, t2,
            TYPES = ['string','boolean','number','null','undefined','function','date','window'];

        for (;i<n;i++) {
            t1 = typeOf(arr1[i]);
            t2 = typeOf(arr2[i]);
            
            if (countMap1[t1]) {
                countMap1[t1]++;
            } else {
                countMap1[t1] = 1;
            }

            if (countMap1[t2]) {
                countMap1[t2]++;
            } else {
                countMap1[t2] = 1;
            }
        }

        function tyoeOf(ele) { 
            var r;
            if (ele === null) r='null';
            else if (ele instanceof Array) r='array';
            else if (ele === window) r='window';
            else if (ele instanceof Date) r='date';
            else r = typeof ele;
            return r;
         }

        for (i=0,n=TYPES.length;i<n;i++) {
            if (countMap1[TYPES[i]] !== countMap2[TYPES[i]]) {
                return false;
          }
        }
        return true;
        }
    </script>
    <script src="testData.js"></script>
</body>
</html>
```



---



```html
<!DOCTYPE HTML>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=gb18030">
    <title>Untitled Document</title>
    
</head>
<body>
    <script type="text/javascript">
        const TYPES = {"String":1,"Boolean":2,"Number":3,"Undefined":4,"Null":5,"Function":6,"Date":7,"Window":8};
        /*
         * param1 Array 
         * param2 Array
         * return true or false
         */
        function arraysSimilar(arr1, arr2){
            this.getType=function(e){return Object.prototype.toString.call(e).replace('[object ','').replace(']','')}
            this.isArray=function(e){return getType(e)==="Array"}
            this.sumType=function(arr){for(var i=0,r=0;i<arr.length;i++)r+=TYPES[getType(arr[i])];return r;}
            if(!isArray(arr1)||!isArray(arr2)||arr1.length!=arr2.length) {return false;}
            return sumType(arr1) === sumType(arr2);
        }
    </script>
    <script src="testData.js"></script>
</body>
</html>
```



---











