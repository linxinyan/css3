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
    (1):first-child、:last-child、:nth-child(n)、:only-child
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
    
    
    
    
    
    
    
