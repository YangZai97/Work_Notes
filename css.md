# Css 基础
## 属性
#### 字体
- font-style
    * normal : 正常的字体
    * italic ：斜体，对于没有斜体变量的特殊字体，将应用oblique（通常使用他）
    * oblique ：倾斜的字体
- line-height： 字体最顶端到最底部之间的距离
- letter-spacing：设置文字之间的间隔
- font-variant
    * normal : 正常的字体
    * small-caps ：小型的大写字母字体
- caption : 使用有标题的系统控件的文本字体（如按钮，菜单等）
- icon : 使用图标标签的字体
- menu : 使用菜单的字体
- message-box : 使用信息对话框的文本字体
- small-caption : 使用小控件的字体
- status-bar : 使用窗口状态栏的字体
- text-decoration 
    * none ：无装饰
    * blink ：闪烁
    * underline ：下划线
    * line-through：贯穿线（删除线）
    * overline： 上划线
- text-transform 
    * none：无转换
    * capitalize: 将每个单词首字母大写（MyName)
    * uppercase：全字母转换为大写
    * lowercase: 全字母转换为小写
#### 文本
- text-indent 检索或设置对象中的文本缩进，允许为负值
- text-overflow 
    * clip：不显示省略标记(...) 只是简单的裁切
    * ellipsis： 对当前对象文本溢出时显示省略标记(...)
- text-align
    * left/right
    * center 居中
    * justify 两端对齐
- white-space
    * normal:默认处理方式
    * nowrap:强制将同一行内显示所有文本，直到文本结束或遭遇br后换行
#### 背景
- background-color:背景色设置
    * transparent：背景色透明
- background-image
    * none 无背景图
    * url使用绝对路径或相对路径指定背景图像位置
- background-position 设置背景图像位置,必须先指定background-image属性
    * 如果只指定一个值，将是代表横坐标
    * 默认值(0%，0%)
- background-positionX 横坐标
    * 默认值（0%）
    * left right center
- background-positionY 纵坐标
    * 默认值（0%）
    * top bottom center
- background-repeat 设置背景图像是否及如何铺排
    * repeat: 背景图在纵向和横向上平铺
    * no-repeat：背景图像不平铺
    * repeat-x 横向
    * repeat-y 纵向
#### 定位
- position 
    * static：无特殊定位，对象遵循html定位规则
    * absolute: 将对象从文档流中拖出，使用left、top、right、bottom等属性进行定位。而其叠层通过z-index进行定义。此时对象不具有边距（以relative作为父级进行移动,如一直没有则相对于body定位。）
    * relative :对象不可层叠，但依left、right、top、bottom等进行在正常文档流中偏移位置
    * flxed
#### 布局
- float (left、righ)
    * 当该属性不等于none引起对象浮动时，对象将被视作块对象(block-level)，即display属性等于block。也就是说，浮动对象的display特性将被忽略。
- clear 清除浮动
    * none：允许两边都有浮动
    * both：不允许有浮动对象
    * left、right ：不允许左、右有浮动对象
- clip 检索或设置对象的可视区域。区域外的部分是透明的。
必须将position的值设为absolute，此属性方可使用
    * auto：无对象剪切
    * rect: (number,number,number,number)
    依据上-右-下-左的顺序提供自对象左上角为(0,0)坐标计算的四个偏移数值，其中任一数值都可用auto替换，即此边不剪切
- overflow 检索或设置当对象的内容超过其指定高度及宽度时如何管理内容
    * visible: 不剪切内容也不添加滚动条，并且clip属性设置失效
    * auto: 刺猬body对象和textarea的默认值。在需要剪切的内容添加滚动条
    * hidden：不显示超出对象尺寸的内容
    * scroll: 总是显示滚动条
- display 设置或检索对象是否显示及如何显示
    * block: 用改值后将元素变成块级元素。（块级元素的默认值）
    * none： 隐藏对象。（与visibility：hidden不同，此none属性是将隐藏的对象彻底移除，并不保留dom物理空间）
    * inline：将对象变成内联元素，与block对应。
    * inline-table：将表格显示为无前后换行的内联元素或内联容器对象。
    * list-item：将块级对象指定为列表项目。并可以添加可选项目标志。
    * table: 将对象作为块级元素的表格显示。
    * table-caption: 将对象作为表格标题显示。
    * table-cell：将对象作为表格单元格显示。
    * table-row：将对象作为表格列显示。
    * table-column：将对象作为表格列显示。
    * table-column-group : 将对象作为表格列组显示
    * table-header-group : 将对象作为表格标题组显示
    * table-footer-group ： 将对象作为表格脚注组显示。
    * table-row-group：将对象作为表格行组显示。
- visibility 设置对象是否显示，与display不同
    * inherit:继承上一个父对象的可见性
    * visible：对象可视
    * hidden：对象隐藏
    * collapse：主要用来隐藏表格的行、列。其作用等同于hidden。
#### 外边距
- margin,margin-top(bottom/right/left) 检索或设置对象四边的外延边距。
#### 内边距
- padding,padding-top(bottom/right/left) 检索或设置对象四边的补丁边距。
#### 边框 （border，border-top/bottom/right/left)
- border-color:设置边框的颜色
- border-width：设置边框的宽度
- border-style
    * none：无边框，与任何指定的border-width无关
    * hidden：隐藏边框
    * dotted：边框为点线
    * solid：边框为实线
    * dashed：边框为虚线
    * double：边框为双边框
#### 列表
- list-style ：设置列表相关内容
    * list-style-image:none/url
    * list-style-position
        * outside：列表标记放置在文本以外，且围绕文本不根据标记对齐
        * inside：列表标记放置在文本以内，且围绕文本根据标记对齐
    * list-style-type:设置列表所用的标记，若list-style-image属性为none或指向图像不可用时，list-style-type将发生作用。仅作用于具有display值等于list-item的对象（如li对象）。
#### 表格
- border-collapse
    * separate :边框独立（标准html）
    * rtl：相邻边被合并
- table-layout
    * auto：默认的自动算法。
    * fixed：固定布局的算法。
#### 其他
- cursor ：设置在对象上移动的鼠标是否采用预定的光标形状，常用在a标签。

## 选择器
- 类型选择器
    - 示例
        ```
        a { text-decoration:none; } 
        ```
- 包含选择器
    - 
    ```
    div span {
        ...
    }
    // 查找div下的span
    ```
- id选择器：#
- 类选择器：.
- 选择符分组（多选）
    * 
    ``` 
    .h1,.h2,div span{
        ...
    }
    ```
## 伪类
- :link 用于设置a标签在未被访问前的样式属性，默认值由浏览器决定
- :hover 用于设置对象在鼠标悬停时的样式属性
- :active 用于设置对象在被用户激活(在鼠标点击与释放之间发生的事件)时激活的样式属性
- :visited 用于设置a标签链接地址已被访问的样式属性
- :first-child
    ```
    p a:first-child{
        ...
    }
    ```
    设置p的第一个a标签的样式属性
## 伪对象
- :before
    ```
    span:before{
        content: 这是内容
    }
    ```
- :after
    ```
    span:after{
        content:这是内容
    }
    ```
    设置span在对象前发生的内容
- :first-letter 设置对象内的第一个字符的样式表属性。
    ```
    a:first-letter{
        color:red
    }
    ```
- :first-line 设置对象内的第一个行的样式表属性。
    ```
    div:first-line{
        color:green
    }
    ```
## 规则
- @import url('相对或绝对路径指定导入样式列表文件')
    ```
        @import "print.css"
        @import url("foo.css") screen, print;
    ```
- @font-face
    ```
    @font-face{
        font-family:name;src:url(...);
         font-weight: bold;
    }
    ```
- @media 媒体查询
    ```
    // 设置显示器用字体的尺寸
    @media screen{
        BODY{
            font-size：12px
        }
    }
    ```
# 总结知识点
## 知识点
1、横线布局我们优先选择浮动，虽然定位任何布局都能解决问题，但是也有很多问题，通过浮动，我们可以清除行内元素的间隙，而且盒子的外边距不影响其他盒子。   
2、定位一定要遵循‘子绝父相’。（子类想要使用绝对定位，一定要在他的父类写上相对定位，不然子类移动的参考物就是更上级的相对定位，如往上走一直没有相对定位，则以body作为参考物）
- 如果定位了，没有设置top、left等这些控制位置的属性，默认会按照他原本在标准流的位置呈现   

3、对齐方式   
* 块级元素水平对齐方式(margin:0 auto)   
* 文本排列方式(text-align:center/left/right) 默认left

4、行高属性
- line-height 行高=字体大小+上间距+下间距
5、选择器优先级
- 优先级的顺序：!important > 行内样式 > id > 类 > 标签 > 继承

5、可以被继承的属性 
```
color ， font- ， text- ，line-，cursor
```
6、元素
- 块级元素block(div/p/h标签等)   
( 1 ) 独占一行   
( 2 ) 默认宽度和父元素一样宽   
( 3 ) css设定的宽高有效   
- 行内元素inline(span/a/em/strong标签等)   
( 1 ) 不会独占一行，并列排列   
( 2 ) 宽度由内容决定   
( 3 ) 在css设定的宽高无效   
- 行内块级元素inline-block(img标签等)   
( 1 ) 不会独占一行   
( 2 ) 可以设置宽高且有效

6.1、元素的模式转换   
- display:block (把某个元素显示修改为块级模式，而且在img标签上设置之后，可以除去图片默认的3px间隙)
- display:inline (把某个元素显示修改为行内模式)
- display:inline-block (把某个元素显示修改为行内块级模式)

7、元素的隐藏方法
- display:none 不显示，既看不见也不占据位置
- visibility:hidden 隐藏,虽然看不见,但是还是占据位置
- visibility:visible 可见(visibility的默认属性)

8、border-collapse: collapse 
- 让表格的单元格之间的间距变没有，并且把表格的边框重叠在一起

9、包含塌陷
- 如果直接给子元素设置margin-top，这个时候，子元素位置改变了，但是有可能会把父元素的也一起带跑了
    - 解决方法：   
    （1）给父元素加上border   
    （2）给父元素加上 overflow:hidden
10、浮动
- 特性：
    - 浮动元素不会占据标准流的位置（脱标）
    - 浮动的元素默认会以`行内块级元素`的形式展示
    - 浮动的元素在元素的顶端对齐
- 影响：
    - 所有的子元素浮动起来之后，因为脱离标准流，不占据位置，会导致父元素的高度变成0，布局变乱。   
    `解决方法`：清除浮动   
        - 给父元素直接设置高度
        - 给父元素设置overflow：hidden
        - 使用单伪元素清除浮动
        ```
        父元素::after {
            content:"";
            display:block;
            clear:both; 
        }
        ```
        - 使用双伪元素清除浮动（重点掌握这种）
        ```
        父元素::after,父元素::before {
        content:"";
        display:block;
        clear:both;
        }
        ```
11、overflow属性
- visible默认值
- auto 如果超出，就隐藏起来，然后会出现滚动条
- hidden 如果超出，就把内容隐藏起来，不出现滚动条
- scroll 不管超出没超出，都显示滚动条

12、四种定位方式
- 静态定位static(默认值)
- 固定定位foxed
    - 脱离标准流不占据位置
    - 改变原有的显示模式
    - 每次设置位置，相对于整个浏览器来说 -- 定位基准：浏览器定位就是让某个元素固定到某个位置
- 相对定位relative
    - 没有脱离标准流，还是回占据标准流的位置
    - 没有改变显示模式
    - 定位基准是他原来的位置
    - 一般用于搭配absolute来使用(作为父级，参考物)
- 绝对定位absolute 
    - 脱离标准流模式，不占据原来的位置
    - 改变了元素的显示模式
    - 定位的基准是：如果前代没有设置定位，绝对定位的基准参考物是body

13、盒子的居中方式
- 先跑父元素高度的50%，再回跑自己宽度的50%
- 定位先跑父元素高度的50%，然后translate(-50%,-50%)

14、控制鼠标样式
- 常用样式：cursor:pointer （小手）

15、去除外轮廓线
- outline:0 none

16、去掉图片的边框的写法
- border:0 none

17、文本超出控制
- white-space:控制是否换行显示的值：   
    - normal 默认值，普通模式
    - nowrap 不换行，在一行显示所有的内容
- text-overflow:超出的文字是否显示省略号或直接裁切
    - clip 直接裁切 默认值
    - ellipsis 显示省略号
- 效果例子：
    ```
    white-space:nowrap  //设置一行显示
    overflow:hidden //超出隐藏
    text-overflow:ellipsis //设置省略号
    ```
