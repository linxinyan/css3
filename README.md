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
