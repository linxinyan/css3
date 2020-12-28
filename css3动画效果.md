## 一、CSS变形（transform）
### 1、平移：使用transform属性的translate()方法
    transform: translateX(x);    //单位可以为px、em和百分比等
    transform: translateY(y);        
    transform: translate(x, y); 
### 2、缩放：使用transform属性的scale()方法
    transform: scaleX(x);      //参数x表示元素在x轴方向的缩放倍数
    transform: scaleY(y);      //当x或y取值为0~1之间时，元素进行缩小；当x或y取值大于1时，元素进行放大。
    transform: scale(x, y);        
### 3、倾斜：使用transform属性的skew()方法
    transform: skewX(x);        //参数x表示元素在x轴方向的倾斜度数，单位为deg（可以为负数）
    transform: skewY(y);       
    transform: skew(x, y);      
### 4、旋转：使用transform属性的rotate()方法
    transform: rotate(angle);
    参数angle表示元素相对于中心原点旋转的度数，单位为deg。如果度数为正，则表示顺时针旋转；如果度数为负，则表示逆时针旋转。
### 5、中心原点 transform-origin  
在CSS3变形中，任何元素都有一个中心原点。默认情况下，元素的中心原点位于x轴和y轴的50%处。（中心位置center center）<br>
默认情况下，CSS3的各种变形（平移、缩放、倾斜等）都是以元素的中心原点进行变形的。<br>
使用transform-origin属性来改变元素的中心原点,则变形效果也会产生相应改变。<br>

    transform-origin: 取值; //取值有两种：一种是“长度值”（单位px、em、百分比等）；另外一种是“关键字”（如top left，right center，bottom center）
