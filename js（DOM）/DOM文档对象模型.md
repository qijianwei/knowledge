# 文档对象模型 (DOM) -document object model
### 概念
通过document提供的API接口，操作页面的内容属性和方法
> API：Application Program Interface

* Document：文档，也就是我们说的html、xml等等这些具有树结构的文本内容
* Object：对象
* Model：模型、一堆接口（抽象）
 > 把具有树结构的文档解析成对象并提供一系列的方法对其进行操作



### 文档树 - DOM 树
document：意义上的文档顶层对象

![image](https://poppinlp.github.io/static/gist/fe-foundation-course-8-dom-1.png)

节点关系

![image](https://poppinlp.github.io/static/gist/fe-foundation-course-8-dom-2.png)

> 以上引用来源
http://poppinlp.com/front-end-appetizers/book/posts/lesson-9.html

页面中又几个特殊元素可以直接通过document来获取

    1.documentElement:<html>
    2.title:<title>
    3.body:<body>

> 注意：在获取元素的一系列方法中，getElementById这个方法只有document对象才有

## 节点

### 概念
Node，文档中的每一个元素都是tree上的节点    
Node的类型其实是有N多种的，我们看到的元素（标签）只是众多节点中的其中一种

### 分类
    1.Element（元素节点）
        1.HTMLElement（元素）
            1.HTMLDivElement（Div元素）
            2.HTMLImgElement（Img元素）
    2.Text（文本节点）
    3.Attribnute（属性节点）
    4.Comment（注释节点）
    5.Document（document节点）
    6.Processing_Instruction（声明节点）
    7.Document_Type（描述文档类型节点）
    8.DocumentFragment（没有父节点的最小的文档对象）
> 一共12个别的弃用，只做了解即可

### nodetype
返回节点的类型值

    1:元素节点
    2:属性节点
    3:文本节点
    8:注释节点
    9:document节点
    
    
## 集合
### HTMLCollection & NodeList
HTMLCollection:一个包含了元素的通用集合，并且提供了用来从集合中选择元素的方法和属性（返回集合中的元素数目）

NodeList：节点的集合（是从childNodes和querySelectorAll返回的）

### 静态集合和动态集合

静态集合：

    1.document.getElementById();
    2.Element.querySelector();
    3.Element.querySelectorAll();

动态集合：

    1.Element.getElementsByTagName();
    2.Element.getElementsByClassName();


# DOM操作
## Element（元素）
### 获取
==1.通过方法获取==

*   document.getElementById()
*   
        ——该方法通过id属性来获取对应的节点，由于id‘是唯一的属性，所以返回的结果为空或者是一个唯一的节点。

*   Element.getElementByTagName()

        ——通过获取标签名称来获取属于该标签节点的动态集合，其中的动态是指，如果通过别的方式更改了节点对应的内容，节点集合的内容也会发生改变。
        
*   Element.getElementsByClassName()

        ——通过类名获取包含该类的节点的动态集合
        
*   Element.querySelector()

        ——ie8+，和getElementById类似，通过id、class、标签等均可，静态获取方式。
        
*   Element.querySelectorAll()

        ——ie8+，通过id、class、标签等获取所有的元素，静态获取。

==2.通过属性获取==

**1.获取子集**
* childNodes
* children
* firstChild
  > 第一个子节点，如果无子节点，返回null
* lastChild
* firstElementChild
* lastElementChild

**2.获取兄弟**
> 只获取一级

* previousSibling
* nextSibling
* previousElementSibling
* nextElementSibling

**3.获取父级**
* parentNode
> 返回Nodelist

* offsetParent
> offsetParent : 获取有最近的有定位特性的父级    
   1. 自身有定位
       1. 没有定位的父级
           ie7-: html
           其他 : body
       2. 有定位父级
           定位父级
   2. 自身没有定位
       1. 没有定位父级
           其他: body
           ie7-:

               1. 没有触发hasLayout的父级
                   body
               2. 有触发hasLayout的父级
                   触发了hasLayout的父级
       2. 有定位父级
           定位父级


### 创建

* innerHTML
   > document.body.innerHTML = '<p>Hello world</p>'
* document.createElement()
    * Element.appendChild()
    
    > 将创建的元素添加在父级的最后

    * Element.insertBefore()
    > 将创建的元素添加在xx之前，如果第2个需要填入的元素是不存在的，需要appendChild进行判断添加
    
    * Element.replaceChild()
    > (父元素对象)Element.replaceChild(Element 要替换的子元素对象, Element 被替换的子元素对象)    
    
    * Element.cloneNode()
    > Element = Element1.cloneNode(isDeepinClone)    isDeepinClone：是否深度克隆，默认是false

cloneNode方法
```
var btn = document.querySelector('button');
    var ul = document.querySelector('ul');

    btn.onclick = function() {
        var newUl = ul.cloneNode(true);
        document.body.appendChild(newUl);
    }
```    
replaceChild方法
```
var btn = document.querySelector('button');
    var ul = document.querySelector('ul');

    btn.onclick = function() {
        var li = document.createElement('li');
        li.innerHTML = '新的li';
        ul.replaceChild(li, ul.children[0]);
    }
    
```
    


* innerHTML 和 createElement

### 删除
Element.removeChild