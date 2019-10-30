# jQuery

隐式迭代：内部自动遍历：
链式编程：能无限漫延；
优点：代码少，做的多；

## Day1

### jQuery  一个js库

jQuery 是一个快速、简洁的 JavaScript 库

​	JavaScript库：即 library，是一个封装好的特定的集合（方法和函数）。

​	学习jQuery本质： 就是学习调用这些函数（方法）。

### 入口函数

如果js要在head标签写的话，用jQuery,必须写入口函数，否则报错。
语法：1.$(function(){
		页面加载完成的入口。。。	js内容
})
			2.$(document).ready(function( ){
		页面加载完成的入口......js内容
			}

### $ jQuery 顶级对象

1.$ 是 jQuery 的别称，在代码中可以使用 jQuery 代替 ​$，但一般为了方便，通常都直接使用 $ 。

2.$ 是jQuery 的顶级对象， 相当于原生JavaScript中的 window。把元素利用​$包装成jQuery对象，就可以调用jQuery 的方法。

### jQuery 获取元素

语法：	$("选择器[元素]")	;
	注：js的对象只能用JS的属性和方法
Jq的对象只能用JQ的属性和方法

### jQuerey 和DOM相互转换

因为JQ只是封装JS部分功能，有时候还需要用JS的方法去操作，所以我们要转换：
DOM对象转化为jQuery对象：
	$(DOM对象)
jQuery对象转化为DOM对象:
 $("div")[index]   index是索引。
$("div").get(index) index是索引

### jQuery 选择器

所有的css 选择器
	$('#id')==》指定id元素
	​$('*')==》所有元素​
	$('.class')==》指定class元素
	$('div')==》根据标签获取元素​			   					
	$('div,p,li')==》获取多个
	​$('li.class')==>交集获取​
	$('ul>li')==>子代
	​$('ul li')==>后代
	注：一定要用引号包起来

### jQuery  筛选选择器

$('li:first')：第一个元素

$('li:last')：最后一个元素

$('li:eq(2)')==》索引为2【查找指定索引的元素】

$('li:odd')==》索引为奇数

$('li:even')==》索引为偶数

注意：索引是从0开始的

### 筛选方法！！！

父级元素: $("li").parent()
祖先$("li").parents("类名")
子级元素：$("li").children("li")，如果添加标签那么获取指定标签，如果没有指定就获取所有元素。
兄弟级元素：$('li').siblings("li");
后代级：$（“li”）.find("li"):
后边的 :  $( "li ").nextAll( );
前边的:   $("li").prevAll( );

### 操作css方法

参数只写属性名，则是返回属性值【$(this).css(''color'');】​参数是属性名，属性值，逗号分隔，是设置一组样式，属性必须加引号，值如果是数字可以不用跟单位和引号【$(this).css(''color'', ''red'');】​参数可以是对象形式，方便设置多组样式。属性名和属性值用冒号隔开， 属性可以不用加引号，【$(this).css({ "color":"white","font-size":"20px"});】​

### 设置类样式方法

作用等同于以前的 classList，可以操作类样式，注意操作类里面的参数不要加点
添加类【$(“div”).addClass(''current'');】

移除类【$(“div”).removeClass(''current'');】

切换类【$(“div”).toggleClass(''current'');】

原生 JS 中 className 会覆盖元素原先里面的类名。
jQuery 里面类操作只是对指定类进行操作，不影响原先的类名

### jQuery效果

- 显示隐藏效果

  show([speed,[easing],[fn]])hide([speed,[easing],[fn]])toggle([speed,[easing],[fn]])​​（1）参数都可以省略， 无动画直接显示。（2）speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。（3）easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。（4）fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。

- 滑动效果

  slideDown([speed,[easing],[fn]])slideUp([speed,[easing],[fn]])slideToggle([speed,[easing],[fn]])​​（1）参数都可以省略。（2）speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。（3）easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。（4）fn:  回调函数，在动画完成时执行的函数，每个元素执行一次

- 事件切换hover([over,]out)

  （1）over:鼠标移到元素上要触发的函数（相当于mouseenter）mouseenter==mouseover
  （2）out:鼠标移出元素要触发的函数（相当于mouseleave）mouseleave==mouseout
  （3）如果只写一个函数，则鼠标经过和离开都会触发它

- 动画队列及其停止排队方法

  动画或者效果一旦触发就会执行，如果多次触发，就造成多个动画或者效果排队执行。
  
  停止排队:stop()
  
  (1）stop() 方法用于停止动画或效果。
  (2)  注意： stop() 写到动画或者效果的前面， 相当于停止结束上一次的动画

- 淡入淡出效果

  fadeIn([speed,[easing],[fn]])fadeOut([speed,[easing],[fn]])fadeToggle([speed,[easing],[fn]])fadeTo([[speed],opacity,[easing],[fn]])【注意fadeTo必须写两个参数，speed和opacity】​​（1）参数都可以省略。（2）speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。（3）easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。（4）fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。

- 自定义动画animate

  语法：animate(params,[speed],[easing],[fn])​参数：（1）params: 想要更改的样式属性，以对象形式传递，必须写。 属性名可以不用带引号， 如果是复合属性则需要采取驼峰命名法 borderLeft。其余参数都可以省略。（2）speed：三种预定速度之一的字符串(“slow”,“normal”, or “fast”)或表示动画时长的毫秒数值(如：1000)。（3）easing：(Optional) 用来指定切换效果，默认是“swing”，可用参数“linear”。（4）fn:  回调函数，在动画完成时执行的函数，每个元素执行一次。
  自定义动画不能加在doucment文档上：

## day2

### jQuery  属性操作

固有属性：
语法：
$("元素").prop( 元素自身属性 );
一个值是获取，两个值设置，只能传一个值
自定义属性：
语法：
$("元素").attr( 元素自身属性 );
一个值是获取，两个值设置，只能传一个值
数据缓存data：
相当于给元素对象上挂属性，不显示但真实存在
	data(''name'',''value'')   向被选元素附加数据   所以元素上无法查看。一旦页面刷新，之前存放的数据都将被移除。
	$('span').data('spanindex',3);

console.log($('span').data('spanindex'));
--------------------------------------------
change事件，状态变化之后，发生事件
。
input事件用于文本框、文本域，输入后发生事件

### jQuery 内容文本值

html（）相当于原生js里的linnerHtml；
不设值是获取文本内容，设置是修改文本内容；
text( ) 相当于linnerText，不设值是获取文本内容，设置是修改文本内容；
以上大多用于双标签
=========================
val( )相当于value，用于表单属性；不设值是获取文本内容，设置是修改文本内容；
=========================
trim 去掉字符串里的空格；
$.trim("  hello, how are you?  ")
返回值：
"hello, how are you?"

### jQuery 遍历 each

jQuery 隐式迭代是对同一类元素做了同样的操作。如果想要给同一类元素做不同操作，就需要用到遍历。
		语法1：$("div").each(function(index, domEle) { xxx; }）
		语法2：$.each(object，function(index, element){ xxx;}）遍历数据
	 index 是每个元素的索引号;  element  遍历内容 
	element是一个文档对象，用时需要转换

### jQuery  创建  添加  删除元素

创建元素：
$("<li>我是新元素</li>")：
添加元素（内部）：
$("要添加的父元素").append 把内容放入匹配元素内部最后面，类似appendChild。]
	.prepend(''内容'') 把内容放入匹配元素内部最前面。
	内部添加元素，生成之后，它们是父子关系。
=========================
添加元素（外部）
element.after(''内容'') // 把内容放入目标元素后面
element.before(''内容'')    //  把内容放入目标元素前面 
=========================
element.remove()   //  删除匹配的元素（本身）
element.empty()    //  删除匹配的元素集合中所有的子节点
element.html('''')   //  清空匹配的元素内容

### jQuery尺寸

jQuery 尺寸：
	width()、height()【只算width和height】

innerWidth()、innerHeight()【包含padding+width】

outerWidth()、outerHeight()【包含padding、border、width】

outerWidth(true)、outerHeight(true)【包含padding、border、margin、width】

### jQuery 位置

offset()设置或获取元素偏移；
	1.offset() 方法设置或返回被选元素相对于文档的偏移坐标
	2.该方法有2个属性 left、top 。offset().top  用于获取距离文档顶部的距离，offset().left 用于获取距离文档左侧的距离。
	3.可以设置元素的偏移：offset({ top: 10, left: 30 });
position() 获取元素偏移
①①position() 方法用于返回被选元素相对于**带有定位的父级**偏移坐标，如果父级都没有定位，则以文档为准。

②该方法有2个属性 left、top。position().top 用于获取距离定位父级顶部的距离，position().left 用于获取距离定位父级左侧的距离。
注意：该方法只能获取
=========================
scrollTop()、scrollLeft()设置或获取元素被卷去的头部和左侧

①scrollTop() 方法设置或返回被选元素被卷去的头部。

②不跟参数是获取，参数为不带单位的数字则是设置被卷去的头部。

scroll事件

## day3

### jQurey 事件注册

语法：$(事件源).事件(function(){
			事件处理程序})
	其他事件和原生基本一致。

	比如mouseover、mouseout、blur、focus、														change、keydown、keyup、resize、scroll 等

### on（）绑定事件

on（）方法在匹配元素上绑定一个或多个事件的事件处理函数；
	语法； element.on（evebts，[selector],fn）
on() 方法优势1：
	1、可以绑定多个事件，多个处理事件处理程序。 
	不同处理程序： $(“div”).on({​
		  mouseover: function(){}
 			 mouseout: function(){},​ 
 					click: function(){}
							})
==================================
on() 方法优势2:
		可以事件委托。就是把原来加给子元素的事件绑定到父元素身上，就是把事件委托给父元素。
		：$('ul').on('click', 'li', function() {
  				 alert('hello world!');
			}); 
++++++++++++++++++++++++++++++++++
		on() 方法优势3：
		$(“div").on("click",”p”, function(){

​     alert("俺可以给动态生成的元素绑定事件")

 });

### off（） 解绑事件

off() 方法可以移除通过 on() 方法添加的事件处理程序：
		$("p").off() // 解绑p元素所有事件处理程序

$("p").off( "click")  // 解绑p元素上面的点击事件 后面的 foo 是侦听函数名

$("ul").off("click", "li");   // 解绑事件委托

### 自触发事件

有些事件希望自动触发，, 比如轮播图自动播放功能跟点击右侧按钮一致。可以利用定时器自动触发右侧按钮点击事件，不必鼠标点击触发：
	> element.click()  // 第一种简写形式

	> element.trigger("type")//第二种自动触发模式
	> element.triggerHandler(type)  // 第三种自动触发模式

> triggerHandler模式不会触发元素的默认行为，这是和前面两种的区别。

### 事件对象

事件触发就会有事件对象：
	element.on(events,[selector],function(event){})       
	阻止默认行为：event.preventDefault()   或者 return  false ​阻止冒泡： event.stopPropagation()

### jQuery 插件库

1.  jQuery 插件库  http://www.jq22.com/  
	 ​2.  jQuery 之家   http://www.htmleaf.com
图片懒加载或者（BOOTSTRAP插件）：
	1、要引入JQuery

​	2、插件JS【js引入文件和js调用必须写到 DOM元素（图片）最后面】

​	3、将图片 src 替换为 data-lazy-src

​	4、调用lazyLoadInit(）
----------------BOOTSTRAP插件

*XMind: ZEN - Trial Version*