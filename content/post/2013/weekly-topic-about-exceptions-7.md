
# 每周异常：第 7期，保持简单，保持拙朴

- template: post.html
- pubdate: 2013-08-28
- tags: 每周异常

----

## 副标题：如何简单有效的发现最重要的有效异常

> Keep It Simple, Stupid.
>
> -- U.S. Navy (1960)

在这之前，我一直苦苦寻求牛逼的算法 [#12](https://github.com/totorojs/javascript-exception-archives/issues/17) ，
来解决这个看似简单，其实不易；仿佛不易，最终简单的问题：
找出最重要的有效异常。

最早的时候，我们定义了『一个异常』由以下核心部分组成：

* URL: 异常所在页面。
* File: 异常代码所在文件。
* Line: 异常代码所在行数。
* Message: 异常消息。

这些是不变的，相同页面中，同一个异常代码文件同一行，异常消息相同的异常，我们可以近似的认为它是同一个异常。

<!--more-->

另外还定义了异常率：

* 异常率(PV)：『一个异常』的 PV，除以这个异常所在页面的 PV。
* 异常率(UV)：『一个异常』的 UV，除以这个异常所在页面的 UV。

于是我们通过 URL, File, Line, Message 四个核心信息来统计每一个异常的 PV, UV, PV异常率，UV异常率。
并按照其中的某个字段为主进行排序。

但是得到的结果总是让人不尽如人意，总会有很多无法排查，甚至还有一些显然不是我们代码的问题的异常排前排。

我们尝试限制异常 PV, UV 的基数，尝试限制页面 PV, UV 的基数，结果仍然不理想。
而且也没有想出其他牛逼的权重算法来评估每个异常。

我们想过异常是跟代码所在文件和行号、异常消息有关系的，跟页面 URL 的关系不那么强，因为公共代码会在很多页面使用，把这同一个异常分散算到不同页面中会严重影响这个异常的排名。

但是实际上公共代码（尤其是基础类库）的异常很多情况下是业务系统调用不当，或者使用的版本有 BUG 导致，最终还是需要这个页面的开发者调整调用方法，或升级使用更新的公共脚本来解决。所以忽略或弱化异常所在页面是不可接受的。

而且排除了异常所在页面的信息，对于排查异常来说更为困难。

够了，我已经受够了，脑袋一片浆糊。
累、困，早点回家睡觉。

----

回到家随手画了几笔，然后去洗澡。洗澡的时候想着刚刚画的思维草图，逐渐想清楚了很多。

* File: 由于是 seajs 自动管理依赖，以及 combo 的使用，异常所在文件本身具有不稳定性。
* Line: 由于上面 File 的原因，不仅仅是 HTML 代码中的异常行号不稳定，静态脚本异常行号也具有不稳定性。
* Message: 不同浏览器（包括不同版本，或者在不同操作系统中）对同一个异常有不同的消息反馈，另外还有本地化的原因，异常消息也具有不稳定性。

最后，只有异常所在页面 URL（或者页面 ID，一个页面源文件可能有多个 URL 地址，但是它们是有关系的，ID 相同）才是最稳定的。

----

于是我根据页面 URL 排列出每个页面的异常 PV, UV, PV异常率，UV异常率。并根据 PV 异常率为主进行倒序排序（每次访问都抛出的异常，比每个用户访问都抛出的异常的优先级更高）于是我们轻易得出了全站异常率最高的页面。

根据这个关键的页面信息，再次查询出每『一个异常』的 PV, UV, PV异常率，UV异常率。

以不变（页面 URL 或 ID），应万变。我们一个个把这些异常大户揪出来，各个击破。即使暂时没有发布解决，我们仍可以轻易识别排除这个已经揪出的异常。

好了，妈妈再也不用操心我的每周异常 TOP 数据分析了。

嗯， [#12](https://github.com/totorojs/javascript-exception-archives/issues/17) 这个 issue 也可以关了。

----

在做静态资源异常监控时，也有类似的经历。

静态资源监控最重要的是发现哪个页面引用了哪个 404资源，尤其是漏发的资源。因此最重要的有两个关联维度：

* 404资源所在页面
* 404资源文件地址

但是引起 404 的场景很多，包括：

* 漏发文件。
* 静态引用地址错误。
* 动态引用地址错误。

其中动态引用是由于动态脚本计算得出的静态资源地址，引发的 404 非常频繁，多样、而且分布的很散。因此这两个维度的排列组合结果就非常巨大。而且我们的分析系统是基于索引的，这些内容不确定、数量庞大的指标非常不适合用这个系统分析。（我们还有另一个非常时候实时异常分析的系统，这里不做介绍）

因此我们把重心放在更为稳定的页面 URL，只关注出现 404 的页面，至于是什么资源可以直接根据 URL 查询日志，或直接访问这个页面。

## 小结

这篇讲的几个关键内容再强调下：

* 保持简单，保持拙朴。
* 抓住重点，真正的核心重点。

----

终于可以睡了，晚安~