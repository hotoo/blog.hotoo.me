
# 面积分割算法

- template: post.html
- pubdate: 2011-08-25
- tags: 算法

----


做用户点击行为分析的展现时，用了一个透明的层覆盖在页面上，然后覆盖一层 canvas
画布，使用稀疏矩阵算法绘制热点分布图。

预蒙上一层透明蒙版，然后只对需要的区域进行绘制热点图，本是非常不错的方案，我
本机上也一直无问题。但是测试提交了一个 bug，说 IE 下看到点击热点图及轨迹图背后
一片漆黑，我就猜测滤镜问题，最先猜想的是浏览器安全设置导致的滤镜无效，但是又
发现有些类似的图形有没有问题。

结果发现是某些显卡下，IE 中超大面积的区域滤镜会失效。

首先想到的解决办法就是针对 IE 进行切割蒙版，由多个蒙版拼接而成，类似于铺地板。

普通的算法有两种：

1. 将整块蒙版区域划分成多个 2000*2000 的蒙版，最后一列和最后一行不足指数，取余
    设置宽高。
2. 将整块蒙版划分成多个不超过 2000*2000 的等份蒙版。这种算法比较简单，稍微的不足
    之处在于，不能除断的情况，无法等分。

TODO: 有更灵巧的算法么，当然有了，只是我还不知道而已。

## 后来想到

用 canvas 绘制一个透明的区域也未尝不可。
