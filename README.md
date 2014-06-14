## 移动端web开发 疑难杂症大record ##

>**本文** 简单记录移动平台web开发过程中遇到的各种疑难杂症、莫名其妙的坑；仅做记录的考量，不纠结于成因原理性的东西。

### 1.移动web页上 textarea有渐变背景  ###
【Q】原以为是给textarea设置了box-shadow之类的问题 将其设为none也无效

【S】可对其设置如下样式：
`-webkit-appearance: none;`
##

### 2.JQuery用属性选择器取节点的问题 ###
【Q】用jquery的属性选择器去取节点(如：
`$('#tabs a[href='+param + ]')` ) 用ip访问不会出错 换做用域名访问 会出现取不到节点的情况。
页面上如：
```<ul id="tabs"><li><a href="#tab1"></li><li><a href="#tab2"></li></ul>```

【S】可能是因为换做域名后  href的值会被浏览器补充完整？... 换别的取节点方式
## 

### 3.改变手机上touch后高亮颜色  ###
`-webkit-tap-highlight-color`  手触摸后 高亮颜色
##

### To be continuing... ###