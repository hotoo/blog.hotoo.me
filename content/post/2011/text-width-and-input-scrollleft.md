
# 文本宽度 及 文本框滚动偏移量(scrollLeft)

- template: post.html
- pubdate: 2011-11-07
- tags:  Web Design

----

## 背景

最近将多标签输入框进行修改，把原来随光标(caret)移动的自动建议浮动条改为根据当前标签相对左对齐。

http://1.bp.blogspot.com/_POl6bUDELqY/SRQ_xx7LXCI/AAAAAAAAFSw/syXjnAQ-RLI/s320/tags.jpg

解决方法很简单，计算当前标签前的文本宽度(将需要计算的文本转义后放入一个各字体样式与目标输入框相同的容器，
如span中，span.offsetWidth即是文本的宽度。注意：文本框中，中文半角空格的宽度和英文半角空格的宽度显示为不同，
虽然这两个空格本质上相同)，浮动条根据该值定位即可。

## 问题

当标签文本过长，超出文本框宽度时，标签文本会向左滚动，但是此时当前标签前面的文本宽度不变，
定位浮动条时需要减去文本向左滚动的尺寸。

网页文档对象中，元素都有一个可读写的scrollLeft属性，表示元素内容相当元素容器向左移动的偏移量。

但是 Firefox 和 Opera 有一些例外，如文本框的 scrollLeft 始终为 0，
[https://developer.mozilla.org/En/DOM/Element.scrollLeft Mozilla] 的描述是：

> If the element can't be scrolled (e.g. it has no overflow), scrollLeft is set to 0.

对于一些不可滚动(scroll，即没有溢出)的元素，scrollLeft始终为0。而单行文本框
（在Gecko引擎看来）是不可滚动的，即使将样式指定为 `overflow:scroll`
（IE会出现水平和垂直滚动条这样的怪胎）。

虽说单行文本框是不应该出现滚动条这样怪异的形态，但是这不表示它是不可滚动的，
当文本宽度大于文本框宽度时，（为了将光标caret显示在文本框可见区域）文本势必向左滚动，如图：

http://3.bp.blogspot.com/_POl6bUDELqY/SRQ2rw-JdEI/AAAAAAAAFSo/hY8HxHGQk0Q/s320/scrollLeft.jpg

## 解决办法

对于文本框不支持scrollLeft的浏览器，一个临时的解决办法是，在文本宽度大于文本框宽度时，
浮动条定位在相对文本框后端若干像素（便于输入）的位置，在增量输入时，体验不是太差，
但是在光标向前移动使文本向右滚动时，就会出现偏差。

最终解决办法是期待浏览器能够得到正确的scrollLeft值，或者其他巧妙的计算方法。
