---
title: BFC
categories:
- CSS
tags:
- 渲染
---
BFC 是 Block Formatting Context 的缩写，中文可以翻译成块级格式化上下文。在解释 BFC 之前，我们有必要先了解一些有关 CSS 布局的基本概念。

## 1 块级元素
w3.org 中的描述：
>Block-level elements are those elements of the source document that are formatted visually as blocks(e.g., paragraphs). The following values of the "display" property make an element block-level: "block", "list-item", and "table".

翻译成中文大概的意思是，块状元素是源文档在被可视化布局时，其中被可视化为块的元素。将元素的 display 属性设置为 “block”、”list-item” 或者 “table” 都可以将元素转化为块状元素。

## 2 块级盒子
w3.org 中的描述：
>Block-level boxes are boxes that participate in a block formatting context. Each block-level element generates a principal block-level box that contains descendant boxes and generated content and is also the box involved in any positioning scheme.

翻译成中文大概的意思是，块级盒子是参与块级格式化上下文的盒子。每一个块级元素都会生成一个包含它后代盒子和生成内容的主要块级盒，并且这个盒子参与了任何定位计算。
也就是说，块级元素会自动生成一个块级盒子。

## 3 BFC
w3.org 中关于 BFC 的描述：
>Floats, absolutely positioned elements, block containers (such as inline-blocks, table-cells, and table-captions) that are not block boxes, and block boxes with "overflow" other than "visible" establish new block formatting contexts for their contents.

>In a block formatting context, boxes are laid out one after the other, vertically, beginning at the top of a containing block. The vertical distance between two sibling boxed is determined by the "margin" properties. Vertical margins between adjacent block-level boxes in a block formatting context collapse.

>In a block formatting context, each box's left outer edge touches the left edge of the containing block (for right-to-left formatting, right edges touch). This is true even in the presence of floats (although a box's line boxed may shrink due to the floats), unless the box established a new block formatting context (in which case the box itself may become narrower due to the floats).

翻译成中文大概是：
1. _浮动元素_，_绝对定位元素_，_不是块级盒子的块级包含块_（比如 inline-block、table-cell、table-caption）和 _overflow 值不是 visible 的块级盒子_，都会建立一个新的块级格式化上下文。

2. 在一个块级格式化上下文中，盒子从包含块的顶部开始，垂直地一个接一个的排列，相邻（如果相邻的是父元素，那么也会折叠）两个盒子之间的垂直间距由盒子的 margin 属性值决定，在一个块状格式化上下文中相邻的连个块级盒子之间的垂直 margin 是折叠的。
需要注意的是，参与 BFC 布局的只有普通流 normal flow 中的块级盒，而 float 和绝对定位的元素虽然可以创建自己的 BFC，但是它们不属于普通流（浮动元素和绝对定位元素会脱离普通流），不参与包含它们的 BFC 的布局，同样也不会与其相邻元素（相邻元素是父元素也算）的 margin 进行折叠。

3. 在一个块级格式化上下文中，每个盒子的左外边接触包含块的左边，即使在浮动元素参与的情况下也是如此（浮动元素会覆盖这个盒子），除非这个盒子新建了一个块级格式化上下文。

目前为止，我们只知道怎么样会产生 BFC，以及 BFC 中的布局规则是什么，那么什么是 BFC 呢。

BFC 是 W3C CSS 2.1 规范中的一个概念，它是一个独立的布局环境，如果一个元素参与了 BFC，或者说这个元素拥有一个 BFC，那么这个元素内部元素如何布局定位，以及这个元素与其它元素的相互作用都要符合 BFC 的规则。

BFC 可以理解为一个箱子，箱子内部的元素再怎么翻江倒海都不会影响到箱子外面的元素，反过来也是一样，箱子外面的元素也不会影响箱子里面的元素。

整理一下 BFC 的布局规则：
1. 在 BFC 下，内部的 box 会在垂直方向上一个接一个地放置
2. box 垂直方向的间距由 margin 决定，属于同一个 BFC 的两个相邻 box 的 margin 会发生重叠
3. 在 BFC 中，每一个盒子的左外边缘会触碰容器的左外边缘
4. BFC 的区域不会与 float box 重叠（自适应两栏布局）
5. 计算 BFC 的高度时，浮动元素也参与计算（解决浮动塌陷）

最后两条实际上是利用 BFC 是独立布局区域，不影响其它元素也不受其它元素影响的特性。虽然浮动元素不参与 BFC 内布局，但是仍然是 BFC 中的一部分）

本文参考
【1】[深入理解BFC](http://www.imooc.com/article/9723)
【2】[Visual formatting model](https://www.w3.org/TR/CSS21/visuren.html#floats)
【3】[BFC 神奇背后的原理](https://www.w3ctech.com/topic/865)
【4】[什么是BFC](http://web.jobbole.com/84808/)
