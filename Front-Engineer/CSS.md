## CSS position 属性 指定元素的定位方式

  

static、relative、absolute、fixed 和 sticky

  

static: 默认值,元素会按照文档流中的正常位置进行排列，不受 top、right、bottom 或 left 值的影响。

  

relative: 相对定位, 元素相对于自己在文档流中的原始位置进行定位，可以通过设置 top、right、bottom 和 left 来调整元素的位置。相对定位不会影响文档流中其他元素的位置。

  

absolute: 绝对定位, 元素相对于最近的 relative 或 absolute 定位的父元素进行定位（如果没有，则相对整个文档）。使用 top、right、bottom 和 left 来指定位置,

  

fixed: 固定定位, 元素相对于浏览器窗口进行定位，即使页面滚动，元素依旧保持在固定位置。可使用 top、right、bottom 和 left 控制位置

  

sticky: 粘性定位, 结合 relative 和 fixed 的特性，元素在其父容器中滚动到指定的偏移位置时变为固定定位。需要设置 top、right、bottom 或 left。

  

## CSS display 属性 指定元素的显示类型

  

- none：元素不显示，且不占据任何空间。

- block：元素显示为块级元素，占据一整行空间。

- inline：元素显示为内联元素，不会换行，只占据自身内容的空间。

- inline-block：元素像内联元素一样不换行，但可以设置宽高。

- inline-grid: 它将元素显示为内联元素，并赋予它网格容器的布局特性。

- inline-flex: 它将元素设置为内联显示，并赋予**弹性布局（flexbox）**的特性。

- flex：将元素变为一个弹性容器，可对子元素进行弹性布局。

- grid：将元素变为网格容器，可对子元素进行网格布局。

- table：将元素呈现为类似表格的布局。

  

## 最大宽带

  

max-w-6xl mx-4 lg:mx-auto 设置宽带为 6xl

  

#### 为什么 Image 使用 div?

  

div 的 classname+Image 的 className='object-contain'

  

#### 为什么 Header 多个 div

  

如果只用一个 div, max-w-\*\* 下边框会两边中断, 两个 div 一个设置 header 属性,其他设置宽带和子元素的属性;

  
  

#### grid实现分列

grid-cols-1  默认一列;

md:grid-cols-3   middle size: 变成3列;

子元素1:

md:col-span-2   md: 占两列;

  

子元素2:

hidden md:col-span-1 md:inline-grid

  

#### Image为什么不能用在stories里面, pravatar的图;

会报错, 只能用img标签;


