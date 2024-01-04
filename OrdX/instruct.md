指令
====



OrdinalsX协议参考了Atomicals协议和BRC-20协议，理念上跟Atomicals协议更接近，实现上跟BRC-20协议更接近。  

OrdinalsX协议只有deploy和mint指令，不需要transfer指令。基本原理是每一个token都是绑定在一个sat上，转移sat也就意味着转移了token，所以不需要额外的账本记录token的转移历史，也不需要在转移之前铭刻transfer指令，这解决了BRC-20的问题。跟Atomicals协议一样，因为最小utxo的限制，一个utxo至少有546个token，要拆分单独的token难度比较大。这个问题我们的解决方案跟Atomicals不同，放在后面讨论。


deploy
----

| KEY   | Required | Description   |
| :------- | :------: | -------: |
| p	| Yes | 协议名称: ordx |
| op | Yes | 指令: deploy, mint |
| tick | Yes | 名称: 只允许3或5-16个字符，（为brc-20保留4个字符） |
| lim | No | 每次mint的限额，默认是1 |
| block | No | 没有总量限制，但是有mint的开始高度和结束高度（开始-结束）。默认是从部署成功开始就可以mint，没有结束。（其他条件限制了mint的可能性）|
| reg | No | 要求该sat的序号满足一定的规则（正则表达式），默认是不设置。比如表示尾部有n个零：^[1-9][0-9]*0{n}$ |
| rarity | No | Sat的稀缺度, 默认是不指定。稀缺度属性：common，uncommon，rare，epic，legendary, mythic。 |
| des | No | 描述内容 |


