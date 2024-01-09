用例
====


我们用下面的几个例子，庆祝协议的发布，并且对先行者致敬。
注意所有通过我们网站进行的交易操作，都会收取一点点的手续费（2000sats或者交易费用的1%），作为支持协议开发和运营的费用。  


东方之珠
----
{   
  "p": "ordx",  
  "op": "deploy",  
  "tick": "Pearl",  
  "block": "827200-828200",  
  "lim": "10000",  
  "des": "The Oriental Pearl."    
}   
我们计划在2024年1月15日正式发布协议，并且部署第一个Token：Pearl。  
大概在2024年1月25日前后开启自由mint，持续到1月31日左右结束（由区块高度827200-828200决定有效的mint时间）。  
这是ordx协议的第一个token，也是一个meme币，仅供试验，没有价值，不要FOMO。  



如果你的BTC很多，可以尝试下是不是可以从BTC中找出闪亮的宝石，只需要输入你的钱包地址，就可以看到结果。或者你认为哪些类型的sat更有价值，可以为这些sat部署特别的Token。 


矿工的翡翠
----
{  
  "p": "ordx",  
  "op": "deploy",  
  "tick": "Jade",  
  "lim": "1",  
  "rar": "uncommon",  
  "des": "Miner's Jade."  
}  
每个区块的第一个sat才能mint成功，预计每个token值1-10个BTC。


Domo的红宝石
----
{  
  "p": "ordx",  
  "op": "deploy",  
  "tick": "Ruby",  
  "lim": "1",  
  "rar": "rare",  
  "des": "Domo's Ruby."  
}  
只有rare属性的sat才能mint成红宝石，最多只有3437个红宝石。目前只有不到400个，预计每个值100BTC。


Casey的蓝宝石
----
{   
  "p": "ordx",  
  "op": "deploy",  
  "tick": "Sapphire",  
  "lim": "1",  
  "rar": "epic",  
  "des": "Casey's Sapphire."  
}  
只有epic属性的sat才能mint成蓝宝石，最多只有32个蓝宝石。目前只有3个，预计每个值10000BTC。


数字黄金
----
{  
  "p": "ordx",  
  "op": "deploy",  
  "tick": "Gold",  
  "lim": "1",  
  “reg”：“^[1-9][0-9]*0{8}$”,  
  "des": "The first satoshi of one BTC"  
}  
每个BTC的第一个sat才能mint成功。正则表达式的意思是该sat的序号的末尾是8个0。这意味着，每个token值一个BTC。


结论
----
Ordinals协议的应用场景还没有被很好挖掘，我们的想象力还没有被打开，无限的想象空间交给充满奇思妙想的你们。
