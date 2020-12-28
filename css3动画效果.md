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
