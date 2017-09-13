> 判断滚动条的方向

```

document.body.scrollTop  // 顶部距离
document.documentElement.scrollTop  // firefox
dom.offsetTop  // 顶部距离（某一元素）
document.documentElement.clientHeight  // 当前高度
document.documentElement.scrollHeight  // 完整高度

function getScrool() {
	var timeScroll = null
	var current = document.body.scrollTop
	window.onscroll = function() {
		clearTimeout(timeScroll)
		timeScroll =  setTimeout(function(){
			judge()  // 调用滚动方向判断函数
			lazyLoad()  // 调用懒加载
		},100)
	}
	function judge() {
		if(current-document.body.scrollTop>0){
			console.log('up')
		}
		else{
			console.log('down')
		}
		current = document.body.scrollTop
	}
}

```

参考

* [JS如何判断滚动条是否滚到底部 - 客齐齐](http://www.kqiqi.com/knowledge/program/1131.html)
* [JavaScript 节流函数 Throttle 详解 - 刘元涛](http://blog.csdn.net/u013510614/article/details/51920770)
* [浅谈javascript的函数节流 - AlloyTeam](http://www.alloyteam.com/2012/11/javascript-throttle/)

> 懒加载实现

把图片的地址存在自定义的data属性里，根据鼠标是否滚动到图片的位置，动态把data里的URL赋值给src属性。图片标签获得了src属性就会触发一个get请求，加载图片。

```

var image = {
  length: document.images.length,
  linkAll: document.images,
  linkIdCurrent: 0
}
function lazyLoad () {
  var bodyScrollTop = document.body.scrollTop
  var clientHeight = document.documentElement.clientHeight
  if ( image.linkIdCurrent < image.length ) {
    var currentScrollTop = image.linkAll[image.linkIdCurrent].offsetTop
    if ( currentScrollTop <= bodyScrollTop + clientHeight ) {
      var imgSrc = image.linkAll[image.linkIdCurrent].getAttribute('data-src')
      image.linkAll[image.linkIdCurrent].src = imgSrc
      image.linkAll[image.linkIdCurrent].removeAttribute('data-src')
      image.linkIdCurrent++
      lazyLoad()
    }
  }
}
lazyLoad()

```

参考

* [js获取页面元素距离浏览器工作区顶端的距离](http://www.cnblogs.com/qdphr/p/5798773.html)

> 文档模型

```

节点操作

createElement(name)  // 创建节点
appendChild(node)  // 添加节点
removeChild(node)  // 删除节点
dom.childNodes  // 节点列表

```

参考

* [DOM1](https://www.w3.org/TR/REC-DOM-Level-1/level-one-core.html)
* [DOM2 Core](https://www.w3.org/TR/2000/REC-DOM-Level-2-Core-20001113/core.html)
* [DOM1, DOM2, DOM3 - 第七城市](http://www.th7.cn/web/js/201511/133510.shtml)
* [关于DOM级别的一些问题](https://segmentfault.com/a/1190000000366311)
* [DOM动态添加HTML节点 appendChild、removeChild](http://blog.csdn.net/pan_junbiao/article/details/9262515)

> 等高布局

```

.parent {
  position: relative;  /* 相对布局 */
  height: 300px;
}
.parent * {
  position: absolute;  /* 和父元素的相对布局配合，可以使子元素基于父元素定位 */
  width: 200px;
  /* 设置顶部和底部都为0，等高布局形成 */
  top: 0;
  bottom: 0;
}

```

参考

* [CSS布局奇淫技巧之-多列等高](http://www.cnblogs.com/2050/archive/2012/07/31/2616460.html)
* [八种创建等高列布局](http://www.w3cplus.com/css/creaet-equal-height-columns)
* [网页上的摄影展:等高响应布局实现](http://www.cnblogs.com/zhangmingze/p/4864367.html)
* [Web页面中八种创建多列等高(等高列布局)的实现技术](http://www.jb51.net/css/68810.html)

> 清除浮动和BFC

* [清除浮动的三种方法](http://www.cnblogs.com/qiye2016/p/5868217.html)
* [BFC块级格式上下文](http://www.cnblogs.com/qiye2016/p/5880121.html)
* [CSS深入理解流体特性和BFC特性下多栏自适应布局](http://www.zhangxinxu.com/wordpress/2015/02/css-deep-understand-flow-bfc-column-two-auto-layout/)
* [前端精选文摘：BFC 神奇背后的原理](http://www.cnblogs.com/lhb25/p/inside-block-formatting-ontext.html)

> 属性操作

```

body.attributes  // 返回属性列表
getAttribute(name)  // 获取
setAttribute(name, value)  // 设置
removeAttribute(name)  // 删除

```

> 媒体查询的两种插入方式

```

@media only screen and (max-width:767px) {...}
<style media="only screen and (max-width:767px)">...</style>

```

参考

* [DOM自定义属性 getAttribute、setAttribute、removeAttribute](http://blog.csdn.net/pan_junbiao/article/details/9262637)

> 格式化JS对象成JSON

```

var obj = {
  a: 1,
  b: 2
}
var res = JSON.stringify(obj, null, '  ')
console.log(res)
/* 结果
"{
  "a": 1,
  "b": 2
 }"
*/

```