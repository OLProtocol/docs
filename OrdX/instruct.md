指令
====



OrdinalsX协议参考了Atomicals协议和BRC-20协议，理念上跟Atomicals协议更接近，实现上跟BRC-20协议更接近。  

OrdinalsX协议只有deploy和mint指令，不需要transfer指令。基本原理是每一个token都是绑定在一个sat上，转移sat也就意味着转移了token，所以不需要额外的账本记录token的转移历史，也不需要在转移之前铭刻transfer指令，这解决了BRC-20的问题。因为最小utxo的限制，一个utxo至少有546个sat，也就有546个token，要拆分单独的token难度比较大。这个问题我们的解决方案跟Atomicals不同，放在后面讨论。


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


例如：
{   
  "p": "ordx",  
  "op": "deploy",  
  "tick": "satoshi",  
  “block”: "830000-833144",  
  "lim": "10000"  
}  
  
在普通情况下，OrdinalsX跟BRC-20协议类似，通过铭刻deploy指令来部署token。不同的是没有供应量的限制，而是指定mint的有效区块高度。在这个高度之内mint的所有token都有效。另外一个不同的地方，deploy时可以声明具备特殊属性的sat才能mint：reg和rarity是用来对sat的属性做规定的。可以发现，OrdinalsX协议除了用于发行普通的token之外，还可能发行特殊的token，仅有特殊的sat才能mint出来。这个特性是为了挖掘sat的独特价值。


mint
----

| KEY   | Required | Description   |
| :------- | :------: | -------: |
| p	| Yes | 协议名称: ordx |
| op | Yes | 指令: deploy, mint |
| tick | Yes | 名称: 只允许3或5-16个字符，（为brc-20保留4个字符） |
| amt | Yes | mint得到的token的数量，不能超过deploy时指定的lim |
| sat | Yes | 指定sat的序号 |

mint时，需要根据deploy声明的规则做检查：检查当前utxo中的sat，看看是否满足规则:  
1. sat：指定这次mint应该从哪个sat开始，该sat后面需要有amt个连续序号的sat，才能mint成功。
2. deploy的规则”block“：该次mint的block高度是否在deploy的规定之内。
3. deploy的规则”lim“：该次mint的amt小于等于lim。
4. deploy的规则”reg“：如果有设置，需要检查该sat的序号是否符合正则表达式reg。
5. deploy的规则”rarity“：如果有设置，检查该sat是否是这种类型。这种类型只允许amt为1.
如果不满足以上规则，就不允许mint。即使使用工具强行mint，钱包也可以自主检查是否满足deploy的规则自行验证。  



upgrade
----
将其他协议的FT升级到OrdinalsX，只能单向升级。以后扩展。
