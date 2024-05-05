指令
====


SAT20资产发行协议只有deploy和mint指令，不需要transfer指令。
指令内容目前支持两种形式，一种是以json文本格式，写入ordinals信封中的body中。另一种是使用压缩的key-value格式，写入metadata中。


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


