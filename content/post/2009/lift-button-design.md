
# 电梯按钮设计

- template: post.html
- pubdate: 2009-04-08
- tags: UED

----

* 外面选择“上”或“下”的按钮换成“开门”，这样外面也可以中断自动关闭的电梯门，
  并增加选择楼层按钮。这样电梯系统可以预知各个起始楼层和目标情况，
  可以结合历史数据合理调整运转过程，对用户来说，也不必都挤在电梯里忙着（或忘记）选择目标层；
* 选择“上”、“下”以及楼层的按钮可以取消选中。建议如下：当前被选中，则按一下取消选中，否则选中。
  目前有一些稍人性化的电梯可以取消操作，但是要按N下，而一般用户又不知道N等于几？
  其实按一下就够了，不过避免误操作，连续按两、三下取消也可以，并在旁边给出提示；
* 里面保留选择上、下和楼层按钮（用户可以中途改变目标），但是选择楼层的按钮应该放到开、
  关门按钮的下面，方便儿童和残障人士使用（开、关门是自动的，影响不大）。


这个改造成本不知道算不算大，每一层都需要增加选择楼层的按钮，不过这对用户和系统都是有利的，
为电梯系统设计的合理也做了准备。我觉得这是未来电梯的最低配置。
