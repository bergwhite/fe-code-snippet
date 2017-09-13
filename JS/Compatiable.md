# 兼容性手册

CSS3大部分得IE9+才支持，以下大部分兼容性内容查询自[caniuse](http://caniuse.com/)

## 选择器

> getElementsByClassName（HTML5）

* IE9+ 支持

> document.querySelector()

* IE8 部分支持
* IE9+ 支持

> CSS2.1 选择器

* IE7+ 支持

```

Basic CSS selectors including: * (universal selector), > (child selector), :first-child, :link, :visited, :active, :hover, :focus, :lang(), + (adjacent sibling selector), [attr], [attr="val"], [attr~="val"], [attr|="bar"], .foo (class selector), #foo (id selector)

```

> CSS3 选择器

* IE7、IE8部分支持
* IE9+ 支持

```

IE7、IE8
--------------
General siblings (element1~element2) and Attribute selectors [attr^=val], [attr$=val], and [attr*=val]

IE9+
--------------
[foo^="bar"], [foo$="bar"], [foo*="bar"], :root, :nth-child(), :nth-last-child(), nth-of-type, nth-last-of-type(), :last-child, :first-of-type, :last-of-type, :only-child, :only-of-type, :empty, :target, :enabled, :disabled, :checked, :not(), ~ (general sibling)

```

## 布局

> CSS3媒体查询（Media Queries）

* IE9+ 支持

> flex（弹性盒子布局）

* IE10（-ms）、IE11 部分支持
* Edge12+
* Android 4.3-（-webkit-）
* Android 4.4
* UC11+ （-webkit-）

> column（分栏布局）

* IE10+
* Firefox、Chrome、Safari、Android 2.1+、UC、QQ、三星 部分支持

## DOM（文档对象模型）

> DOM2

* IE6+支持（以下属性）

```
className
createElement
createTextNode
getElementById
getElementsByTagName
nodeName

nodeType
nodeValue
tagName
hasChildNodes
parentNode

appendChild
cloneNode
insertBefore
removeChild
replaceChild
deleteData

insertData
normalize
replaceData
substringData
createAttribute

getAttribute
setAttribute
documentElement
ownerDocument
```

## 事件

> onclick

* 无兼容性问题，事件冒泡，重写会覆盖
* 阻止默认事件
	* return false;

> addEventListener(event.type, handle, boolean);

* IE8- 不支持
* 阻止默认事件
	* event.preventDefault();
* 阻止冒泡和捕获
	* event.stopPropagation();

> attachEvent(event.type, handle)

* IE6-8 支持
* 只支持冒泡
* 阻止默认事件
	* event.returnValue = false;
* 阻止冒泡
	* event.cancelBubble = true;

> new ActiveXObject('Microsoft.XMLHTTP')

* IE5.5

> 事件绑定

```

function addEvent(element, eType, handle, bol) {
    if(element.addEventListener){           //如果支持addEventListener
        element.addEventListener(eType, handle, bol);
    }else if(element.attachEvent){          //如果支持attachEvent
        element.attachEvent("on"+eType, handle);
    }else{                                  //否则使用兼容的onclick绑定
        element["on"+eType] = handle;
    }
}

```

> 解除绑定

```

function removeEvent(element, eType, handle, bol) {
    if(element.addEventListener){
        element.removeEventListener(eType, handle, bol);
    }else if(element.attachEvent){
        element.detachEvent("on"+eType, handle);
    }else{
        element["on"+eType] = null;
    }
}

```

参考

* [JS中的事件绑定，事件捕获，事件冒泡以及事件委托，兼容IE](http://www.cnblogs.com/zhangmingze/p/4864367.html)

## 异步

> XHR（XMLHttpRequest）

* IE7+ 支持
* IE5、IE6
	* new ActiveXObject("Microsoft.XMLHTTP")

```

xmlhttp=new XMLHttpRequest();

```

参考

* [XMLHttpRequest 对象 - W3School](http://www.w3school.com.cn/xml/xml_http.asp)

> Fetch

* IE 不支持
* Edge14+ 支持
* Safari10.1+ 支持
* ios Safari10.3+ 支持
* UC不支持

## 图片格式

> webp

* Chrome、Opera 支持
* Android 4、4.1 部分支持
* Android 4.3+ 支持
* UC11 支持
* 三星4 支持
* QQ 1.2支持

## 库

> Bootstrap

* BS2 支持 IE6 / 7 / 8
* BS3 支持 IE9+

> jQuery

* JQ1 支持 IE6 / 7 / 8
* JQ2 支持IE9+，在1的基础上删除了兼容代码
* JQ3 内核更改，部分老旧jq插件不兼

### jQuery

* 动态元素监听
	* $( document ).on( events, selector, data, handler );        // jQuery 1.7+