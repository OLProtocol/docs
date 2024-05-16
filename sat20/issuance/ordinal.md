序数
====

SAT20严格按照聪的出生顺序来给聪编号的，严格保证**编号和聪一一对应并且从0递增**。这意味着，在有效范围内，每一个序数都对应一个聪，每一个聪都对应一个序数。这种严格的一一对应关系是永久不变的。该序数的基本原则：
1. 第一个聪的序数为0。
2. 按照出生顺序递增编号，没有空缺。
3. 聪的转移遵循先进先出原则。
4. 在奖励交易中，奖励的聪做为第一个输入，其他交易作为费用的聪按顺序排在后面。
5. 奖励数量与实际奖励数量严格相等。

SAT20的序数理论脱胎于Ordinals协议，但是跟Ordinals协议有原则上的不同，其核心区别在于Ordinals协议认为聪是可以销毁的，另外一个不同是Ordinals协议按照理论给聪编号，导致有很多的序数背后并没有实际的聪对应。

SAT20完全支持Ordinals NFT，主要原因是因为Ordinals NFT是一种绑定在聪上的资产，符合SAT20资产的定义，也就是说Ordinals NFT也是一种SAT20资产。

（具体背景请参考github issue：https://github.com/ordinals/ord/issues/3690#issuecomment-2083950493 和 https://github.com/ordinals/ord/issues/3702#issuecomment-2081429205）

（备注：ordinals理论现在已经有了正式的BIP编号，正式进入考察流程。Ordinals理论成为BTC标准的可能性非常的高。最终Ordinals理论使用的编码方案，都会成SAT20的编码方案。具体参考：https://github.com/bitcoin/bips/pull/1408 ）