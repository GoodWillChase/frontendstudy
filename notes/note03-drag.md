## 设置元素为可拖放

首先，为了使元素可拖动，把 draggable 属性设置为 true ：    

<img draggable="true">

------

## 拖动什么 - ondragstart 和 setData()

然后，规定当元素被拖动时，会发生什么。

在上面的例子中，**ondragstart 属性调用了一个函数，drag(event)，它规定了被拖动的数据。**

**dataTransfer.setData() 方法设置被拖数据的数据类型和值：  **  

```js
function drag(ev)        
{ ev.dataTransfer.setData("Text",ev.target.id);       
}
```

在这个例子中，数据类型是 "Text"，值是可拖动元素的 id ("drag1")。

**提示：**你可以在本站的“[ondragstart 事件](https://www.w3cschool.cn/jsref/event-ondragstart.html)”部分了解到更多的有用信息！

------

## 放到何处 - ondragover

[ondragover 事件](https://www.w3cschool.cn/jsref/event-ondragover.html)规定在何处放置被拖动的数据。

**默认地，无法将数据/元素放置到其他元素中。如果需要设置允许放置，我们必须阻止对元素的默认处理方式。**

**这要通过调用 ondragover 事件的 event.preventDefault() 方法：**    

 *event*.preventDefault()



------

## 进行放置 - ondrop

当放置被拖数据时，会发生 drop 事件。

在上面的例子中，ondrop 属性调用了一个函数，drop(event)：    
```js
function drop(ev)        
{        
ev.preventDefault();        
var data=ev.dataTransfer.getData("Text");        
ev.target.appendChild(document.getElementById(data));        
}
```
代码解释：

- **调用 preventDefault() 来避免浏览器对数据的默认处理（drop 事件的默认行为是以链接形式打开）**
- **通过 dataTransfer.getData("Text") 方法获得被拖的数据。该方法将返回在 setData() 方法中设置为相同类型的任何数据。**
- 被拖数据是被拖元素的 id ("drag1")
- 把被拖元素追加到放置元素（目标元素）中





----
sr-only 代表元素只在屏幕阅读器中显示：sc (screen-reader)，为残障人士 设计，体现人文关怀；

这是专门为残障人士浏览网页设计的。

在前端开发中，有些时候设计图上面会出现仅供正常视觉用户看的元素。比如：导航栏菜单当前页面选中高亮状态，这些状态只有视力正常的人才能正常使用。

而残障人士，弱势或盲人是很难或者根本看不出导航菜单高亮的。他们上网可能借助的是屏幕阅读器，也就是 screen reader（sr），屏幕阅读器需要找到能辨识的文本说明然后“读”出来给用户听。

问题是：一些元素，比如选中高亮状态无法读出。因此我们还要写上这些元素的文本说明，但是又不需要展示给普通用户看到，于是加上 sr-only 的意义就在于能保证屏幕阅读器正确读取且不会影响正常人的使用。

比如：导航栏首页链接被选中高亮，我们可以这样表示。

```html
<li class="active">

  <a href="#">首页 <span class="sr-only">(current)</span></a>

</li>
```

这样正常人看起来只有首页两个字，而屏幕阅读器却可以读首页 current

---

data-toggle的意思是设置触发器，相当于告诉浏览器你是一个什么组件；data-target是设置目标，相当于告诉浏览器你要操作那个元素

---

