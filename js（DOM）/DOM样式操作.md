# Dom的样式操作
style属性：一个元素节点对象上的属性，我们可以通过这个属性，我们可以设置一个元素的行间样式
> 通过这个style添加的样式，是加入到行间的

### getComputedStyle(获取已经渲染过后的值)
- 返回一个CSSStyleDeclaration(div.style，获取的是没有渲染过的样式，大多数为空)

## 盒模型样式信息
### 宽高
- style.width／style.height
- getcomputedStyle().width／getcomputedStyle().heigth    
    -   样式宽高：前者获取渲染前的样式，后者获取渲染后的样式
- clientWidth／clientHeight    
    -   可视宽高：样式宽高 + padding

- offsetWidth／offsetHeight    
    -   实际宽高：样式宽高 + padding + border

### 定位
- offsetLeft／offsetTop
>浏览器默认8pxmargin
一个元素的offsetLeft／Top其实是到该元素的offsetParent

### Element.getBoundingClientRect():获取盒模型的信息
-   right：右边内侧到浏览器可视区域
-   top／left：元素的左侧／顶部，到浏览器可视区顶部的距离


### scrollLeft和scrollTop
- 滚动条滚动的距离

```
console.log(document.body.scrollTop)//滚动出可视区域的距离
```
==document.body.scrollTop || document.documentElement.scrollTop(火狐和chrom的滚动条兼容)==


## 窗口的宽高
- window.innerWidth
- window.innerHeigth
包含滚动条（pc会出现横向），推荐移动端使用

- document.documentElement.clientWidth
- document.documentElement.clientHeigth
推荐pc使用（移动端也可以，无兼容等问题）



```
style.width ==> 获取行间样式

getComputedStyle(div1).height ==> 200px(带单位的值)

div1.getBoundingClicent().heigth ==> 222(带边框+padding+div1的高度)

div1.clientheigth ==> 220(padding+div2的高度)

div1.offsetWidth ==> 222(带边框+padding+div2的高度)

div1.scrollHeight ==> 2010(从border开始，加上padding的值，一直到div2的高度结束，这部分算内容)
```


### scrollWidth和scrollHeigth
- scrollWidth：实际内容的宽度(从内容开始的位置到结束
- scrollHeigth:实际内容的高度

> 如果我的内容没有超出    
scrollWidth = clientWidth    
> 如果我的内容超出可视区    
scrollWidth > clientWidth
