
# 編輯器之神

- template: post.html
- pubdate: 2009-07-24
- tags: Vim

----

最初的时候我一直使用 [Editplus](http://www.editplus.com/)，这是一款轻量级，
效率极高，可配置性稍强的编辑器，而且有内嵌的(IE6)浏览器内核，
使用快捷键 <Ctrl-b> 就可以在 html 代码和预览效果之间快速切换，
甚至可以无需保存html 文件到指定磁盘位置（默认保存在浏览器临时目录）。
我仍然很喜欢 Editplus，但是不经常用了。

后来使用的 [Eclipse](http://www.eclipse.org/) 在项目管理和强大的插件支持下，
如神器一般。这是一个足够伟大的IDE，不过如果单纯的作为编辑器来用，就有点大材小用了。

最后，就是 [Vim](http://www.vim.org/) 了，Vim 和 Emacs 两款编辑器我都试用过，
最开始不理解多模式，没有适应这种使用习惯，心想：这是什么破编辑器！？

来来回回丢弃过几次，后来有一次不小心心智大开，迅速的习惯了多模式编辑，
并从此爱上了 Vim，经过一段时间的学习和练习，更是无法自拔。

上面三款编辑器如此优秀，Vim更有神器的美称，但即使是神器也有美中不足之处。
下面是我期待中的编辑神器的主要功能点。

* 代码着色
* 现代化的代码折叠方式
* 大纲视图
* 代码压缩与格式化
* 文本比较
* 文本书签
* 文本拖放
* 多模式编辑
* 内联搜索模式
* 在滚动条或附近使用彩色条纹标识状态
* 自动识别文件编码
* 可扩展
* 项目管理支持
* 二进制编辑支持
* 代码着色
    基本上现在的编辑器都支持代码着色，虽然使用方式各不相同，
    但是使用效果基本可以达到一致，没什么要挑剔的。不过 Vim 的配色模式不错，
    另外应该提供导入到处配色模式。
* 现代化的代码折叠方式
    代码折叠是一项如此受人喜爱的创造发明，不支持代码折叠你都不好意思更人打招呼。
    不过 Editplus 和 Vim 的代码折叠方式比较原始，默认情况下只识别缩进后的文本/代码，
    而且Vim左边的折叠按钮更是土到掉渣。
* 大纲视图
    Eclipse精于此道，自带的大纲视图对 Java，C++，PHP 等支持都很好，
    而 Aptana 对 Javascript 的大纲视图更是令人称道。
* 代码压缩与格式化
    Vim的代码格式化做的很不足，有很多时候格式化不到位。Eclipse及其插件做的比较完美。
* 文本比较。<br />
    Vim 和 Eclipse 都做的很好。
* 文本书签<br />
    要在大段、篇幅很长的文本/代码中跳跃阅读，并能轻松回到原来的位置上，
    书签就显得尤为重要。Vim 的 mark 插件对文本书签支持的很好。
* 文本拖放<br />
    在不想使用复制/剪贴影响剪贴板内容的情况下很有用。
    不过 Vim 默认不支持，Editplus 和 Eclipse 做的很好。
* 多模式编辑<br />
    Vim 和 Emacs 的多模式编辑，舒适到不行。
* 内联搜索模式<br />
    Vim 的内联搜索模式是如此的浑然天成，并且支持强劲的正则表达式匹配模式。
* 在滚动条或附近使用彩色条纹标识状态<br />
    Eclipse的全局搜索，Chrome浏览器的搜索，Beyond Compare 2的文本比较，
    都有在恰当的位置标识出所有结果集在编辑器的全局大体位置，
    使用滚动条拖放到某位置，即可看到对应的搜索结果。
* 自动识别文件编码<br />
    Ediplus 做的最为精湛，Vim 也有一个不错的插件支持。
* 可扩展<br />
    Eclipse 和 Vim 的扩展性较强。
* 项目管理支持<br />
    作为 IDE，Eclipse 当然表现强劲。Editplus 也有一个原始的项目管理功能。
    编辑器本身可以没有项目管理功能集成，这个可以交给更专业的项目管理软件来做，
    编辑器可以实现某些接口来集成或挂载项目管理功能。
* 二进制编辑支持<br />
    一般人并不常用，如果在不影响前面的功能和编辑器效率的情况下，
    加上这个功能也未尝不可。

如果我们有一个编辑器，他启动像 Editplus和Vim一样迅捷，
使用Eclipse或类似的现代代码折叠方式，有Eclipse那样成熟的大纲视图、
代码压缩工具和文本比较功能，像 Vim一样的多模式编辑和内联搜索模式，
支持如Perl一般的正则表达式匹配模式，并将搜索结果集在文档全局中对应的位置
在恰当的位置（如滚动条底带）呈 现，支持文本书签，另外有像Eclipse一样，
或更好的更专业的项目管理工具支持，这将是怎么一款伟大的现代编辑器。