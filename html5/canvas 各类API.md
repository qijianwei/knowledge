## HTML5 Canvas
> HTML5 <canvas> 元素用于图形的绘制，通过脚本 (通常是JavaScript)来完成.
<canvas> 标签只是图形容器，必须使用脚本来绘制图形。可以通过多种方法使用Canvas绘制路径,盒、圆、字符以及添加图像。

### 实例
```
<canvas id="myCanvas" width="200" height="100" style="border:1px solid #000000;">
</canvas>
<script>
    var c=document.getElementById("myCanvas");
    var ctx=c.getContext("2d");
    ctx.fillStyle="#FF0000";
    ctx.fillRect(0,0,150,75);
</script>
```

## Canvas坐标
 canvas 是一个二维网格。canvas 的左上角坐标为 (0,0)。横向是x轴，纵向是y轴。

## Canvas路径
```
moveTo(x,y) //定义线条开始坐标
lineTo(x,y) //定义线条结束坐标
```
## beginPath()
beginPath() 方法开始一条路径，或重置当前的路径

```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");

ctx.beginPath(); 
ctx.lineWidth="5";
ctx.strokeStyle="green"; // Green path
ctx.moveTo(0,75);
ctx.lineTo(250,75);
ctx.stroke(); // Draw it

ctx.beginPath();
ctx.strokeStyle="purple"; // Purple path
ctx.moveTo(50,0);
ctx.lineTo(150,130); 
ctx.stroke(); // Draw it
```
## closePath()

closePath() 方法创建从当前点到开始点的路径。

## fill()填充当前绘图（路径）
```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.rect(20,20,150,100);
ctx.fillStyle="red";
ctx.fill();
```
## clip()

clip()方法从原始画布中剪切任意形状和尺寸。

提示：一旦剪切了某个区域，则所有之后的绘图都会被限制在被剪切的区域内（不能访问画布上的其他区域）。您也可以在使用 clip() 方法前通过使用 save() 方法对当前画布区域进行保存，并在以后的任意时间对其进行恢复（通过 restore() 方法）。

## arc()绘制圆
【语法】
```
context.arc(x,y,r,sAngle,eAngle,counterclockwise);
x   圆的中心的 x 坐标。
y   圆的中心的 y 坐标。
r   圆的半径。
sAngle  起始角，以弧度计（弧的圆形的三点钟位置是 0 度）。
eAngle  结束角，以弧度计。
counterclockwise    可选。规定应该逆时针还是顺时针绘图。False = 顺时针，true = 逆时针。
```
【实例】
```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.beginPath();
ctx.arc(95,50,40,0,2*Math.PI);
ctx.stroke();
```

## Canvas文本
1. font - 定义字体
2. textAlign - textAlign 设置或返回文本内容的当前对齐方式。
3. textBaseline - 设置或返回在绘制文本时使用的当前文本基线。
4. fillText(text,x,y) - 在 canvas 上绘制实心的文本
5. strokeText(text,x,y) - 在 canvas 上绘制空心的文本

## textAlign
【语法】
```
context.textAlign="center|end|left|right|start";
start   默认。文本在指定的位置开始。
end     文本在指定的位置结束。
center  文本的中心被放置在指定的位置。
left    文本在指定的位置开始。
right   文本在指定的位置结束。
```
【实例】

```
ctx.textAlign="start"; 
ctx.fillText("textAlign=start",150,60); 
ctx.textAlign="end"; 
ctx.fillText("textAlign=end",150,80); 
ctx.textAlign="left"; 
ctx.fillText("textAlign=left",150,100);
ctx.textAlign="center"; 
ctx.fillText("textAlign=center",150,120); 
ctx.textAlign="right"; 
ctx.fillText("textAlign=right",150,140);
```

## textBaseline
【语法】
```
context.textBaseline="alphabetic|top|hanging|middle|ideographic|bottom";
alphabetic  默认。文本基线是普通的字母基线。
top         文本基线是 em 方框的顶端。
hanging     文本基线是悬挂基线。
middle      文本基线是 em 方框的正中。
ideographic 文本基线是表意基线。
bottom      文本基线是 em 方框的底端。
```
【实例】
```
ctx.textBaseline="top"; 
ctx.fillText("Top",5,100); 
ctx.textBaseline="bottom"; 
ctx.fillText("Bottom",50,100); 
ctx.textBaseline="middle"; 
ctx.fillText("Middle",120,100); 
ctx.textBaseline="alphabetic"; 
ctx.fillText("Alphabetic",190,100); 
ctx.textBaseline="hanging"; 
ctx.fillText("Hanging",290,100);
```
## fillText()

fillText() 方法在画布上绘制填色的文本。文本的默认颜色是黑色。

**提示：请使用 font 属性来定义字体和字号，并使用 fillStyle 属性以另一种颜色/渐变来渲染文本。**
【语法】

```
context.fillText(text,x,y,maxWidth);
text    规定在画布上输出的文本。
x   开始绘制文本的 x 坐标位置（相对于画布）。
y   开始绘制文本的 y 坐标位置（相对于画布）。
maxWidth    可选。允许的最大文本宽度，以像素计。
```

【实例】
```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");

ctx.font="20px Georgia";
ctx.fillText("Hello World!",10,50);

ctx.font="30px Verdana";
// Create gradient
var gradient=ctx.createLinearGradient(0,0,c.width,0);
gradient.addColorStop("0","magenta");
gradient.addColorStop("0.5","blue");
gradient.addColorStop("1.0","red");
// Fill with gradient
ctx.fillStyle=gradient;
ctx.fillText("Big smile!",10,90);
```

## strokeText()
【语法】
```
context.strokeText(text,x,y,maxWidth);
text    规定在画布上输出的文本。
x   开始绘制文本的 x 坐标位置（相对于画布）。
y   开始绘制文本的 y 坐标位置（相对于画布）。
maxWidth    可选。允许的最大文本宽度，以像素计。
```
strokeText() 方法在画布上绘制文本（无填充色）。文本的默认颜色是黑色。

提示：请使用 font 属性来定义字体和字号，并使用 strokeStyle 属性以另一种颜色/渐变来渲染文本。

【实例】
```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");

ctx.font="20px Georgia";
ctx.strokeText("Hello World!",10,50);

ctx.font="30px Verdana";
// Create gradient
var gradient=ctx.createLinearGradient(0,0,c.width,0);
gradient.addColorStop("0","magenta");
gradient.addColorStop("0.5","blue");
gradient.addColorStop("1.0","red");
// Fill with gradient
ctx.strokeStyle=gradient;
ctx.strokeText("Big smile!",10,90);
```
## measureText()
【语法】
```
context.measureText(text).width;
text    要测量的文本。
```
context.measureText(text).width;
text    要测量的文本。

【实例】
```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.font="30px Arial";
var txt="Hello World"
ctx.fillText("width:" + ctx.measureText(txt).width,10,50)
ctx.fillText(txt,10,100);
```

## canvas
1. createLinearGradient(x,y,x1,y1) - 创建线条渐变
2.  createRadialGradient(x,y,r,x1,y1,r1) - 创建一个径向/圆渐变

**createLinearGradient()实例**
```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");

// Create gradient
var grd=ctx.createLinearGradient(0,0,200,0);
grd.addColorStop(0,"red");
grd.addColorStop(1,"white");

// Fill with gradient
ctx.fillStyle=grd;
ctx.fillRect(10,10,150,80);
```
**createLinearGradient()实例**
```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");

// Create gradient
var grd=ctx.createRadialGradient(75,50,5,90,60,100);
grd.addColorStop(0,"red");
grd.addColorStop(1,"white");

// Fill with gradient
ctx.fillStyle=grd;
ctx.fillRect(10,10,150,80);
```

## Canvas图像

drawImage(image,x,y)

【实例】
```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
var img=document.getElementById("scream");
ctx.drawImage(img,10,10);
```
## isPointInPath() 方法
```
context.isPointInPath(x,y)
x   要测试的 x 坐标。
y   要测试的 y 坐标。

```
如果指定的点位于当前路径中，isPointInPath() 方法
返回 true，否则返回 false。

## scale()
```
context.scale(scalewidth,scaleheight);
scalewidth  缩放当前绘图的宽度（1=100%，0.5=50%，2=200%，依次类推）。
scaleheight 缩放当前绘图的高度（1=100%，0.5=50%，2=200%，依次类推）。
```
scale() 方法缩放当前绘图至更大或更小。

注意：如果您对绘图进行缩放，所有之后的绘图也会被缩放。定位也会被缩放。如果您 scale(2,2)，那么绘图将定位于距离画布左上角两倍远的位置。

**【实例】绘制一个矩形；放大到 200%，再次绘制矩形；放大到 200%，再次绘制矩形；放大到 200%，再次绘制矩形：**
```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.strokeRect(5,5,25,15);
ctx.scale(2,2);
ctx.strokeRect(5,5,25,15);
ctx.scale(2,2);
ctx.strokeRect(5,5,25,15);
ctx.scale(2,2);
ctx.strokeRect(5,5,25,15);
```
## rotate()
角度转换为弧度: degrees*Math.PI/180 

弧度转角度：rad * 180/Math.PI

注意：旋转只会影响到旋转完成后的绘图。


## translate()
```
context.translate(x,y);
x   添加到水平坐标（x）上的值。
y   添加到垂直坐标（y）上的值。

```
translate() 方法重新映射画布上的 (0,0) 位置。

注意：当您在 translate() 之后调用诸如 fillRect() 之类的方法时，值会添加到 x 和 y 坐标值上。

**【实例】在位置 (10,10) 处绘制一个矩形，将新的 (0,0) 位置设置为 (70,70)。再次绘制新的矩形（请注意现在矩形从位置 (80,80) 开始绘制）：**
```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.fillRect(10,10,100,50);
ctx.translate(70,70);
ctx.fillRect(10,10,100,50);
```

## transform()
```

context.transform(a, b, c, d, e, f) - 按指定的矩阵转换当前的用户坐标系。
a   水平缩放绘图。
b   水平倾斜绘图。
c   垂直倾斜绘图。
d   垂直缩放绘图。
e   水平移动绘图。
f   垂直移动绘图。

相当于：context.transform(M11, M12, M21, M22, OffsetX, OffsetY)
X = x * M11 + y * M12 + OffsetX
Y = x * M21 + y * M22 + OffsetY
```
- 位移。用transform来替代就是修改最后两个参数： ctx.transform(a,b,c,d,e,f) 其中的e和f两个参数。
- 旋转。旋转呢，就需要配合四个参数来实现了，ctx.transform(a,b,c,d,e,f)其中的abcd四个参数。
- 缩放。缩放仅需要修改其中两个参数即可，ctx.transform(a,b,c,d,e,f)其中的a和d两个参数;

## imageData

**createImageData()**

```
//以指定的尺寸（以像素计）创建新的 ImageData 对象：
var imgData=context.createImageData(width,height);
//创建与指定的另一个 ImageData 对象尺寸相同的新 ImageData对象（不会复制图像数据）：
var imgData=context.createImageData(imageData);

width   ImageData 对象的宽度，以像素计。
height  ImageData 对象的高度，以像素计。
imageData   另一个 ImageData 对象。
```
createImageData() 方法创建新的空白 ImageData 对象。新对象的默认像素值 transparent black。

对于 ImageData 对象中的每个像素，都存在着四方面的信息，即 RGBA 值：
R - 红色（0-255）G - 绿色（0-255）B - 蓝色（0-255）A - alpha 通道（0-255; 0 是透明的，255 是完全可见的）

因此 ，transparent black 表示 (0,0,0,0)。

color/alpha 信息以数组形式存在，并且由于数组包含了每个像素的四条信息，所以数组的大小是 ImageData 对象的四倍：widthheight4。（获得数组大小有更简单的办法，就是使用 ImageDataObject.data.length）

包含 color/alpha 信息的数组存储于 ImageData 对象的 data 属性中。

提示：在操作完成数组中的 color/alpha 信息之后，您可以使用 putImageData() 方法将图像数据拷贝回画布上。

## getImageData()
```
context.getImageData(x,y,width,height);
x   开始复制的左上角位置的 x 坐标（以像素计）。
y   开始复制的左上角位置的 y 坐标（以像素计）。
width   要复制的矩形区域的宽度。
height  要复制的矩形区域的高度。
```
getImageData() 方法返回 ImageData 对象，该对象拷贝了画布指定矩形的像素数据。

## putImageData()
```
context.putImageData(imgData,x,y,dirtyX,dirtyY,dirtyWidth,dirtyHeight);
imgData 规定要放回画布的 ImageData 对象。
x   ImageData 对象左上角的 x 坐标，以像素计。
y   ImageData 对象左上角的 y 坐标，以像素计。
dirtyX  可选。水平值（x），以像素计，在画布上放置图像的位置。
dirtyY  可选。垂直值（y），以像素计，在画布上放置图像的位置。
dirtyWidth  可选。在画布上绘制图像所使用的宽度。
dirtyHeight 可选。在画布上绘制图像所使用的高度。
```
putImageData() 方法将图像数据（从指定的 ImageData 对象）放回画布上。

【实例】复制
```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.fillStyle="red";
ctx.fillRect(10,10,50,50);
function copy()
{
    var imgData=ctx.getImageData(10,10,50,50);
    ctx.putImageData(imgData,10,70);
}
```

## globalAlpha
```
context.globalAlpha=number;
number  透明值。必须介于 0.0（完全透明） 与 1.0（不透明） 之间。
```
globalAlpha 属性设置或返回绘图的当前透明值（alpha 或 transparency）。

globalAlpha 属性值必须是介于 0.0（完全透明） 与 1.0（不透明） 之间的数字。

【实例】
```
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.fillStyle="red";
ctx.fillRect(20,20,75,50);
// Turn transparency on
ctx.globalAlpha=0.2;
ctx.fillStyle="blue"; 
ctx.fillRect(50,50,75,50); 
ctx.fillStyle="green"; 
ctx.fillRect(80,80,75,50);
```
## globalCompositeOperation
```
context.globalCompositeOperation="source-in";

值           描述

source-over 默认。在目标图像上显示源图像。
source-atop 在目标图像顶部显示源图像。源图像位于目标图像之外的部分是不可见的。
source-in   在目标图像中显示源图像。只有目标图像之内的源图像部分会显示，目标图像是透明的。
source-out  在目标图像之外显示源图像。只有目标图像之外的源图像部分会显示，目标图像是透明的。
destination-over    在源图像上显示目标图像。
destination-atop    在源图像顶部显示目标图像。目标图像位于源图像之外的部分是不可见的。
destination-in  在源图像中显示目标图像。只有源图像之内的目标图像部分会被显示，源图像是透明的。
destination-out 在源图像之外显示目标图像。只有源图像之外的目标图像部分会被显示，源图像是透明的。
lighter 显示源图像 + 目标图像。
copy    显示源图像。忽略目标图像。
xor 使用异或操作对源图像与目标图像进行组合。
```