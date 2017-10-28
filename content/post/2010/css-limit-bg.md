
# CSS 实现有限不确定背景

- template: post.html
- pubdate: 2010-02-20
- tags: CSS

----


2 个嵌套的 html 元素，分别用个两个背景图交替叠加，
形成固定高度，有限、不确定宽度的元件，
或固定宽度，有限、不确定高度的元件（比如实现简单的圆角效果），
要求将有限延伸的背景图放置在内层元素上（如图中 b 区），
避免 b 区的背景图多出的备延伸部分（b' 区）影响到固定的背景图（a 区）的透明部分会被影响。
可以使用外层的 `padding-left` 或内层的 `margin-left` 来处理。