## 定位的简介

### 定位（position）

+ 定位是一种更加高级的布局手段
+ 通过定位可以将元素摆放在页面的任意位置
+ 使用position属性来设置定位

#### 可选值：

1. static 默认值，元素是静止的没有开启定位
2. relative 开启元素的相对定位
3. absolute 开启元素的绝对定位
4. fixed 开启元素的固定定位
5. sticky 开启元素的粘滞定位

### 偏移量（offset）

+ 当元素开启了定位以后，可以通过偏移量来设置元素的定位

#### 值

+ top
  + 定位元素和定位位置上边的距离

+ bottom
  + 定位元素和定位位置下边的距离

+ 定位元素垂直方向的位置由top和bottom两个属性来控制，通常情况下我们只会使用一个

+ right
  + 定位元素和定位位置右边的距离

+ left
  + 定位元素和定位位置左边的距离
+ 定位元素水平方向的位置由left和right两个属性来控制，通常情况下我们只会使用一个

### 包含块

+ 正常情况下，包含块就是离当前元素最近的祖先元素

#### 绝对定位的包含块

+ 绝对定位的包含块就是离它最近的开启了定位的祖先元素
+ 如果所有祖先元素都没有开启定位则相对于根元素（初始包含块）进行定位
  + html（根元素、初始包含块）

### 元素的层级

对开启了定位的元素，可以通过z-index属性来指定元素的层级

+ z-index 需要一个整数作为参数，值越大元素的层级越高，元素层级越高越优先显示
+ 如果元素的层级一样，则优先显示html中靠下的元素
+ 祖先元素的层级再高也不会盖住后代元素

### 相对定位

+ 当元素的position属性值设置为relative时则开启了元素的相对定位

#### 相对定位特点

1. 元素开启相对定位后，如果不设置偏移量元素不会发生变化
2. 相对定位是参照于元素在文档流中的位置进行定位的
3. 相对定位会提升元素的层级
4. 相对定会不会使元素脱离文档流
5. 相对定位不会改变元素的性质，块元素还是块元素，行内元素还是行内元素

### 绝对定位

+ 当元素的position属性值设置为absolute时则开启了元素的绝对定位

#### 绝对定位特点

1. 开启绝对定位后，如果不设置偏移量元素位置不会发生变化
2. 绝对定位元素是相对于其开启定位的包含块进行定位
3. 开启绝对定位后，元素会从文档流中脱离
4. 绝对定位会改变元素性质
5. 绝对定位会使元素提升一个层级

#### 绝对定位元素布局

##### 水平布局的特点

+ ``````css
  left + margin-left + border-left-width + padding-left+ content-width + padding-right+ border-right-width + margin-right + right = 包含块宽度

+ 当我们开启了绝对定位后，水平方向的布局就需要添加left和right两个值，规则和之前一样只是多添加了两个值，当发生过度约束，9个值没有auto则自动调整right使等式满足
  + 注意！因为left 和 right的值默认是auto，所以如果不设置left和right则等式不成立，会自动调整这两个值

##### 垂直方向的特点

+ 垂直方向布局的等式也必须要满足

  + ```````````````````css
    top + margin-top + border-top-width + padding-top+ content-height + padding-bottom + border-bottom-width + margin-bottom + right = 包含块高度
    ```````````````````

+ 当我们开启了绝对定位后，垂直方向的布局就需要添加top和bottom两个值，规则和之前一样只是多添加了两个值，当发生过度约束，9个值没有auto则自动调整bottom使等式满足

### 固定定位

+ 当元素的position属性值设置为fixed时则开启了元素的固定定位

#### 固定定位特点

+ 固定定位也是一种绝对定位，所以固定定位大部分特点和绝对定位一样
+ 唯一不同于绝对定位的是固定定位永远参照于浏览器的视口进行定位
  + 视口就是浏览器窗口
  + 固定定位的元素不会随网页的滚动条滚动

### 粘滞定位

+ 当元素的position属性值设置为sticky时则开启了元素的粘滞定位

#### 粘滞定位特点

+ 粘滞定位和相对定位的特点基本一致
+ 不同的是粘滞定位可以在元素到达某个位置时将其固定
+ 根据包含块定位


