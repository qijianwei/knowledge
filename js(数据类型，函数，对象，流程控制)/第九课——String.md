# 字符串
字符内容:字符序列和unicode
> 如果内容是有特殊含义的字符,需要通过\来进行转义描述,比如\n(换行)\r(回车换行),如果内容是一个unicode 编码,那么需要通过\u对应编码,来进行描述    
es2015新增字符串用``(1边上的)形式来表示

### 返回字符的编码
str.charCodeAt(str中指定的字符位置)

str.codePointAt 我们通过这个,返回字符真正的unicode码,es2015新增方法

string.fromCharCode(unicode) 
> 根据unicode来获取字符,不可以获取四个字节的

string.fromCodePoint


chatAt:获取指定位置字符

indexof

返回参数在str中首次出现的位置    
查找方向:从左到右

如果找不到的话,返回-1

