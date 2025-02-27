##03-HTML和CSS进阶

###00-知识点预习
-	1.表单
- 	2.元素类型
-  3.浮动
-  4.定位

###01- 表单
- **form标签 表单用来提交数据**
	- **action** 要提交的网址,默认是当前网页
	- **method** 请求  提交方式
		- 默认get请求   
		- post请求
		- 切换请求方式时注意缓存问题
- **label标签**
	- for属性如果设置的值和 input标签中设置的id属性值一样就可以实现点击label让对应的input成为焦点
- **输入框的两个常用属性：**
	- **placeholder** 占位提示文字
	- **outline:none** 输入框的边框
- **input标签中的type属性值介绍:**

type值 |含义
---|---
**text** |文本输入框
	 **password** |密文 密码文本输入框
	**radio**  |单选 需要设置name属性值一样才能单选 默认选择checked
	**checkbox**  |多选按钮   默认选择 checked
**file**  |选择文件
**submit** | 提交 注册按钮
**reset** | 重置按钮
**button**  |普通按钮

- **select** 下拉列表'选择列表'新的标签
	- **option** 选项
-	**textarea标签** 多行文本输入框


###02-搜索条案例
-	文本距离盒子有一定间距时优先考虑使用文字缩进text-indent,如果用内边距还要考虑盒子模型问题
- **文本输入框默认有边框和内边距**
- **按钮也有默认边框**
- 默认元素会以文字基线"文字底部"来进行元素对齐,用浮动可以解决让元素不以文字基线对齐,也可以解决元素之间默认间距问题
- cursor:pointer 设置鼠标在元素上的样式为小手

###03-块元素特点
-	块元素，也可以称为行元素，布局中常用的块标签如：div、p、ul、li、h1~h6等等都是块元素，它在布局中的行为特点:
	-	1.独霸一行
	-	2.宽度默认和父元素一样宽
	-	3.支持所有样式如margin padding等

###04-块元素的样式重置
-	有些标签是包含默认的样式的:
	-	p标签：含有默认外边距
	-	ul：含有默认外边距和内边距，以及条目符号
	-	h1~h6标签：含有默认的外边距和字体大小
	-	body标签：含有默认的外边距

- 实际开发中，为了便于布局我们会把带有默认样式的标签样式清除掉,这个做法就叫样式重置.

```
/* 清除标签默认的外边和内边距 */
body,p,h1,h2,h3,h4,h5,h6,ul{
    margin:0px;
    padding:0px;
}

/* 清除标签默认条目符号 */
ul{
    list-style:none;
}

/* 将h标签的文字大小设置为默认大小 */
h1,h2,h3,h4,h5,h6{
	/* 和父元素的字体一样大 默认16 */
    font-size:100%;
    /* 根据实际需求来加   */
    font-weight:normal;
}

```

###05-行内元素的特点
-	内联元素，也可以称为行内元素，布局中常用的标签如：a、span等等都是内联元素，它们在布局中的行为:
	-	1.宽高默认和内容决定
	-	2.排列在一行,当遇到父元素的边界会自动换行
	-	3.不支持宽高 margin上下 padding上下有问题
	-	4.代码换行后行内元素之间有小间隙
	-	5.行内元素设置文本水平对齐无效,但可以设置他们的父元素的text-align实现子元素水平对齐
        

###06-行内元素的样式重置
-	其他内联元素"面试前最好看看它们的语义"

```
1、<em> 标签 行内元素，表示语气中的强调词
2、<i> 标签 行内元素，表示专业词汇
3、<b> 标签 行内元素，表示文档中的关键字或者产品名
4、<strong> 标签 行内元素，表示非常重要的内容
```

-	包含默认样式的内联元素

	-	a标签：含有的下划线以及文字颜色
	-	em、i标签：文字默认为斜体
	-	b、strong标签：文字默认加粗
	-	实际开发中，对这些标签进行样式重置。
	
```
/* 去掉a标签默认的下划线 */
a{
    text-decoration:none;
}
/* 去掉标签默认的文字倾斜 */
em,i{
    font-style:normal;
}
/* 去掉标签默认的文字加粗(按实际需求) */
b,strong{
    font-weight:normal;
}
```
-	解决内联元素间隙的方法:
	-	1、去掉内联元素之间的换行
	-	2、将内联元素的父级设置font-size为0，内联元素自身再设置具体的font-size

###07-行内元素布局菜单案例
-	行内元素设置文本水平对齐无效,但可以设置他们的父元素的text-align实现子元素水平对齐

###08-行内块元素的特性
-	内联块元素，也叫行内块元素，是新增的元素类型，现有元素没有归于此类别的，img和input元素的行为类似这种元素，但是也归类于内联元素，我们可以用display属性将块元素或者内联元素转化成这种元素。它们在布局中表现的行为：
	-	1.元素排列一行
	-	2.宽度默认有内容决定
	-	3.元素间有默认间距
	-	4.支持宽高 marign padding等所有样式
	-	5.子元素是内联块元素，父元素可以用text-align属性设置子元素水平对齐方式


-	display属性是用来设置元素的类型及隐藏的，属性的值有：
	-	1、none 元素隐藏且不占位置
	-	2、block 元素以块元素显示
	-	3、inline 元素以内联元素显示
	-	4、inline-block 元素以内联块元素显示

###09-行内块分页导航案例
-	把li和a都转换成inline-block
- 	为了动态性,可以确定子元素的尺寸,父元素的尺寸有子元素撑起来


###10-浮动元素的特性
-	如果要实现子元素在父元素中水平居中时不能用浮动
- 元素浮动特点:
	-	1.只有左和右浮动
	-	2.浮动元素遇到父元素或其他元素都会停下来
	-	3.浮动后块元素也会排在一行,宽度会默认有内容决定,相邻元素一行排不下之后会自动换行
	-	4.块元素和行内元素浮动后会自动转换为浮动特性的行内块元素

-	浮动可以解决的问题:
	-	1.行内元素及行内块元素之间间距问题
	-	2.垂直外边距不再合并
	-	3.margin-top塌陷问题

###11-清除浮动
- 什么时候需要清除浮动?
	-	当父元素没有设置高度而子元素又全部浮动时,此时父元素的高度就无法通过子元素自动计算了,就要清除浮动来让父元素还能自动计算高度

-	清除浮动的方法

```
第一种:父级上增加属性overflow：hidden

第二种:在最后一个子元素的后面加一个空的div，给它样式属性 clear:both（不推荐）

第三种:使用成熟的清浮动样式类，clearfix
.clearfix:after,.clearfix:before{ content: "";display: table;}
.clearfix:after{ clear:both;}
.clearfix{zoom:1;} /* IE下清除浮动及解决margin-top塌陷问题 */
```


###12-定位
- **文档流**
	-	文档流，是指盒子按照html标签编写的顺序依次从上到下，从左到右排列，块元素占一行，行内元素在一行之内从左到右排列，先写的先排列，后写的排在后面，每个盒子都占据自己的位置。


-	我们可以使用CSS的position属性来设置元素的定位类型，postion的设置项如下：
	-	1.relative 生成相对定位元素，元素所占据的文档流的位置保留，元素本身相对自身原位置进行偏移。

	-	2.absolute 生成绝对定位元素，元素脱离文档流，不占据文档流的位置，可以理解为漂浮在文档流的上方，相对于上一个设置了定位的父级元素来进行定位，如果找不到，则相对于window元素进行定位。

	-	3.fixed 生成固定定位元素，元素脱离文档流，不占据文档流的位置，可以理解为漂浮在文档流的上方，相对于浏览器窗口进行定位。

	-	4.static 默认值，没有定位，元素出现在正常的文档流中，相当于取消定位属性或者不设置定位属性。

-	**定位元素的偏移**
	-	定位的元素还需要用left、right、top或者bottom来设置相对于参照元素的偏移值。

-	**定位元素层级**
	-	定位元素是浮动的正常的文档流之上的，可以用z-index属性来设置元素的层级

- **定位元素特性**
	-	绝对定位和固定定位的块元素和行内元素会自动转化为行内块元素

###15-定位案例

```
/* 设置元素圆角,将元素四个角设置4px半径的圆角 */
border-radius:4px;

/* 设置元素透明度,将元素透明度设置为0.3，此属性需要加一个兼容IE的写法 */
opacity:0.3;
/* 兼容IE */
filter:alpha(opacity=30);
```

###16-水平垂直居中提示框案例
```
	/* 固定定位 */
	position: fixed;

	/* 水平居中 */
	left: 50%;
	margin-left: -150px;
	/* 垂直居中 */
	top:50%;
	margin-top: -150px;
```

###17-定位小结
-	static 默认值,没有定位
	- 使用场景:一般来说不用写，除非想要覆盖之前设置的定位 
-	relative 相对定位   
	- 使用场景:和absolute一起使用，常用于logo的定位。
-  absolute 绝对定位  
	- 使用场景:网页中的logo图片及一定移动动画
-  fixed 固定定位     
	- 使用场景:悬浮在浏览器中的广告窗口
