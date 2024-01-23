用例
====


我们用下面的几个例子，庆祝协议的发布，并且对先行者致敬。
注意所有通过我们网站进行的交易操作，都会收取一点点的手续费（1000sats或者交易费用的1%），作为支持协议开发和运营的费用。  


东方之珠
----
{   
  "p": "ordx",  
  "op": "deploy",  
  "tick": "Pearl",  
  "block": "828200-830000",  
  "lim": "10000",  
  "des": "The Oriental Pearl."    
}   
我们计划在2024年1月25日正式发布协议，并且部署第一个Token：Pearl。  
大概在2024年2月1日前后开启自由mint，持续到2月10日左右结束（由区块高度828200-830000决定有效的mint时间）。这是ordx协议的第一个token，也是一个meme币，仅供试验，没有价值，不要FOMO。  
   


为了挖掘特殊sat的价值，并且方便这些特殊sat的管理，我们将这些特殊sat归类，并将他们铭刻为某种Fungible Token。这是OrdX协议的特殊能力。 下面是我们预先支持的特殊sat的类型，你可以在我们网站上检查下自己的BTC钱包中是否包含了这些闪亮的宝石（只需要提供钱包地址）。或者你认为哪些类型的sat更有价值，可以为这些sat部署一个响亮的名字。(以下功能需要下个版本才支持)  

矿工的翡翠
----
{  
  "p": "ordx",  
  "op": "deploy",  
  "tick": "Jades",  
  "lim": "1",  
  "rar": "uncommon",  
  "des": "Miner's Jades."  
}  
每个区块的第一个sat才能mint成功，预计每个Jades值1个BTC。


Domo的蓝宝石
----
{  
  "p": "ordx",  
  "op": "deploy",  
  "tick": "Sapphires",  
  "lim": "1",  
  "rar": "rare",  
  "des": "Domo's Sapphires."  
}  
只有rare属性的sat才能mint成蓝宝石，最多只有3437个蓝宝石。目前只有不到400个，预计每个值100BTC。


Casey的红宝石
----
{   
  "p": "ordx",  
  "op": "deploy",  
  "tick": "Rubies",  
  "lim": "1",  
  "rar": "epic",  
  "des": "Casey's Rubies."  
}  
只有epic属性的sat才能mint成红宝石，最多只有32个红宝石。目前只有3个，预计每个值10000BTC。


数字黄金
----
{  
  "p": "ordx",  
  "op": "deploy",  
  "tick": "Golds",  
  "lim": "1",  
  “reg”：“^[1-9][0-9]*0{8}$”,  
  "des": "The first satoshi of one BTC"  
}  
每个BTC的第一个sat才能mint成功。正则表达式的意思是该sat的序号的末尾是8个0。这意味着，每个token值一个BTC。



玉如意
----
{  
  "p": "ordx",  
  "op": "deploy",  
  "tick": "JadeRuyi",  
  "lim": "9999",  
  “cn”：“99999”,  
  "des": "The coin has n consecutive numbers, which means everything goes well."  
}  
在某个具备99999个连续编号的sat上mint一个玉如意。拥有一个玉如意的人将获得万事如意的祝福。


结论
----
Ordinals协议的应用场景还没有被很好挖掘，我们的想象力还没有被打开，无限的想象空间交给充满奇思妙想的你们。
