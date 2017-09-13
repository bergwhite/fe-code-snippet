触摸事件
三种在规范中列出并获得跨移动设备广泛实现的基本触摸事件：
1. touchstart ：手指放在一个DOM元素上。
2. touchmove ：手指拖曳一个DOM元素。
3. touchend ：手指从一个DOM元素上移开。
每个触摸事件都包括了三个触摸列表：

## x

1. touches ：当前位于屏幕上的所有手指的一个列表。
2. targetTouches ：位于当前DOM元素上的手指的一个列表。
3. changedTouches ：涉及当前事件的手指的一个列表。
例如，在一个touchend事件中，这就会是移开的手指。
这些列表由包含了触摸信息的对象组成：

## x

1. identifier ：一个数值，唯一标识触摸会话（touch session）中的当前手指。
2. target ：DOM元素，是动作所针对的目标。
3. 客户/页面/屏幕坐标 ：动作在屏幕上发生的位置。
4. 半径坐标和 rotationAngle ：画出大约相当于手指形状的椭圆形。

## x

1. touchenter ：移动的手指进入一个DOM元素。
2. toucheleave ：移动手指离开一个DOM元素。
3. touchcancel ：触摸被中断（实现规范）。

[From](http://blog.csdn.net/zhy421202048/article/details/53032395)