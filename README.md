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

