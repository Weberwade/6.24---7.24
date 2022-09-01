## 动画效果

### transition（过度）

通过过度可以指定一个属性发生变化出现过度离开或进场的效果，不会一瞬间进入或消失，并且过度可以创建一些比较好的效果，提升用户体验。

+ 大部分属性都支持过度效果，值是可以计算的就能过度。
+ 注意！
  + 过渡时必须时从一个有效值向另一个有效值进行过度

#### transition-property

指定执行过度的属性

+ 值可以是多个值，值间用逗号隔开
+ 所有属性都要过度可以使用all关键字

#### transition-duration

指定过度效果的持续时间

+ 值是一个时间，一定要带单位
+ 单位：
  + s
  + ms
  + 1s = 1000ms
+ 时间也可以指定多个值，逗号隔开，对应设置的过度属性的位置对应设置。

#### transition-timing-function

时序函数，指定动画过度的执行方式

+ 可选值
  + ease 默认值 慢速开始 加速 快结束时减速
  + linear 线性  匀速运动
  + ease-in  加速运动
  + ease-out 减速运动
  + ease-in-oute 先加速后减速
  + cubic-bezier() 贝塞尔曲线 [cubic-bezier(.17,.67,.83,.67) ✿ cubic-bezier.com](https://cubic-bezier.com/#.17,.67,.83,.67)
  + steps（） 分步指定过度效果
    + 第一个值表示分几步进行过度
    + 第二个值 
      + end 表示时间结束时过度
      + start 表示时间开始时过度

#### transition-delay

过度效果的延迟，等待一段时间后再执行过度效果

#### transition

简写属性，可以同时设置过度相关的所有属性，位置只有一个要求，两个时间中第一个是持续时间，第二个是延迟时间

### animation（动画）

动画和过度类似，都是可以实现一些动态的效果，不同的是过度需要再某个属性发生变化时才会触发，而动画可以自动触发动态效果。

**设置动画效果，必须先要设置一个关键帧，关键帧设置了动画执行每一个步骤。（帧数）**

#### 关键帧

+ 如何设置关键帧

  + ``````````css
            @keyframes ball {
                from{
                    margin-top: 0px;
                }
                33%,to{
                    margin-top: 400px;
                    animation-timing-function: ease-in;
                }
                66%{
                    margin-top: 100px;
                }
            }
    ``````````
    
  + @@keyframes 后面跟的是关键帧名字 可以随意取名
  
  + 属性 from{}表示动画开始的位置
  
  + 属性 to{}表示动画结束的位置
  
  + 属性也可以是一个百分比代表动画进度位置，并且在进度内设置动画内容

#### animation动画相关属性

##### animation-name

+ 指定关键帧的名字

+ `````````````````css
   animation-name: 关键帧名字;
  `````````````````

##### animation-duration

+ 指定动画的持续时间

+ ```````````````` css
  animation-duration: 时间 ;

+ 时间可以指定 秒 = s 或者 毫秒 = ms ， 1 秒 = 1000毫秒

#####  animation-delay

+ 设置动画延迟

+ ````````````````css
  animation-delay: 时间 ;
  ````````````````

+ 时间可以指定 秒 = s 或者 毫秒 = ms ， 1 秒 = 1000毫秒

##### animation-timing-function

+ 设置动画的活动方式

+ `````````````css
  animation-timing-function: ease-in;
  `````````````

+ 可选值

  + ease 默认值 慢速开始 加速 快结束时减速
  + linear 线性  匀速运动
  + ease-in  加速运动
  + ease-out 减速运动
  + ease-in-oute 先加速后减速
  + cubic-bezier() 贝塞尔曲线 [cubic-bezier(.17,.67,.83,.67) ✿ cubic-bezier.com](https://cubic-bezier.com/#.17,.67,.83,.67)
  + steps（） 分步指定过度效果
    + 第一个值表示分几步进行过度
    + 第二个值 
      + end 表示时间结束时过度
      + start 表示时间开始时过度

##### animation-iteration-count

+ 动画执行的次数

+ `````````````````css
  animation-iteration-count: 次数 ;
  `````````````````

+ 可选值

  + 一个整数
  + infinite 无限执行

##### animation-direction

+ 指定动画运行的方向

+ ``````````css
  animation-direction: 可选值 ;
  ``````````

+ 可选值

  + normal 默认值 从from 到 to运行 每次都是这样
  + reverse 将to 和 from 对调 从to 向 from运行
  + alternate 从from 到 to运行 重复执行时反向执行
  + alternate-reverse 从to 向 from运行 重复执行时反向执行

##### animation-play-state

+ 指定动画的执行状态，一般用来配合hover鼠标移入，动画暂停

+ ```````css
  animation-play-state: 可选值 ;
  ```````

+ 可选值 

  + running 默认值
  + paused 动画暂停

#####  animation-fill-mode

+ 指定动画开始结束时的效果

+ ````````````````css
   animation-fill-mode: 可选值 ;
  ````````````````

+ 可选值

  + none 默认值 动画执行完毕元素回到原来的位置
  + forwards 动画执行完毕元素停在动画结束位置
  + backwards 动画延时等待时，元素就会处于动画开始位置
  + both 结合了forwards 和 backwards 动画延时到动画开始位置，动画结束时停在动画结束位置

##### animation

简写属性

+ 只有动画时间和动画延迟两个时间单位有顺序要求，其他属性位置随意
  + 动画时间 写在 动画延迟前面 

### transform（变形）

可以一次指定多个值，用空格隔开，但是顺序会影响触发顺序

#### 平移属性

+ 可以同时指定多个值，中间用空格隔开

+ 平移元素时，如果值是百分比是相对于相对于自身的值计算的
+ 可以利用平移实现居中效果，left拉到中间，再用translate拉回自身的50%，让自身的中间对齐中线实现居中

##### translateX() 元素沿着x轴方向平移

x轴平移，调整元素在x轴的位置，正常情况就是调整元素向右移动

+ 值
  + 直接写一个像素值
  + 百分比（值按照元素自身计算）

##### translateY() 元素沿着y轴方向平移

y轴平移，调整元素在y轴的位置，正常情况就是调整元素向下移动

值

+ 直接写一个像素值
+ 百分比（值按照元素自身计算）

##### translateZ() 元素沿着z轴方向平移

z轴平移，调整元素在z轴的位置，正常情况就是调整元素和人眼之间的距离，距离越大，元素离人越近

z轴平移属于立体效果（近大远小），默认情况下网页不支持透视，如果需要看见效果，必须要设置网页的视距，一般设置给body（perspective: 800px;）值600 - 1200最好。

值

+ 直接写一个像素值
+ 百分比（值按照元素自身计算）

#### 旋转属性

通过旋转可以使元素沿着轴 x y 或者 z旋转指定的角度

如果想要3D效果一定要设置视距

##### rotateX()

##### rotateY()

##### rotateZ()

### transform-style（元素的显示方式）平面-3D切换

可以将画面从2D切换到3D效果

不切换3D效果看不到旋转了90°的图片

+ ``````````css
  transform-style: preserve-3d;

##### backface-visibility

不显示图片背面

+ 可选值
  + visible 默认值 显示背面
  + hidden 不显示背面

### 缩放属性

#### scale()

双方向缩放

+ 值
  + 一个可以乘的整数，正负数都可以，小数代表正常缩小，负数将从另一边重新长出，正数1以上的数字就是正常放大

#### scaleX()

水平方向缩放

+ 值
  + 一个可以乘的整数，正负数都可以，小数代表正常缩小，负数将从另一边重新长出，正数1以上的数字就是正常放大

#### scaleY()

垂直方向缩放

+ 值
  + 一个可以乘的整数，正负数都可以，小数代表正常缩小，负数将从另一边重新长出，正数1以上的数字就是正常放大

#### scaleZ()

Z轴很难看出效果，只有3D才能看到效果，让视距变近，变大

+ 值
  + 一个可以乘的整数，正负数都可以，小数代表正常缩小，负数将从另一边重新长出，正数1以上的数字就是正常放大

### transform-origin

变形的原点

left right center 改变元素变形原点

