

##### 以下崩溃于网上收集，非完全原创：

---

```
死循环逻辑，如：
    1.任意单位进入区域1 立即移动触发单位到区域2
      任意单位进入区域2 立即移动触发单位到区域1 
    2.任意单位造成伤害，命令其对受伤害者造成伤害
    3.任意单位发布无目标指令,命令触发单位无目标-停止

负数水元素

死亡单位设置光环等级

范围9999999的地狱火

过多的elseif

连接字符串以每次大于3个字符的速度次数过多

Filter和Condition的参数用null 而不是直接用null代替boolexpr

LightningEx的z过高或者移动了null

给单位添加多个等级上限很高的技能

普通单位添加工程升级

蝗虫群的蝗虫位置移动速度为 0

新建或者移动单位坐标出完整地图区域

设置等价物循环

普通单位英雄物品栏吃书

图标的坐标出界例如 (-1,-1) 或者 (5,4) //注意 0,-11是允许的，可以用来隐藏图标

超过一个单位放 普通单位－英雄 或者 英雄－普通单位 英雄－英雄的变身

模型问题

用优化器slk错误的优化

物品的描述中出现"<"

地图初始化时按种族在玩家开始点为玩家创建单位,需要延时创建

无攻击单位释放攻击地面

多人游戏下，在上一局游戏中对玩家执行过"胜利"或"失败"动作，
在下一局，此玩家创建单位后对玩家使用SelectUnitForPlayerSingle函数（玩家选中某单位动作）
此崩溃几率出现，人数越多几率越高

当单位在攻击可破坏物（例如场景里的石头和树这类）瞬间删除可破坏物,会立刻崩溃
```


