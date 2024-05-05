序数
====

SAT20使用的序数，是严格按照聪的出生顺序来决定的，严格保证一一对应，这意味着，在有效范围内，每一个序数都对应一个聪，每一个聪都对应一个序数。这种严格的一一对应关系是永久不变的。该序数基本原则：
1. 第一个聪的序数为0
2. 按照出生顺序递增编号，没有空缺。（Ordinals的序数存在空缺））
3. 聪的转移遵循先进先出原则。
4. 在奖励交易中，奖励聪做为第一个输入，其他交易的费用按顺序排在后面。
5. 奖励聪的数量严格按照实际奖励数量。 （Ordinals的奖励聪数量按照理论数值）

SAT20协议早期使用Ordinals协议，利用了Ordinals协议提供的序数理论和铭刻功能。但是Ordinals协议在聪不可销毁这件事上有不同的原则，所以最终我们选择独自发展自己的序数理论，这可以看作是对Ordinals协议的一种分叉，依旧是属于Ordinals协议的一种。SAT20完全支持Ordinals NFT，可以认为Ordinals NFT就是SAT20 NFT，两者之间没有本质区别。

（具体背景请参考github issue：https://github.com/ordinals/ord/issues/3690#issuecomment-2083950493 和 https://github.com/ordinals/ord/issues/3702#issuecomment-2081429205）
