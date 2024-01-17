协议比较
=====


| - | OrdX | BRC-20 | Atomicals |
| :--: | :----: | :----: | :----: | 
| 价值主张 | 数字珍宝 | - | 数字对象 |
| 资产类型 | FT | FT | NFT+FT | 
| 铸造方法 | 基于ord的信封，使用deploy和mint | 基于ord的信封，使用deploy、mint、tranfer | 使用"atom"进行承诺&揭露的信封 | 
| 索引 | 依赖ordx索引器跟踪序数系统和ticker | 依赖brc-20索引器 | 依赖electrumx索引器跟踪序数和编号系统 | 
| 验证 | 通过索引服务ordx验证，可以客户端验证 | 通过索引服务brc-20验证，无法客户端验证 | 通过索引服务electrumx验证，理论上可以客户端验证 |
|地址格式| P2TR | P2TR | P2TR | 
| 原子swap | PBST | PBST | PBST | 
| 转移 | 直接转移 | 先铭刻，再转移 | 直接转移 | 
| 基本单位 | 一sat一token，跟sat绑定，使用ordinals协议对sat编码 | 跟地址绑定，无限可分 | 一sat一token，但是跟sat不绑定，不需要对sat编码 | 
| 销毁可能性 | sat不可销毁，token也就无法销毁，即使使用不支持ordinals协议的钱包也不会导致token销毁，最多被转移 | 不可销毁 | 使用错误的钱包或者错误的使用方式容易导致token被销毁 | 
