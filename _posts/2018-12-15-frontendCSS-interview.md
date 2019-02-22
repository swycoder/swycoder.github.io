---
title: Frontend CSS interview
excerpt: |
   Frontend interview
category:  Frontend interview
feature_image: "https://picsum.photos/2560/600?image=872"
---
####介绍一下标准的CSS的盒子模型？低版本IE的盒子模型有什么不同的？
CSS盒子模型又称框模型 (Box Model) ，包含了元素内容（content）、内边距（padding）、边框（border）、外边距（margin）几个要素。
区  别： IE的content部分把 border 和 padding计算了进去;
####CSS选择符有哪些？哪些属性可以继承？

  *   1.id选择器（ # myid）
  	2.类选择器（.myclassname）
  	3.标签选择器（div, h1, p）
  	4.相邻选择器（h1 + p）
  	5.子选择器（ul > li）
  	6.后代选择器（li a）
  	7.通配符选择器（ * ）
  	8.属性选择器（a[rel = "external"]）
  	9.伪类选择器（a:hover, li:nth-child）

  *   可继承的样式： font-size font-family color, UL LI DL DD DT;

  *   不可继承的样式：border padding margin width height ;
####CSS优先级算法如何计算？

  *   优先级就近原则，同权重情况下样式定义最近者为准;
  *   载入样式以最后载入的定位为准;

  优先级为:
  	同权重: 内联样式表（标签内部）> 嵌入样式表（当前文件中）> 外部样式表（外部文件中）。
  	!important >  id > class > tag
  	important 比 内联优先级高（IE6不认识!important的优先级）
####CSS3新增伪类有那些？

  	举例：
  	p:first-of-type	选择属于其父元素的首个 <p> 元素的每个 <p> 元素。
  	p:last-of-type	选择属于其父元素的最后 <p> 元素的每个 <p> 元素。
      p:only-of-type	选择属于其父元素唯一的 <p> 元素的每个 <p> 元素。
  	p:only-child		选择属于其父元素的唯一子元素的每个 <p> 元素。
  	p:nth-child(2)	选择属于其父元素的第二个子元素的每个 <p> 元素。

  	::after			在元素之前添加内容,也可以用来做清除浮动。
  	::before			在元素之后添加内容
      :enabled  		
  	:disabled 		控制表单控件的禁用状态。
  	:checked        单选框或复选框被选中。
####如何居中div？

水平居中：给div设置一个宽度，然后添加margin:0 auto属性

```
div{
 	width:200px;
 	margin:0 auto;
  }```
让绝对定位的div居中
```
 div {
 	position: absolute;
 	width: 300px;
 	height: 300px;
 	margin: auto;
 	top: 0;
 	left: 0;
 	bottom: 0;
 	right: 0;
 	background-color: pink;	/* 方便看效果 */
 }
 ```
水平垂直居中一

 确定容器的宽高 宽500 高 300 的层
 设置层的外边距
```
 div {
 	position: relative;		/* 相对定位或绝对定位均可 */
 	width:500px;
 	height:300px;
 	top: 50%;
 	left: 50%;
 	margin: -150px 0 0 -250px;     	/* 外边距为自身宽高的一半 */
 	background-color: pink;	 	/* 方便看效果 */

  }
```
水平垂直居中二

 未知容器的宽高，利用 `transform` 属性
```
 div {
 	position: absolute;		/* 相对定位或绝对定位均可 */
 	width:500px;
 	height:300px;
 	top: 50%;
 	left: 50%;
 	transform: translate(-50%, -50%);
 	background-color: pink;	 	/* 方便看效果 */

 }
```
水平垂直居中三

 利用 flex 布局
 实际使用时应考虑兼容性
```
 .container {
 	display: flex;
 	align-items: center; 		/* 垂直居中 */
 	justify-content: center;	/* 水平居中 */

 }
 .container div {
 	width: 100px;
 	height: 100px;
 	background-color: pink;		/* 方便看效果 */
 }  
```
####flex布局的justify-content属性和align-items，align-self属性
```
justify-content（在父元素设置），设置弹性盒子元素在主轴（横轴）的对齐方式。
取值：
justify-content: flex-start | flex-end | center | space-between | space-around;

flex-start: 弹性盒子元素将向行起始位置对齐。第一个元素与左起始边界对齐，后面的元素接着第一个元素进行排列。
flex-end: 弹性盒子元素将向行结束位置对齐。整体靠着行结束的位置排列。
center：整体居中显示。
space-between: 弹性盒子元素均匀分布。第一个元素的边界与行的主起始位置的边界对齐，同时最后一个元素的边界与行的主结束位置的边距对齐，而剩余的伸缩盒项目则平均分布，并确保两两之间的空白空间相等。
space-around: 弹性盒子元素均匀分布。两端保留子元素与子元素之间间距大小的一半。

align-items, align-self 
设置弹性盒子元素在垂直方向上（纵轴）的对齐方式。其中align-items属性用于弹性容器，而align-self用于弹性项目。

align-items: flex-start | flex-end | center | baseline | stretch;
align-self: auto | flex-start | flex-end | center | baseline | stretch;
```
####display有哪些值？说明他们的作用。

    block       	块类型。默认宽度为父元素宽度，可设置宽高，换行显示。
    none        	元素不显示，并从文档流中移除。
    inline      	行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。
    inline-block  默认宽度为内容宽度，可以设置宽高，同行显示。
    list-item   	象块类型元素一样显示，并添加样式列表标记。
    table       	此元素会作为块级表格来显示。
    inherit     	规定应该从父元素继承 display 属性的值。
####position的值relative和absolute定位原点是？

    absolute
  	生成绝对定位的元素，相对于值不为 static的第一个父元素进行定位。
    fixed （老IE不支持）
  	生成绝对定位的元素，相对于浏览器窗口进行定位。
    relative
  	生成相对定位的元素，相对于其正常位置进行定位。
    static
  	默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right z-index 声明）。
    inherit
  	规定从父元素继承 position 属性的值。
####CSS3有哪些新特性？

    新增各种CSS选择器	（: not(.input)：所有 class 不是“input”的节点）
    圆角		    （border-radius:8px）
    多列布局	    （multi-column layout）
    阴影和反射	（Shadow\Reflect）
    文字特效		（text-shadow、）
    文字渲染		（Text-decoration）
    线性渐变		（gradient）
    旋转		 	（transform）
    缩放,定位,倾斜,动画,多背景
    例如:transform:\scale(0.85,0.90)\ translate(0px,-30px)\ skew(-9deg,0deg)\Animation:
####请解释一下CSS3的Flexbox（弹性盒布局模型）,以及适用场景？

   一个用于页面布局的全新CSS3功能，Flexbox可以把列表放在同一个方向（从上到下排列，从左到右），并让列表能延伸到占用可用的空间。
   较为复杂的布局还可以通过嵌套一个伸缩容器（flex container）来实现。
   采用Flex布局的元素，称为Flex容器（flex container），简称"容器"。
   它的所有子元素自动成为容器成员，称为Flex项目（flex item），简称"项目"。
   常规布局是基于块和内联流方向，而Flex布局是基于flex-flow流可以很方便的用来做局中，能对不同屏幕大小自适应。
   在布局上有了比以前更加灵活的空间。
####用纯CSS创建一个三角形的原理是什么？
```
  把上、左、右三条边隐藏掉（颜色设为 transparent）
  demo {
    width: 0;
    height: 0;
    border-width: 20px;
    border-style: solid;
    border-color: transparent transparent red transparent;
  }
```
####一个满屏 品 字布局 如何设计?

  简单的方式：
  	上面的div宽100%，
  	下面的两个div分别宽50%，
  	然后用float或者inline使其不换行即可
####css多列等高如何实现？
方法一：
  利用padding-bottom|margin-bottom正负值相抵；
  设置父容器设置超出隐藏（overflow:hidden），这样子父容器的高度就还是它里面的列没有设定padding-bottom时的高度，
  当它里面的任 一列高度增加了，则父容器的高度被撑到里面最高那列的高度，
  其他比这列矮的列会用它们的padding-bottom补偿这部分高度差。
其他方法：https://www.cnblogs.com/kasmine/p/6498577.html
####CSS flex 属性
flex 属性用于设置或检索弹性盒模型对象的子元素如何分配空间。
flex 属性是 flex-grow、flex-shrink 和 flex-basis 属性的简写属性。flex 的默认值是以上三个属性值的组合。假设以上三个属性同样取默认值，则 flex 的默认值是 0 1 auto
注意：如果元素不是弹性盒模型对象的子元素，则 flex 属性不起作用。
```
flex-grow	一个数字，规定项目将相对于其他灵活的项目进行扩展的量。
flex-shrink	一个数字，规定项目将相对于其他灵活的项目进行收缩的量。
flex-basis	项目的长度。合法值："auto"、"inherit" 或一个后跟 "%"、"px"、"em" 或任何其他长度单位的数字。
auto	与 1 1 auto 相同。
none	与 0 0 auto 相同。
initial	设置该属性为它的默认值，即为 0 1 auto。
inherit	从父元素继承该属性。
```
当 flex 取值为一个非负数字，则该数字为 flex-grow 值，flex-shrink 取 1，flex-basis 取 0%。
当 flex 取值为一个长度或百分比，则视为 flex-basis 值，flex-grow 取 1，flex-shrink 取 1（注意 0% 是一个百分比而不是一个非负数字）。
当 flex 取值为两个非负数字，则分别视为 flex-grow 和 flex-shrink 的值，flex-basis 取 0%。
当 flex 取值为一个非负数字和一个长度或百分比，则分别视为 flex-grow 和 flex-basis 的值，flex-shrink 取 1。
详见：https://blog.csdn.net/fengyjch/article/details/79047908

#####实例
让所有弹性盒模型对象的子元素都有相同的长度，且忽略它们内部的内容：
```
<div class="container">
    <div class="left">多列等高布局左<br/>多列等高布局左</div> 
<div class="right">多列等高布局右</div>
</div>

<style>
 .container{
  display:flex;
}
.left,.right{
  flex:1;
}
.left{
  background:pink;
}
.right{
  background:green;
}
</style>
```
####经常遇到的浏览器的兼容性有哪些？原因，解决方法是什么，常用hack的技巧 ？

  * png24位的图片在iE6浏览器上出现背景，解决方案是做成PNG8.

  * 浏览器默认的margin和padding不同。解决方案是加一个全局的*{margin:0;padding:0;}来统一。

  * IE6双边距bug:块属性标签float后，又有横行的margin情况下，在ie6显示margin比设置的大。

    浮动ie产生的双倍距离 #box{ float:left; width:10px; margin:0 0 0 100px;}

    这种情况之下IE会产生20px的距离，解决方案是在float的标签样式控制中加入 ——_display:inline;将其转化为行内属性。(_这个符号只有ie6会识别)

#####渐进识别的方式，从总体中逐渐排除局部。

    首先，巧妙的使用“\9”这一标记，将IE游览器从所有情况中分离出来。
    接着，再次使用“+”将IE8和IE7、IE6分离开来，这样IE8已经独立识别。

    css
        .bb{
            background-color:red;/*所有识别*/
  	      background-color:#00deff\9; /*IE6、7、8识别*/
  	      +background-color:#a200ff;/*IE6、7识别*/
  	      _background-color:#1e0bd1;/*IE6识别*/
        }


  *  IE下,可以使用获取常规属性的方法来获取自定义属性,
     也可以使用getAttribute()获取自定义属性;
     Firefox下,只能使用getAttribute()获取自定义属性。
     解决方法:统一通过getAttribute()获取自定义属性。

####什么是CSS Hack？
CSS hack是通过在CSS样式中加入一些特殊的符号，让不同的浏览器识别不同的符号（什么样的浏览器识别什么样的符号是有标准的，CSS hack就是让你记住这个标准），以达到应用不同的CSS样式的目的。CSS hack的目的就是使你的CSS代码兼容不同的浏览器。当然，我们也可以反过来利用CSS hack为不同版本的浏览器定制编写不同的CSS效果。
CSS Hack常见的有三种形式：
CSS属性Hack、CSS选择符Hack以及IE条件注释Hack， Hack主要针对IE浏览器。

1、属性级Hack：比如IE6能识别下划线“_”和星号“*”，IE7能识别星号“*”，但不能识别下划线”_ ”，而firefox两个都不能认识。

2、选择符级Hack：比如IE6能识别*html .class{}，IE7能识别*+html .class{}或者*:first-child+html .class{}。

3、IE条件注释Hack：IE条件注释是微软IE5开始就提供的一种非标准逻辑语句。比如针对所有IE：<!-[if IE]><!-您的代码-><![endif]>，针对IE6及以下版本：<!-[if it IE 7]><!-您的代码-><![endif]->，这类Hack不仅对CSS生效，对写在判断语句里面的所有代码都会生效。

PS：条件注释只有在IE浏览器下才能执行，这个代码在非IE浏览下被当做注释视而不见。可以通过IE条件注释载入不同的CSS、JS、HTML和服务器代码等。
####li与li之间有看不见的空白间隔是什么原因引起的？有什么解决办法？
行框的排列会受到中间空白（回车\空格）等的影响，因为空格也属于字符,这些空白也会被应用样式，占据空间，所以会有间隔，把字符大小设为0，就没有空格了。
####为什么要初始化CSS样式？
因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对CSS初始化往往会出现浏览器之间的页面显示差异。

  - 当然，初始化样式会对SEO有一定的影响，但鱼和熊掌不可兼得，但力求影响最小的情况下初始化。

  最简单的初始化方法： * {padding: 0; margin: 0;} （强烈不建议）
####absolute的containing block(容器块)计算方式跟正常流有什么不同？

  无论属于哪种，都要先找到其祖先元素中最近的 position 值不为 static 的元素，然后再判断：
  1、若此元素为 inline 元素，则 containing block 为能够包含这个元素生成的第一个和最后一个 inline box 的 padding box (除 margin, border 外的区域) 的最小矩形；
  2、否则,则由这个祖先元素的 padding box 构成。
  如果都找不到，则为 initial containing block。

  补充：
  1. static(默认的)/relative：简单说就是它的父元素的内容框（即去掉padding的部分）
  2. absolute: 向上找最近的定位为absolute/relative的元素
  3. fixed: 它的containing block一律为根元素(html/body)，根元素也是initial containing block

