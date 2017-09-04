
# 不缓存 CDN 静态资源方案

- template: post.html
- pubdate: 2013-09-21
- tags: Web Design, CDN

----


## 背景

支付宝目前使用淘宝提供的 CDN 服务，这个服务中的 CDN 节点在自身找不到对应资源时
主动到源服务器拉取的策略。

![图](/images/no-cache-in-cdn.png)

支付宝使用的静态资源合并(combo)方案，导致在不同的访问参数情况下，被认为是不同
的静态资源。如果挟带的是避免缓存的随机参数，CDN 在没有缓存这个资源的情况下，
会到源服务器拉取资源。

原则上，我们使用特定的版本机制，每个新版本文件以不同的文件名发布，不允许使用
参数，尤其是随机数方式避免缓存问题。


## 问题

由于我们使用的版本策略，我们可以指定用户缓存静态资源时效为永久，实际方案上
我们指定用户缓存时间为 1年，但是在某些场景下（如测量用户网络速度），
用户客户端（非 CDN 节点）访问某些特定静态资源需要禁止使用缓存。

目前常见的方案都是在客户端使用时间戳+随机数。这个方案本身看似没什么问题，但是
实际上有非常大的隐患，测量的数据参考性也不佳。

* CDN 节点上缓存了大量挟带永不重复随机数的资源，对磁盘造成影响。
* CDN 缓存命中率降低，这些挟带随机数的静态资源缓存率命中率为 0。
* 增加源服务器的访问压力。
* 测量的用户网络响应时间实际不是到 CDN 节点的，还包含 CDN 回源的时间。

<!--more-->

## 解决方案

为了解决这种明确不允许用户客户端缓存，同时又不建议使用随机参数访问的需求，我们
有以下几种方案：

1. CDN 服务器端控制浏览器不缓存。『最佳方案』

   设置指定目录下的静态资源禁止缓存头信息，有需要禁止缓存需求时上传静态资源到
   这个目录。

2. 直接访问源服务器。

   现在的加随机数访问 CDN 方案和直接访问源服务器本质上相同，这方案只能测用户到
   源服务器的响应时间。

3. 使用有限随机数方案。

   虽然第一种是最佳方案，但也不排除某些浏览器或壳在不关闭页面情况下，有缓存的
   问题，所以这和第一种方案结合使用可能是更靠谱一些的方案。『待验证』

   页面脚本请求静态资源时，带上从零递增的参数，避免单页面缓存问题，亦可避免
   CDN 缓存大量无意义资源的问题。


## 延伸

实际上，对于静态资源来说，纯粹的参数是无意义的，CDN 节点本可以忽略这个参数。
虽然合并策略使用了参数方式，但是我们使用双问号激活合并服务的方案可以让我们
明确区分出合并参数和其他参数，因此技术上是完全可以忽略其他参数导致的回源。

## 参考

1. [拉取式相比推送式的对比的参考](http://segmentfault.com/q/1010000000119794)