## 一、CSS变形（transform）
### 1、平移：使用transform属性的translate()方法
    transform: translateX(x);    /*单位可以为px、em和百分比等*/
    transform: translateY(y);        
    transform: translate(x, y); 
### 2、缩放：使用transform属性的scale()方法
    transform: scaleX(x);      /*参数x表示元素在x轴方向的缩放倍数*/
    transform: scaleY(y);      /*当x或y取值为0~1之间时，元素进行缩小；当x或y取值大于1时，元素进行放大。*/
    transform: scale(x, y);        
### 3、倾斜：使用transform属性的skew()方法
    transform: skewX(x);        /*参数x表示元素在x轴方向的倾斜度数，单位为deg（可以为负数）*/
    transform: skewY(y);       
    transform: skew(x, y);      
### 4、旋转：使用transform属性的rotate()方法
    transform: rotate(angle);
    参数angle表示元素相对于中心原点旋转的度数，单位为deg。如果度数为正，则表示顺时针旋转；如果度数为负，则表示逆时针旋转。
### 5、中心原点 transform-origin  
在CSS3变形中，任何元素都有一个中心原点。默认情况下，元素的中心原点位于x轴和y轴的50%处。（中心位置center center）<br>
默认情况下，CSS3的各种变形（平移、缩放、倾斜等）都是以元素的中心原点进行变形的。<br>
使用transform-origin属性来改变元素的中心原点,则变形效果也会产生相应改变。<br>

    transform-origin: 取值; /*取值有两种：一种是“长度值”（单位px、em、百分比等）；另外一种是“关键字”（如top left，right center，bottom center）*/
## 二、CSS过渡（transition）
* transition属性可以将元素的某一个属性从“一个属性值”在指定的时间内平滑地过渡到“另一个属性值”，从而来实现动画效果
* CSS变形（transform）呈现的仅仅是一个“结果”，而CSS过渡（transition）呈现的是一个“过程”，一种动画变化过程，如渐渐显示、渐渐隐藏、动画快慢等

      transition: 过渡属性 过渡时间 过渡方式 延迟时间;
      
      transition-property	对元素的哪一个属性进行操作
      transition-duration	过渡的持续时间
      transition-timing-function	过渡的速率方式，取值：
                                    ease（默认值）  由快到慢，逐渐变慢
                                    linear   匀速
                                    ease-in  速度越来越快（即渐显效果）
                                    ease-out	速度越来越慢（即渐隐效果）
                                    ease-in-out	先加速后减速（即渐显渐隐效果）
      transition-delay	    过渡的延迟时间（可选参数），默认值为0s，延迟开始呈现过渡效果，过渡效果也延迟恢复
* 当transition-property属性定义为all时，CSS3会自动判断哪些属性是作为过渡效果的属性
* transition属性写在普通状态和悬浮状态（即:hover{}）效果不同：移入时效果两者没有区别；transition属性写在普通状态内，移出时会有过渡效果；transition属性写在悬浮状态内，移出时没有过渡效果。
## 三、CSS3动画（animation）
对于transition属性来说，它只能将元素的某一个属性从一个属性值过渡到另一个属性值。<br>
对于animation属性来说，它可以将元素的某一个属性从第1个属性值过渡到第2个属性值，然后还可以继续过渡到第3个属性值，以此类推。<br>
* transition属性（即CSS3过渡）只能实现一次性的动画效果，而animation属性（即CSS3动画）可以实现连续性的动画效果。

        animation: 动画名称 持续时间 动画方式 延迟时间 动画次数 动画方向;
        
        animation-name	对哪一个CSS属性进行操作
        animation-duration	动画的持续时间
        animation-timing-function	动画的速率方式
        animation-delay	动画的延迟时间
        animation-iteration-count	动画的播放次数  /*取值是n（正整数）时，动画播放n次；取值为infinite时，动画播放无数次，也就是循环播放。*/
        animation-direction	动画的播放方向，正向还是反向  /*取值为normal（默认值），正方向播放；
                                                                reverse，反方向播放；
                                                                alternate，播放次数是奇数时，动画正方向播放；播放次数是偶数时，动画反方向播放 */
### 1、 定义动画 @keyframes    
        @keyframes 动画名
        {
          0%{}      /*0%表示动画的开始，100%表示动画的结束，0%和100%是必须的。*/
          ……        /*描述每个百分比（阶段）动画的样式，之后运行起来就是一段连续的动画变化了*/
         100%{}
        }
        
        @keyframes mytransform
        {
            0%{border-radius:0;}
            50%{border-radius:50px; transform:translateX(0);} /*若是少了transform:translateX(0);，则从0%开始运动50px到100% */
            100%{-webkit-transform:translateX(50px);}
        }
        
### 2、调用动画        
        eg：
        @keyframes mycolor
        {
            0%{background-color:red;}
            30%{background-color:blue;}
            60%{background-color:yellow;}
            100%{background-color:green;}
        }
        div:hover
        {
            animation:mycolor 5s linear; /*调用mycolor这个动画*/
        }
若想元素自动执行，而不是鼠标移到元素上时（:hover），动画才开始，则将调用动画的代码放在div元素，而不是在:hover伪类中     
### 3、播放状态 animation-play-state      
       animation-play-state: 取值;  /*取值为running（默认值），播放；paused，暂停
        
        
        
        
        
