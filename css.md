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
    * absolute: 将对象从文档流中拖出，使用left、top、right、bottom等属性进行定位。而其叠层通过z-index进行定义。此时对象不具有边距（以relative作为父级进行移动,如没有则以此往上）
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