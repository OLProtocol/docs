指令
====



ordx协议参考了Atomicals协议和BRC-20协议，理念上跟Atomicals协议更接近，实现上跟BRC-20协议更接近。  

ordx协议只有deploy和mint指令，不需要transfer指令。基本原理是每一份资产都是绑定在一个sat上，转移sat也就意味着转移了资产，所以不需要额外的账本记录资产的转移历史，也不需要在转移之前铭刻transfer指令。


deploy
----

| KEY | Required | Description |
| :---: | :---: | :------- |
| p	| Yes | 协议名称: ordx |
| op | Yes | 指令: deploy |
| tick | Yes | 名称: 只允许3或5-16个字符，（为brc-20保留4个字符） |
| lim | No | 每次mint的token的限额，默认是10000。如果deploy特殊sat上的token，默认是1。 |
| selfmint | No | 默认是false；设置为true，只有持有该ticker的地址才能铸造（父子铭文） |
| block | No | 没有总量限制，但是有mint的开始高度和结束高度（开始-结束）。|
| attr | No | sat的属性要求，比如"rar=uncommon;trz=8"，可扩展。 |
| des | No | 描述内容 |


例如：  
{   
  "p": "ordx",  
  "op": "deploy",  
  "tick": "satoshi",  
  “block”: "830000-833144",  
  "lim": "10000"  
}  

attr是一个可以扩展的属性，目的是让越来越多特殊的sat可以通过这个属性被筛选出来。目前支持的属性有：
1. rar：稀有度，在Ordinals中定义：common, uncommon, rare, epic, legendary, mythic 
2. trz：trailing zeros，尾部为零的数量，比如trz=8，说明该sat的编号的尾部有8个零  
如果你有什么好主意，或者发掘了什么特殊价值的sat，可以提交代码给我们。  

通过deploy指令，我们可以发现，ordx跟其他协议的不同主要体现在这几个方面：
1. 一个sat绑定一份资产
2. 没有供应量的限制，而是指定mint的有效区块高度。在这个高度之内mint的所有token都有效。
3. 通过父子铭文的方式支持项目方全盘控制。
4. 可以指定具备某种属性的sat才能mint，也就是资产只能绑定在特殊属性的sat上。



mint
----

| KEY | Required | Description |
| :---: | :---: | :------- |
| p	| Yes | 协议名称: ordx |
| op | Yes | 指令: mint |
| tick | Yes | 名称: 只允许3或5-16个字符，（为brc-20保留4个字符） |
| amt | No | mint得到的token的数量，默认等于lim，不能超过lim |
| sat | No | sat的序号，设置了attr属性的ticker，mint时需要提供满足条件的sat |


例如：  
{  
  "p": "ordx",  
  "op": "mint",  
  "tick": "satoshi"  
}   

每次mint时，需要做的通用检查：
1. 协议必须是ordx
2. op必须是mint
3. tick必须已经部署过
4. amt小于等于deploy的规则“lim”
5. 如果有deploy的规则“selfmint”：只有持有ticker的地址才能mint（父子铭文）
6. 如果有deploy的规则”block“：该次mint的block高度要在规定之内
7. 如果有deploy的规则“attr”：mint时必须提供sat这个参数，并且根据attr对该sat做检查：
    * 如果有rar属性：检查该sat是否是这种类型
    * 如果有trz属性：检查该sat的序号是否有足够的尾数零

不满足以上规则，就不允许mint。即使有工具强行mint，ordx的indexer也会判定无效。钱包可以独立对每个token做验证，通过Ordinals协议的indexer和Deploy指令的数据就可以直接验证。




upgrade
----
将其他协议的FT升级到ordx，主要支持brc-20。以后扩展。例如：   

{   
  "p": "ordx",  
  "op": "upgrade",  
  "tick": "ordi",  
  "amt": "1000",  
  "org": "brc-20",  
  "cfactor": "1"  
}  

可选方案：
通过OLDEX协议锁定到闪电网络通道中，在提款时直接转换成ordx资产并销毁老token。  

