## HTML 速查列表

------



------

## HTML 基本文档

```html
<!DOCTYPE html>
<html>
<head>
<title>文档标题</title>
</head>
<body> 可见文本... </body>
</html>
```

## 基本标签（Basic Tags）

```html
<h1>最大的标题</h1>
 <h2> . . . </h2>
 <h3> . . . </h3>
 <h4> . . . </h4>
 <h5> . . . </h5>
 <h6>最小的标题</h6>
 <p>这是一个段落。</p>
 <br> （换行）
 <hr> （水平线）
 <!-- 这是注释 -->
```

## 文本格式化（Formatting）

```html
<b>粗体文本</b>
 <code>计算机代码</code>
 <em>强调文本</em>
 <i>斜体文本</i>
 <kbd>键盘输入</kbd>
 <pre>预格式化文本</pre>
 <small>更小的文本</small>
 <strong>重要的文本</strong>
 <abbr> （缩写）
 <address> （联系信息）
 <bdo> （文字方向）
 <blockquote> （从另一个源引用的部分）
 <cite> （工作的名称）
 <del> （删除的文本）
 <ins> （插入的文本）
 <sub> （下标文本）
 <sup> （上标文本）
```

## 链接（Links）

```html
普通的链接：<a href="链接地址">链接文本</a>
图像链接： <a href="http://www.example.com/"><img src="URL" alt="替换文本"></a> 
邮件链接： <a href="mailto:webmaster@example.com">发送e-mail</a>
书签： <a id="tips">
提示部分</a> <a href="#tips">跳到提示部分</a>
```

## 图片（Images）

```html
<img src="URL" alt="替换文本" height="42" width="42">
```

## 样式/区块（Styles/Sections）

```html
<style type="text/css">
   h1 {color:red;}
   p {color:blue;}
 </style>
 <div>文档中的块级元素</div>
 <span>文档中的内联元素</span>
```

## 无序列表

```html
<ul>
   <li>项目</li>
   <li>项目</li>
 </ul>
```

## 有序列表

```html
<ol>
   <li>第一项</li>
   <li>第二项</li>
 </ol>
```

## 定义列表

```html
<dl>
   <dt>项目 1</dt>
     <dd>描述项目 1</dd>
   <dt>项目 2</dt>
     <dd>描述项目 2</dd>
 </dl>
```

## 表格（Tables）

```html
<table border="1">
   <tr>
     <th>表格标题</th>
     <th>表格标题</th>
   </tr>
   <tr>
     <td>表格数据</td>
     <td>表格数据</td>
   </tr>
 </table>
```

## 框架（Iframe）

```html
<iframe src="demo_iframe.htm"></iframe>
```

## 表单（Forms）

```html
<form action="demo_form.php" method="post/get">

<input type="text" name="email" size="40" maxlength="50"> 
<input type="password"> 
<input type="checkbox" checked="checked"> 
<input type="radio" checked="checked"> 
<input type="submit" value="Send"> 
<input type="reset"> 
<input type="hidden"> 

<select> 
<option>苹果</option> 
<option selected="selected">香蕉</option> 
<option>樱桃</option> 
</select>

<textarea name="comment" rows="60" cols="20">
</textarea> 
</form>
```

## 实体（Entities）

```html
&lt; 等同于 <
 &gt; 等同于 >
&copy; 等同于 ©
```



---

为 HTML 添加新元素

```html
<script>
document.createElement("myHero")
</script>

<style>
myHero {
    display: block;
    background-color: #ddd;
    padding: 50px;
    font-size: 30px;
}
</style> 
```

```html
<myHero>我的第一个新元素</myHero>
```



---

```html
<!-- 带边框的表格 -->
<form action="">
    <fieldset>
        <legend>Personal information:</legend>
        Name: <input type="text" size="30"><br>
        E-mail: <input type="text" size="30"><br>
        Date of birth: <input type="text" size="10">
    </fieldset>
</form>

```



---

```html
<p>最好的 HTML 解决方法
    下面的例子使用了两个不同的音频格式。HTML5 audio 元素会尝试以 mp3 或 ogg 来播放音频。如果失败，代码将回退尝试 embed 元素。</p>
<audio controls>
  <source src="/statics/demosource/horse.mp3" type="audio/mpeg">
  <source src="/statics/demosource/horse.ogg" type="audio/ogg">
  <embed height="50" width="100" src="/statics/demosource/horse.mp3">
</audio>


<p>HTML视频（Videos）播放

    最好的 HTML 解决方法
    以下实例中使用了4种不同的视频格式。HTML 5 video 元素会尝试播放以 mp4、ogg 或 webm 格式中的一种来播放视频。如果均失败，则回退到 embed 元素。
    
    HTML 5 + object> + embed>:</p>

<video width="320" height="240" controls autoplay>
  <source src="/statics/demosource/movie.ogg" type="video/ogg">
  <source src="/statics/demosource/movie.mp4" type="video/mp4">
  <source src="/statics/demosource/movie.webm" type="video/webm">
  <object data="/statics/demosource/movie.mp4" width="320" height="240">
    <embed width="320" height="240" src="/statics/demosource/movie.swf">
  </object>
</video>

```



---

### LocalStorage

```html
<div id="result"></div>
<script>
if(typeof(Storage)!=="undefined")
{
  localStorage.sitename="W3Cschool在线教程";
  document.getElementById("result").innerHTML="网站名：" + localStorage.sitename;
}
else
{
  document.getElementById("result").innerHTML="对不起，您的浏览器不支持 web 存储。";
}
</script>

<br>
<hr>
<section><pre>
实例解析：

使用 key="sitename" 和 value="W3Cschool在线教程" 创建一个 localStorage 键/值对。
检索键值为"sitename" 的值然后将数据插入 id="result"的元素中。
以上实例也可以这么写：

// 存储
localStorage.sitename = "W3Cschool在线教程";
// 查找
document.getElementById("result").innerHTML = localStorage.sitename;

---

移除 localStorage 中的 "lastname" : 

localStorage.removeItem("lastname");

---

不管是 localStorage，还是 sessionStorage，可使用的API都相同，常用的有如下几个（以localStorage为例）： 

保存数据：localStorage.setItem(key,value);
读取数据：localStorage.getItem(key);
删除单个数据：localStorage.removeItem(key);
删除所有数据：localStorage.clear();
得到某个索引的key：localStorage.key(index);</pre></section>

```



---







---













