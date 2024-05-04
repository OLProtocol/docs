资产发行模式
====


SAT20资产的发行有三种主要模式，主要根据这两个参数进行调节：
selfmint：是否只能自己铸造
block：可以铸造的区块高度区间


项目方主导
----
selfmint: true
block: 一般不设置

这种模式下，只有持有deploy这个nft的地址才能mint。
这种模式下，资产将由项目方完全持有。比如稳定币，一般都是由项目方铸造。


公平发射
----
selfmint: false (或者不设置)
block: start-end （必须设置）

这种主要由社区主导的发行模式，主打社区成员公平铸造。比如设置block的范围。
在这种模式下，在deploy完成之后，必须经过1000个区块才能开始mint，在1000个区块之内的mint无效。


无限制
----
selfmint: false (或者不设置)
block: 一般也不设置

这种模式下，mint被其他因素制约，不可能无限制mint，具体制约条件，由项目方设置。
比如，要求在某种稀有聪或者某个ticker上继续铸造。


我们期望通过这种模式的设置，让参与者能清楚知道，参与的项目是哪一种类型的项目。