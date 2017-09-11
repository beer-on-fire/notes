# CSS笔记整理 #


-	Q: css是否区分大小写？
 
	A: 
	-	不区分，html和css都对大小写不严格，但为了可读性而采用小写

----------

-	Q： 替换元素和非替换元素？

	A： 
	-	替换元素是浏览器根据其标签的元素与属性来判断显示具体的内容。如(X)HTML中的`<img>、<input>、<textarea>、<select>、<object>`都是替换元素，这些元素都没有实际的内容。
	-	(X)HTML 的大多数元素是不可替换元素，他们将内容直接告诉浏览器，将其显示出来。比如`<p>、<div>`

----------

-	Q: 	设置`p`的`font-size:10rem`，当用户重置或拖曳浏览器窗口时，文本大小是否会也随着变化？
	
	A: 
	-	不会，`rem`是以`html`根元素中`font-size`的大小为基准的相对度量单位，文本的大小不会随着窗口的大小改变而改变。	


----------

-	Q： 伪类选择器`:checked`将作用与`input`类型为`radio`或者`checkbox`,不会作用于`option`

	A:
	-	不对。


----------

> :root选择器用匹配文档的根元素。在HTML中根元素始终是HTML元素。

----------

-	Q:`translate()`方法能移动一个元素在z轴上的位置？

    A: 
	-	不能。`translate()`方法只能改变x轴，y轴上的位移。

----------

-	Q:  `only` 选择器的作用是？

    A：
	-	停止旧版本浏览器解析选择器的其余部分。

    -	only 用来指定某种特定的媒体类型，可以用来排除不支持媒体查询的浏览器。其实only很多时候是用来对那些不支持Media Query 但却支持Media Type 的设备隐藏样式表的。其主要有：支持媒体特性（Media Queries）的设备，正常调用样式，此时就当only 不存在；对于不支持媒体特性(Media Queries)但又支持媒体类型(Media Type)的设备，这样就会不读了样式，因为其先读only 而不是screen；另外不支持Media Qqueries 的浏览器，不论是否支持only，样式都不会被采用。
  
-----------

-	Q: `overflow:hidden` 是否形成新的块级格式化上下文？
	
    A：
	-	会形成。
	-	BFC:如果一个元素符合了成为BFC的条件，该元素内部元素的布局和定位就和外部元素互不影响(除非内部的盒子建立了新的 BFC)，是一个隔离了的独立容器。

   > 会触发BFC的条件有：

    - float的值不为none。
    - overflow的值不为visible。
    - display的值为table-cell, table-caption, inline-block 中的任何一个。
    - position的值不为relative 和static。
   
-----------

-	Q: `screen`关键词是指设备物理屏幕的大小还是指浏览器的视窗？

    A: 
	-	浏览器视窗

-----------

#TIPS:
> 浏览器CSS匹配顺序：

-    浏览器CSS匹配不是从左到右进行查找，而是从右到左进行查找。比如`#divBox p span.red{color:red;}`，浏览器的查找顺序如下：先查找html中所有class='red'的span元素，找到后，再查找其父辈元素中是否有p元素，再判断p的父元素中是否有id为divBox的div元素，如果都存在则匹配上。浏览器从右到左进行查找的好处是为了尽早过滤掉一些无关的样式规则和元素。

> `display:none` 和`visibilty:hidden`的区别：

-    `display:none`和`visibility:hidden`都是把网页上某个元素隐藏起来的功能，但两者有所区别，使用`visibility:hidden`属性会使对象不可见，而 `display:none`属性会使这个对象彻底消失,不占高度。


---------------
#以往笔记

### box-sizing 盒模型设置
    -   border-box 设置为怪异盒模型
	-   content-box 设置为标准盒模型

### 属性选择器
    -   E [attr] 找到所有具有attr属性的E类型元素
    -   E [attr="value"] 找到所有具有attr属性的E类型元素,并且属性名为Value
    -   E [attr ~ ="value"] 找到所有具有attr属性的E类型元素，并且属性为Value（指定属性名，并且具有属性值，此属性值是一个词列表，并且以空格隔开，其中词列表中包含了一个value词，而且等号前面的“〜”不能不写）
    -   E [attr ^="value"] 指定了属性名，并且有属性值，属性值是以Value开头的
    -   E [attr $="value"] 属性值以value结束的
    -   E [attr *="value"] 属性值中包含了value
    -   E [attr |="value"] 属性值是以value或者value- 开头的值，（比如说zh-cn）

### 结构选择器
    -   .p + h3 找到.p的下一个兄弟元素，并且是h3元素
    -   .p ~ h3 找到.p后面所有的h3标签
    -   :target 表示当前的URL片段的元素类型，这个元素必须是E
    -   ::selection 设置文本选中的背景和文字颜色 
    -   :not(.p) 排除class为p的元素

## 选择器
    -   E:nth-child()：E元素父级下的第几个子元素,并且元素的类型还得是E，支持odd（奇数）
even（偶数）    如： p:nth-child(4) p标签父级下的第4个子元素 ，并且标签类型还得是p标签
    -   > ：只找第一层子元素，如：
       
    -   *或者空格： 所有元素下第四个子级   
    
    -   E:nth-of-type() 找到E元素父级下的第几个E类型的元素，也支持even 、odd
       
    -   E:only-child E元素是他的父级下唯一的子元素
    
    -   E:empty E元素是个空标签
    
    -   :first-letter 文本第一个字

    -   :first-line 文本第一行


## Media Query 媒体查询
    -  媒询 设置了媒体类型之后，那只有在对应的媒体下，媒询中的样式才会被解析
    
    
###  媒体类型
        -   all 所有媒体
		-	braille 盲文触觉设备
		-	embossed 盲文打印机
		-	handheld 手持设备
		-	print 打印预览 
		-	projection 投影设备
		-	screen 彩屏设备
		-	speech '听觉'类似的媒体类型
		-	tty 不适用像素的设备
		-	tv  电视
		
###  关键字
		-	only 只有
		-	not 排除
		-	and 连接媒体类型和媒体特征
		
###  媒体特性:(min) (max)
		-	width
		-	divice-width
		-	orientation     (landscape横屏样式||portrait竖屏样式 )
		-	device-aspect-ratio             (高宽比:device-aspect-ratio:16/10)
            常见高宽比:
            			4/3
            			16/9
            			16/10

###  写法：
        
```
	-   `<link rel="stylesheet" type="text/css" href="index.css" media="">`
		
	-   @media {}

	-   @import url() 媒询条件;
```

```
	`@media all and (min-width:400px) and (max-width: 600px)  {}`
    所有的设备，宽度大于等于400px并且宽度小于等于600px的时候，识别其中的样式
```

###  meta标签
    

```
	<meta name="viewport" content="width=device-width, initial-scale=1">
```

###  屏幕大小
        -   超小屏幕
                手机 (<768px) xs
        -   小屏幕
                平板 (≥768px) sm
        -   中等屏幕
                桌面 (≥992px) md
        -   大屏幕
                桌面 (≥1200px) lg
                
                
==栅格布局，设置小尺寸之后，大尺寸会自动继承,设置了大尺寸之后，在小尺寸下样式会无效==

###  列偏移 
    
    ```
        col-xs-offset-n
    	col-sm-offset-n
    	col-md-offset-n
    	col-lg-offset-n
    ```
-----------
## 老版本弹性盒模型
    -   display:box;   
    -   display:inline-box;
    1.     老版本在使用时需要加前缀
    2.     块级子元素会在一行显示

###  box-orient  
        定义主轴方向
    -   horizontal水平
    -   vertical垂直
    
###  box-direction
        定义元素的排列顺序
    -   normal  左到右
    -   reverse 倒序
    
###  box-pack
        主轴方向富裕空间管理
    -   start
    -   end
    -   center
    -   justify
    
###  box-align
        侧轴（垂直于主轴方向）方向富裕空间管理
    -   start
    -   end
    -   center
    
###  box-flex
        定义子元素的弹性尺寸
    -   元素的尺寸 = box-flex
    -   元素的尺寸 = 元素的box-flex/所有元素的box-flex之和 * 父级的剩余空间;
	-   剩余空间 = 元素的总宽度 - 固定宽度的内容的宽度
    

    
###  box-ordinal-group
        定义子元素的排列顺序
1.     最小值1
2.     默认值大小为1
3.     数值越大排列越靠后
  
==**box的子元素不会自己换行**==



## display:flex(box的进化版)
    -       内嵌元素也支持宽高


###  flex-direction:
        主轴方向设置
    
    -   row 从左到右
    -   row-reverse 从右到左
    -   column 从左到右
    -   column-reverse 从右到左
    
    
###  justify-content:
        主轴对齐（主轴方向富裕空间管理）
        
    -   flex-start
    -   flex-end
    -   center
    -   space-between
    -   space-around
    
    
###  align-items:
        侧轴对齐（默认上到下、左到右）
        
    -   flex-start
    -   flex-end
    -   center
    
###  flex-wrap:
        换行
        
    -   nowrap 不换行（默认）
    -   wrap 换行
    -   wrap-reverse 反向换行
    
###  align-content
        行对齐
     
    -   flex-start
    -   flex-end
    -   center
    -   space-between
    -   space-around   
    
###  flex-flow: flex-direction flex-wrap;
        复合样式
        
        
###  flex:
    -   number
    -   auto
    -   none
    ==加给子级==
    元素的尺寸 = 元素的flex/flex之和 * 父级的宽度
    
###  order
        排序（数值越大，越往后排）
    ==加给子级==  
    默认值0，可接受负值
    


###  align-self
        对齐自身
        
    -   flex-start
    -   flex-end
    -   center

----------------------
## 布局容器 
    -   所有的内容都是放在布局容器中
    -   写栅格布局的时候，一定先写row，然后在row添加col
    -   1200 container 1170   
	    992  container 970
	    768  container 750
	    <768
	    
## 伪元素：
	-   after 在元素内容的末尾添加一块内容
	-   before 在元素内容的开始添加一块内容

	-   after 和 before要添加的内容写在content里,而且after和before必须有content	
	
##  考虑所有设备
	常见分辨率:
	-	1400以上(4k屏，高清屏)
	-	1366和1280 常规电脑
	-	1024 (平板横屏和老版本电脑)
	-	800和768 (平板竖屏和电脑的最小分辨率)
	-	480 手机横屏
	-	414 375 360 320 (手机) 
		
		

    -	1024或1280的电脑页面
    -	768的平板页面
    -	768一下的手机页面(通常做成自适应宽度)

    -   1400以上(4k屏，高清屏)
    -   1366和1280 常规电脑
    -   1024 (平板横屏和老版本电脑)
    
    
##  第一种写法：
    - 第一套样式写三种屏幕下通用的样式
	   


```
 <link rel="stylesheet" href="">
```


    - 第二套样式写屏幕宽度小于768的时候的样式，也就是手机
	   
```
 <link rel="stylesheet" media="(max-width:767px)" href="indexA.css">
```

	
    - 第三套样式写屏幕宽度小于1024大于等于768的时候的样式，也就是平板的竖屏
	   
```
 <link rel="stylesheet" media="(min-width:768px) and (max-width:1023px)" href="indexB.css">
```


	- 第四套样式写屏幕宽度大于等于1024的时候的样式，也就是平板的横屏和电脑
	  
```
  <link rel="stylesheet" media="(min-width:1024px)" href="indexC.css">
```

		
==注意这种写法写出来的内容，ABC三套样式不存同时被引入的情况，所有三套样式之间没有任何关系,所以在书写书序上，可以随意的写==


##  第二种写法：
    -   写通用样式，以及屏幕宽度小于768的样式
	       
```
 <link rel="stylesheet" href="indexA.css">
```

	-   屏幕大于等于768的时候引入
	        
```
 <link rel="stylesheet" media="(min-width:768px)" href="indexB.css">
```

	- 屏幕大于等于1024的时候引入
	        
```
<link rel="stylesheet" media="(min-width:1024px)" href="indexC.css">
```


    -	1. 所有屏幕下都会引入indexA
	-   2. 屏幕宽度大于等于768的时候，会引入indexA,indexB
	-   3. 屏幕宽度大于等于1024的时候，会引入indexA,indexB,indexC

==先写最小屏的，当屏幕宽度变宽的时候,会引入大屏下的样式表，同时小屏下的样式表也会被引入进来,我们只需要在大屏样式表中覆盖添加和小屏不一致的样式,所以有明确的先后顺序，先写小屏，再写大屏==


## 第三种写法：

    -   写通用样式，以及屏幕宽度大于等于1024的样式 
	
```
<link rel="stylesheet" href="indexA.css">
```

	-   屏幕宽度小于1024-->
	
```
<link rel="stylesheet" media="(max-width:1023px)" href="indexB.css">
```

	-   屏幕宽度小于768
	
```
<link rel="stylesheet" media="(max-width:767px)" href="indexC.css">
```

	-	1. 所有屏幕下都会引入indexA
	-	2. 屏幕宽度小于1024的时候，会引入indexA,indexB
	-	3. 屏幕宽度小于768的时候，会引入indexA,indexB,indexC

==先写最大屏的，当屏幕宽度变小的时候,会引入下屏下的样式表，同时大屏下的样式表也会被引入进来,我们只需要在小屏样式表中覆盖添加和大屏不一致的样式,所以有明确的先后顺序，先写大屏，再写小屏==

---------------
# 3D变换

##  transform:
		-	rotate 旋转
		-	skew 斜切
		-	scale 缩放
		-	translate 位移

## 	transform-origin 设置变换的原点
	    -transform-origin: center center 0;

	==后写先执行，rotate,skew,scale都是围绕着origin点进行的,而**位移不受origin点影响**==
	
## box-reflect 倒影
		-	*(webkit 私有样式)*
		-	above | below | left | right
		-	距离(可选项)
		-	渐变(可选项)
		

		
## rotate
		-	rotateX
		-	rotateY
		-	rotateZ
		-	rotate3d

		

## scale
		-	scaleX
		-	scaleY
		-	scaleZ
		-	scaleX3d
		


## skew
		-	skewX
		-	skewY

		
## translate
		-	translateX
		-	translateY
		-	translateZ
		-	translate3d


## perspective 景深(透视)

		当前我们的视线和变换元素之间的距离
		==景深加给变换元素的父级==
		
## transform-style:(3d空间,元素在做3D变换的时候，是否保留子元素的3D变换)  
	-	flat(默认值) 平面空间 不保留子元素的3d效果
	-	preserve-3d 3D空间 保留子元素的3d效果
	-	父级有3D变换，子元素也有时，一定要加给父级



##  backface-visibility:hidden;
    -   隐藏背面(背面，角度和父级的角度相对的面，叫背面)
    -   样式加给组成盒子的面
	
## perspective-origin 景深原点(center center) 视线方向


    -   正N边形外角和 = 360
	-	正N边形外角 = 360/N;
	-	(180 - 正N边形外角)/2
	-	正切：Math.tan();
	-	直角三角形，对边和临边的比值
	
