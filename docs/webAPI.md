# DOM

##    注册事件



* 点击事件 onclick

* 有光标的时候 onfocus

* 失去焦点时 onblur

* 多次注册事件 .addEventListenter('click',function() {

  * 例 btn.addEventListenter('click',function() {      });

* 鼠标的按键点下的时候触发 onmousedown

  * 例document.onmousemove = function(e) {   }

  * 例box.addEventListener("mouseup", function() {

        console.log(3);

      });

* 鼠标在某个元素身上移动的时候触发 onmousemove

* 鼠标的按键被松开的时候触发 onmouseup

##### 键盘事件onkeydown、onkeyup

```js
- 按键按下：keydown
- 按键弹起：keyup
text.onkeydown = function(e) {
   // console.log(e.keyCode, e.ctrlKey);
    // 判断是否同时按下ctrl和回车
    if (e.ctrlKey && e.keyCode === 13) {
    }
}
```

##### 鼠标移入，移出onmouseover、onmouseout

```js
box.onmouseover = function() {
    // 获取自定义属性
    this.getAttribute("index");
    // 添加节点对象属性，随便添加；
    console.log(this.a);
}

// 鼠标移除时触发
dom.onmouseout = function(){ 
}
```

##### 动画结束事件,帧动画结束事件

```js
//过渡结束时触发
var box = document.querySelector('.box');
box.addEventListener('transitionend',function(){
  console.log(123);
});
//帧动画结束时触发
var box = document.querySelector('.box');
box.addEventListener('animationend',function(){
  console.log(123);
})
```

* 注意：
  - 不能使用on的方式注册，只能使用addEventListener的方式注册
  - 如果帧动画是无限次的，不会触发该事件animationend

##    获取元素对象（DOM节点）

#####       根据DOM节点 获取 DOM节点

```js
父元素.children  //获取子元素：可以得到某个元素之下的所有的子元素的集合，一个**伪数组
元素.parentNode //获取父元素：返回一个；
元素.nextElementSibling  -  得到下一个兄弟元素
元素.previousElementSibling - 得到上一个兄弟元素
```

- 获取元素对象 选择器 !!!

```js
document.querySelector(css选择器);
// 作用：根据选择器获取所有满足条件的元素，这个使用的比较多；
// 参数：多个css选择器，以逗号隔开，都是字符串
// 返回值：伪数组；for，但是这个伪数组上面有forEach方法
document.querySelectorAll(css选择器1,css选择器2...);
```

- 根据**标签名**获取元素

  ```js
  document.getElementsByTagName(tagname);
  ```

- 根据元素**类名**获取元素

  ```js
  document.getElementsByClassName(classname);
  ```

- **元素对象的位置**：获取到的是数值

```js
// 得到的是某个元素距离他的offsetParent元素的水平距离
元素.offsetLeft     元素.offsetTop 
元素的offsetParent// 找到一个有定位的父亲元素进行参考，如果亲生父亲没有定位，会一直往上找，直到找打有定位的父亲，或者body；
```

##    操作属性

##### 修改节点

```js
ul.innerHTML = '<li>狗蛋</li>';   // 元素.innerHTML = '是满足html语法的标签结构';
innerText：获取和设置元素对象（DOM节点）的文本信息；
```

##### 自定义属性

```js
a: 元素.getAttribute(属性名)
// 作用： 根据属性名获取属性值   返回值：返回获取属性的值；
b: 元素.setAttribute(属性名,属性值) 
// 作用：添加或者修改属性的值  参数：都是字符串；
c: 元素.removeAttribute(属性名)
// 作用：删除某个属性
```

##### 标准属性-style

```js
// 获取：只能获取行内样式；
div.style.backgroundColor
// 设置
div.style.backgroundColor = "#fff";
```

##### 标准属性-style

```js
console.log(元素.className); // 正常输出元素的class属性
// 如果要修改类样式,会直接覆盖
box.className = '新的类名';
// 解决：在原来的基础上进行添加类名
box.className += '新的类名';
```

#####  属性 类样式对象-classList

```js
a:  box.classList.add("类名1","类名2"...)；
//add：给元素对象添加一个或者多个类名，不会影响原来的类名
// 参数：多个类名，之间用逗号隔开
b:  box.classList.remove("类名1","类名2"...)
//remove： 给元素删除一个或者多个类名
// 参数：多个类名，可以是多个，多个之间用逗号隔开
c:  box.classList.toggle("类名")
//toggle：切换类名，
// 参数： 要切换的类名
```

##### 鼠标位置属性

```js
// 页面坐标系  -  以body的左上角作为原点
事件对象.pageX
事件对象.pageY

// 可视区域坐标系 - 以浏览器的可视区域的左上角为原点的
// 可视区域：就是元素用来显示内容的区域
事件对象.clientX
事件对象.clientY

// 事件的目标对象，用户点击到谁上面了；用于事件委托；
事件对象.target

// 事件的绑定对象，就是是绑定在哪个DOM节点上 和 this一样
// 前面说的事件源，
e.currentTarget==this -----> true
```

##    方法

##### 插入到列表最前面

``` js
父元素.insertBefore(新的子元素,旧的子元素)
```

##### 删除节点

```js
// 父元素.removeChild(要删除的子元素);
var first = ul.children[0];
// 调用方法，移除
ul.removeChild(first);
```

##### 创建节点

```js
document.createElement('标签名');
// 返回值：一个元素对象 DOM节点；
// 注意：该方法创建的元素，是不会自动进入结构里面的，需要自己手动添加
document.write();//JS基础
```

```js
事件对象.stopPropagation();// 阻止冒泡
事件对象.preventDefault();// 阻止默认行为；

document.oncontextmenu = function(e){
  e.preventDefault();// 页面右键事件 查看右键菜单
}

// 阻止a标签转跳
// 1 把a标签的href属性设置为 javascript:void(0);
// 2 在a标签的点击事件里面，return false;
// 3 使用事件对象.preventDefault();
dom_a.addEventListener('click', function(e) {
    e.preventDefault();
});
```

# BOM

## 属性

##### 获取元素的实际宽度和高度

```js
// 返回值：数值；
元素.offsetWidth// 只能进行获取；元素的实际宽度 
元素.offsetHeight// 元素的实际高度

// 获取和设置
dom.style.width；
```



##### location

```js
// 如果想要使用js进行跳转，只需要 location.href = 新的地址;
location.href = 'http://www.jd.com';
```

##### localStorage和JSON

```js
一、localStorage:
// 存储： 后面的值 前面可以放入任何数据类型，保存后为字符串；
// 注意： 如果存储的是对象之类的复杂类型，需要先把复杂类型转换为的字符串，再存进去；
// 多次对一个键进行赋值，会把前面的值覆盖；
localStorage.setItem(键,值);

// 读取 数据
// 返回：我们存入的的数据的值，返回的是字符串；
localStorage.getItem(键);

// 删除键的值
localStorage.removeItem(键);　　

// 全部清空
localStorage.clear();　

二、JSON
// 将对象转换为json格式的字符串   返回值：一个满足json格式的 字符串
JSON.stringify(对象);

// 将json格式的字符串转换为对象  返回值：依赖于你的json格式字符串，可能返回数组，或者是对象....
JSON.parse(json格式字符串);
```

## 方法

#####  获取dom节点

```js
// Computed：计算后的样式
// 返回值： 当前作用在这个元素身上的所有样式的集合对象  BOM的方法；
// 属性：具体的属性 无论是行内的还是CSS样式设置的，都可以获取到；字符串
var res = window.getComputedStyle(元素对象)；
res.width 
```

#####   方法：onload

```js
window.onload = function(){
    // 想要获取图片的宽高，就需要等待图片加载完成后才执行后面的函数；
}
```

##### 定时器

```js
一次性定时器：
var timer = setTimout(函数,延迟的毫秒数);
// 作用： 延迟一定的毫秒之后，调用函数一次;
// 返回值： 是该定时器的id，id可以用于停止这个定时器
clearTimeout(timer);// 停止一次性的定时器：清除后，就不会执行这个定时器；
永久性定时器：
var timer = setInterval(函数,间隔);
// 作用：阶段的时间执行函数；
// 返回值：就是该定时器的id
clearInterval(timer);// 清除永久定时器


```

## 数组操作

###   Math

- Math.random 随机数

  var res = Math.random() 0~1的随机数，不包括1.

- Math.floor 向下取整

  一般配合Math.random使用

- Math.round 四舍五入

  var res = Math.round(3.5000001);
    // console.log(res);

- Math.abs 绝对值

  var res = Math.abs(40);
  console.log(res);
   var res = Math.abs(-40.4562);
   console.log(res);

  保留小数

- Math.max和Math.min

  最小值和最大值：
   var res = Math.max(10, 50, 999);
    console.log(res)

- Math.ceil 向上浮点取整

  Math.ceil(x)  把一个浮点数进行向上取整
  console.log(Math.ceil(3.1));  // 4

### Date

- new Date

  var date = new Date(); // 得到的是当前时间的日期对象

- 获取年月日时分秒

  配合 new Date使用：
  	console.log(date.getFullYear());// 年份
  console.log(date.getMonth()); // 月份，从0开始

  // 当前日 为什么不是getDay() 英语：日期date，day某天；
  console.log(date.getDate()); 

  console.log(date.getHours()); // 小时，0-23
  console.log(date.getMinutes()); // 分钟 ， 0-59
  console.log(date.getSeconds()); // 秒数 ， 0-59
  console.log(date.getMilliseconds()); // 毫秒 0-999 ， 1秒 = 1000毫秒

- 创建一个指定日期的对象

  // 给一个日期格式字符串var date = new Date('2019-01-01');// 分别传入年月日时分秒。注意传入的月份是从0开始算的var date = new Date(2019,0,1,12,33,12);

- 时间戳

  获取从1970年1月1日到现在的总毫秒数，常说的时间戳：
  var date = new Date();

  console.log(date.valueOf());
  console.log(date.getTime());
  console.log(1*date);

  console.log(Date.now());

### Array

- push 从数组后面添加一个元素

  push 从数组后面推入一个元素或多个元素：
  var arr = [1,2,3];// 返回：修改后数组的长度arr.push(4,5,6);

- pop 删除数组最后一个元素

  // 数组的pop方法用于将数组的最后一个元素移除
  var arr = [1,2,3];

  // 返回 被删除的元素；
  arr.pop();

- unshift 从数组前面添加一个或多个元素

  unshift 从数组前面添加一个或多个元素：
  var arr = [1,2,3];// 返回：修改后数组的长度arr.unshift(4,5,6);

- shift 用于将数组的第一个元素移除

  shift 用于将数组的第一个元素移除:
  // 数组的shift方法用于将数组的第一个元素移除var arr = [1,2,3];// 返回 被删除的元素；arr.shift();

- splice：可进行数组任何位置的增删改

  splice：可进行数组**任何位置**的增删改:
  	// 数组的splice方法用于从数组的指定位置移除、添加、替换元素
  var arr = ['a','b','c','d','e'];

  // 对原数组操作
  // 作用：从索引3开始移除，总共移除1个元素 ，
  // 返回 被移除数据的数组
  arr.splice(3,1); 
  console.log(arr);


  // 在c的后面添加7和8两个元素
  // 作用：从索引3开始添加，移除0个元素，把7，8加入；
  // 
  // 返回：一个空数组
  // 操作原数组；
  arr.splice(3,0,7,8); 

  

  // 作用：从索引1开始替换，总共替换1个，用0替换 ；
  // 返回：被替换元素的数组
  arr.splice(1,1,0);
  console.log(arr);

### 与字符串互转

- join 数组转字符串

  join 用于将数组中的多元素以指定分隔符连接成一个字符串：
  	var arr = ['刘备','关羽','张飞'];var str = arr.join('|'); console.log(str);  // 刘备|关羽|张飞

- split 字符串转数组

  split 字符串的方法：转数字，后面为分隔的字符：
  	// 这个方法用于将一个字符串以指定的符号分割成数组var str = '刘备|关羽|张飞';var arr = str.split('|');console.log(arr);

### 查找元素

- indexOf：根据元素查找索引

  indexOf：根据元素查找索引，如果这个元素在数组中，返回索引，否则返回-1，找元素在不在数组内部：
  	var arr = [10,20,30]
  console.log(arr.indexOf(30));  // 2
  console.log(arr.indexOf(40));  // -1

- findIndex方法用于查找满足条件的第一个元素的索引

  findIndex方法用于查找满足条件的第一个元素的索引，如果没有，则返回-1：
  	var arr = [10, 20, 30];
  var res1 = arr.findIndex(function (item) {
    return item >= 20;
  });
  // 返回 满足条件的第一个元素的的索引
  console.log(res1);  


  var res2 = arr.findIndex(function (item) {
    return item >= 50;
  });
  // -1
  console.log(res2);

### 遍历数组

- forEach：遍历数组

  // 数组的 forEach 方法用于遍历数组
  var arr_1 = [10,20,30,40,50];

  // forEach方法需要一个参数是一个函数，这个函数也接收3个参数，
  // item是数组中的每个元素，index是item的索引,arr表示当前数组；
  // 对本数组操作，没有返回值；
  arr_1.forEach(function(item,index,arr){
    console.log(item,index);
  });

- filter 筛选出数组中满足条件的数组

  filter 筛选出数组中满足条件的数组，**返回是一个新的数组；
  	// 数组的filter方法用于将数组中满足条件的元素筛选出来
  // 筛选出数组中 小于 2000 的数据
  var arr_1 = [1500,1800,2200,300,2600,800];
  var res = arr_1.filter(function(item,index,arr){
    return item < 2000;
  });
  // fitler方法的的参数要求是一个函数，这个函数接收2个参数：item是数组中的每个元素，index是item对应的索引,arr代表当前的数组

### 拼接与截取

- concat  拼接数组

  concat  拼接数组，**不改变原数组，创建新数组返回：
  	// 数组的concat方法的作用是把多个数组合并成一个新的数组
  var arr1 = [1,2,3];
  var arr2 = [4,5,6];
  var arr3 = [7,8,9];
  var res = arr1.concat(arr2,arr3);
  console.log(res);

  // 复制一个数组
  var arr_1 = arr.concat();

- slice 截取数组

  slice 截取数组：**不对原数组操作，返回的是新的数组；
  	var arr = ['a','b','c','d','e'];// 表示 从下标1（包括），截取到下标为4(不包括),var res = arr.slice(1, 4);// 如果不给第二个参数，默认就是把从start开始，到length结束的所有的元素截取var arr_1 = arr_2.slice(1);// 复制数组：如果省略两个参数，start默认是0，end默认是lengthvar arr_1 = arr_2.slice();

### 数组的复制

- 方法1 原始for循环

  var new_arr_1 = [];
    for (let index = 0; index < arr.length; index++) {
      new_arr_1[index] = arr[index];
    }

- 方法2  forEach 和push配合

  // forEach : 变量
    var new_arr_2 = [];
    arr.forEach(function(item, index) {
      new_arr_2.push(item);
    });

- 方法3  filter

  // 复制一个数组

  var arr_1 = arr_2.filter(function(item,index,arr){

    return item;

  });

- 方法4  concat

  var new_arr = arr.concat();

- 方法5  slice

  var new_arr = arr.slice();

- 对象复制

  var obj_1 = {    a:1,    b:2};
  var obj_2 = {}
  for(var key in obj_1)
  {  obj_2[key] = obj_1[key]}

### string 拼接与截取

- concat 拼接

  // 这个方法用于连接多个字符串，其作用相当于 + 操作符var res = "abc".concat('def','ghi');console.log(res);

- substring 截取字符串

  substring 截取字符串，不操作原字符串；返回截取出来的字符串；
  	/ 这个方法用于获取字符串中的部分字符
  var str = '我爱中华人民共和国';

  // 从索引2开始，到索引4结束，得到之间的字符，不包含索引4的字符
  var res = str.substring(2,4);
  console.log(res);

- slice 获取字符串中的部分

  // 这个方法用于获取字符串中的部分字符
  var str = '我爱中华人民共和国';
  var res = str.slice(2,4);// 从索引2开始，到索引4结束，得到之间的字符，不包含索引4的字符
  console.log(res);

  // 看起来和substring 没有啥区别，
  // slice()可以设置参数为负数，slice()方法在遇到负的参数的时候，会将这个负值与字符串的长度相加。
  console.log(str.slice(-6,7));

- substr  获取字符串中的部分

  // 这个方法用于获取字符串中的部分字符var str = '我爱中华人民共和国';var res = str.substr(2,2);// 索引2开始，总共获取2个字符，第二个参数为个数

*XMind: ZEN - Trial Version*