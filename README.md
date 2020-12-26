css3 learning note

## 一、浏览器私有前缀：
    私有前缀	对应的浏览器
    -webkit-	Chrome和Safari
    -moz-	    Firefox
    -ms-	    IE
    -o-	      Opera
* 更多CSS3属性在各大浏览器的兼容性情况，在https://caniuse.com/上查看

## 二、选择器
### 1、属性选择器
    选择器	            说明
    E[attr^=“xxx”]	 选择属性是以xxx开头的元素E
    E[attr$=“xxx”]	 选择属性是以xxx结尾的元素E
    E[attr*=“xxx”]	 选择属性包含xxx的元素E
### 2、子类
    (1):first-child、:last-child、:nth-child(n)、:only-child  (:nth-child(n)中n取值有3种：数字、odd和even，其中n从1开始）
    (2):first-of-type、:last-of-type、:nth-of-type(n)、:only-of-type 
* :first-child在选择父元素下的子元素时，不仅要区分元素类型，还要求是第一个子元素。而:first-of-type在选择父元素下的子元素时，只需要区分元素类型，不要求是第一个子元素

### 3、UI伪类选择器
针对不同状态的元素选择器，大多是表单元素（按钮、单选框、复选框、文本框、下拉列表）<br>
#### （1）:focus
定义元素获取焦点时使用的样式（表单元素和超链接）
#### （2）::selection
定义页面中被选中文本的样式。注意，::selection选择器使用的是双冒号，而不是单冒号。`实际上，单冒号往往都是伪类，而双冒号往往都是伪元素`。
#### （3）:checked
定义单选框或复选框被选中时的样式。兼容性很差，简单了解即可。
#### （4）:enabled和:disabled
:enabled选择器定义表单元素“可用”时的样式；:disabled选择器来定义表单元素“不可用”（disabled）时的样式。
#### （5）:read-write和:read-only
:read-write选择器定义表单元素“可读写”时的样式；:read-only选择器定义表单元素“只读”（readonly）时的样式。

### 4、其他伪类选择
#### （1）:root
选择HTML页面的根元素（即整个页面）<br>
        :root{background-color:gray;}
        html{background-color:gray;}
以上两句代码等价，同时，如果想要设置整个页面的背景色，我们应该针对html元素来设置，而不是body元素。
#### （2）:empty
选择一个空元素
#### （3）:target
选取页面中的某一个target元素（所谓的target元素，指的是id被当成页面的锚点链接来使用的元素），如：

        <a href="#music">推荐音乐</a><br />
        
        <div id="music">
            <h3>推荐音乐</h3>
            <ul>
                <li>林俊杰-被风吹过的夏天</li>
                <li>曲婉婷-在我的歌声里</li>
                <li>许嵩-灰色头像</li>
            </ul>
        </div>
点击“推荐音乐”链接，则可跳转到div元素所在位置
#### （4）:not()
选取某一个元素之外的所有元素，如：

        ul li:not(.first)
即选取除了class="first"以外的li元素

## 三、文本样式
### 1、文本阴影 text-shadow
        text-shadow:x-offset  y-offset  blur  color;
文字凸起效果：向左和向上的阴影颜色设置为白色 <br>
文字凹陷效果：向右和向下的阴影颜色设置为白色<br>
`text-shadow还可为文本定义多个阴影，并且针对每个阴影使用不同的颜色。如：`<br>

        text-shadow:0 0 4px red,  0 -5px 4px green,  2px -10px 6px blue;
当text-shadow属性是一个值列表时，阴影效果会按从左到右的顺序应用到文本上，因此可能会出现相互覆盖的效果。但是text-shadow属性永远不会覆盖文本本身     
### 2、文本描边 text-stroke       
          text-stroke:width color;     
若将文字颜色设为 color:transparent;再使用text-stroke则可实现镂空文字
### 3、文本溢出 text-overflow
        text-overflow:取值;   //取值为ellipsis，当文本溢出时，显示省略号，并且隐藏多余的文字；取值为clip，则将溢出的文字裁切掉
实现单行文本的省略号效果：

        overflow:hidden; 
        white-space:nowrap;
        text-overflow:ellipsis; 
若想实现“多行文本”的省略号效果，必须借助JavaScript或jQuery。JQuery可通过插件jquery.dotdotdot.js实现该效果
### 4、强制换行 word-wrap和word-break
定义长单词或URL地址是否换行到下一行

        word-wrap:取值;  //取值为normal，自动换行（默认值）；取值为break-word，强制换行 
        
        word-break:取值; //取值为normal，自动换行（默认值）；break-all，允许在单词内换行；keep-all，只能在半角空格或连字符处换行
* 重点掌握 word-wrap:break-word;和word-break:break-all <br>
* word-wrap:break-word; 会首先尝试挪到下一行，看看下一行的宽度够不够，不够的话再进行单词内的断句。
* word-break:break-all; 不会尝试把长单词挪到下一行，而是直接就进行单词内的断句。
* 注：word-wrap和word-break这两个属性都是针对英文页面来说的   
### 5、嵌入字体：@font-face  
加载服务器端的字体，从而使得所有用户都能正常显示该字体

        @font-face
        {
            font-family: 字体名称;
            src:url(文件路径);
        }
使用@font-face定义字体，再使用font-family引用字体 <br>     
src属性中的“文件路径”指的是服务器端中字体文件的路径 <br>
`注：不建议使用@font-face来实现嵌入中文字体。这是因为中文字体文件大多数都是10MB以上。这么大的字体文件，会严重影响页面的加载速度，导致用户体验非常差。不过对于英文字体来说，字体文件往往只有几十KB，非常适合使用@font-face。`
## 四、颜色样式
### 1、opacity透明度 
        opacity:数值; //取值范围为0.0~1.0,0.0表示完全透明，1.0表示完全不透明。
 opacity属性在实际开发用得比较多，大多数时候都是配合:hover来定义鼠标移动到某个按钮或图片上时，改变透明度来呈现动态的效果。       
### 2、RGBA颜色
        rgba(R,G,B,A); //R指红色值（Red）；G指绿色值（Green）；B指蓝色值（Blue）；A指透明度（Alpha）。
                         R、G、B这三个可以为整数，取值范围为0~255，也可以为百分比，取值范围为0%~100%。
                         参数A为透明度，跟opacity属性是一样的，取值范围为0.0~1.0。
*  如果对某个元素使用opacity属性，则该元素中的所有的子元素以及文本内容都会受到影响。 
*  而RGBA中的透明度只会针对当前设置的属性起作用
### 3、CSS3渐变
#### （1）线性渐变
       background:linear-gradient(方向, 开始颜色, 结束颜色) //方向取值有两种:一种是使用角度（单位为deg）;另外一种是使用关键字，如下所示：
        属性值	        对应角度	   说明
        to top	        0deg	     从下到上
        to bottom	    180deg	     从上到下（默认值）
        to left	        270deg	     从右到左
        to right	    90deg	     从左到右
        to top left	    无	        从右下角到左上角（斜对角）
        to top right	无	        从左下角到右上角（斜对角）
* 线性渐变也可以接受一个“值列表”，用于同时定义多种颜色的线性渐变，颜色值之间用英文逗号隔开即可。如：<br>
* background:linear-gradient(to right, red, orange, yellow, green, blue);
#### （2）径向渐变
颜色从内到外进行的圆形（椭圆）渐变。颜色不再沿着一条直线渐变，而是从一个起点向所有方向渐变。
        
        background:radial-gradient(position, shape size, start-color, stop-color)
        //position用于定义圆心位置。shape size用于定义形状大小，由两部分组成，shape定义形状，size定义大小。
          其中，position和shape size都是可选参数。如果省略，则表示采用默认值。start-color和stop-color都是必选参数，可以有多个颜色值。        
圆心位置position<br>
取值有两种：一种是“长度值”（如10px）；另外一种是“关键字”（center（默认值），top，bottom，left，right，<br>
top center靠上居中，top left左上，left center靠左居中，bottom left左下等   [top,center,bottom与left,center,bottom的组合]）<br>
<br>
shape 取值：ellipse椭圆形（默认值）,circle	圆形 <br>
* 径向渐变也可以接受一个“值列表”，用于同时定义多种颜色的径向渐变。默认情况下，径向渐变的颜色节点是均匀分布的，不过我们可以为每一种颜色添加百分比，从而使得各个颜色节点不均匀分布。
* 在真正的开发中，大多数渐变效果都是线性渐变，重点掌握线性渐变
## 五、边框样式
### 1、圆角效果 border-radius
        border-radius:取值; //取值是一个长度值，单位可以是px、em和百分比等
        border-radius:10px; //元素4个角的圆角半径都是10px
        
        * 顺序为左上-右上-右下-左下（顺时针）
        border-radius:10px 20px; //左上角和右下角的圆角半径是10px，右上角和左下角的圆角半径都是20px
        border-radius:10px 20px 30px; //左上角的圆角半径是10px，右上角和左下角的圆角半径都是20px，右下角圆角半径是30px
        border-radius:10px 20px 30px 40px; //依次为左上角、右上角、右下角和左下角的圆角半径
     
        //border-radius实现半圆
        width:100px;
        height:50px;  
        border-radius:50px 50px 0 0; //实现了一个半径为50px的上半圆
        
        //border-radius实现圆（元素的宽度和高度定义为相同值，然后4个角的圆角半径定义为宽度（或高度）的一半（或者50%））
        width:100px;
        height:100px;
        border-radius:50px; //实现了一个半径为50px的圆
        
        //border-radius实现椭圆
        border-radius:x/y; //x表示圆角的水平半径，y表示圆角的垂直半径
### 2、边框阴影 box-shadow
#### （1）
        box-shadow:x-offset  y-offset  blur  spread  color  style;
        
        x-offset：定义水平阴影的偏移距离，x-offset取值为正时，向右偏移；取值为负时，向左偏移。
        y-offset：定义垂直阴影的偏移距离，y-offset取值为正时，向下偏移；取值为负时，向上偏移。
        blur：定义阴影的`模糊`半径，只能为正值。
        spread：定义阴影的大小。
        color：定义阴影的颜色。
        style：定义是外阴影还是内阴影，默认为外阴影outset，内阴影为inset
        
        eg：
        box-shadow:5px 5px 8px 0px red;表示阴影的水平偏移距离为5px，垂直偏移距离为5px，模糊半径为8px，阴影大小为0px，阴影颜色为red。       
#### （2）各个方向阴影独立样式
        box-shadow:左阴影, 上阴影, 下阴影, 右阴影;  //每条边的阴影属性值之间用逗号隔开！
        eg:       
        box-shadow:-5px 0 12px red,
                   0 -5px 12px yellow,
                   0 5px 12px blue,
                   5px 0 12px green;





