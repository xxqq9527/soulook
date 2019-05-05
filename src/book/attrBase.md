属性系统(基本)

---

```
黄金/木头/经验率
    影响资源获取率

生命
    单位的最大生命值
    修改范围 -999999999 到 999999999
    最小值 1

魔法
    单位的最大魔法值
    修改范围 -999999999 到 999999999
    最小值 1

生命恢复/魔法恢复
    每秒对生命/魔法恢复的量

生命源/魔法源
    储存自身恢复生命/魔法的量
    初始500点，每升1级增加10点

移动力
    [范围] 0～?取决于地图的平衡常数设置(hjass设为522)，当camera采用zoomin模式时，最大移动力增加2倍
    每秒移动最大距离
    *数值无上限，但地图移动上限为522或1044（camera = zoomin）
    *假设移动力为2000，则实际移动仍为522，而其他由移动力影响的技能属性将以2000点计算

护甲
    修改范围 -999999～999999
    依照公式将抵消/增加受到的伤害比例
    假设当前护甲为 x ：
    正护甲抵伤公式：x/(x+200)
    负护甲增伤公式如下 ：
    大于-100：2-(0.99)^abs(x)-0
    大于-200：3-(0.99)^abs(x)-100
    大于-300：4-(0.99)^abs(x)-200
    ...
    遇到无视护甲的伤害时，正护甲将会失效，如果此时护甲为负，依然会承受更大的伤害
    当受到物理伤害混合了其他伤害的情况时，以单位的攻击力占比计算，如物理攻击力100，魔法50，则护甲只有66.66%的效果(负护甲无影响)

魔抗
    魔法伤害的抵抗因数
    如果魔抗小于0%，则额外承受同比例伤害,如-25%，则承受125%伤害
    如果魔抗为100%，则完全不受魔法伤害
    如果魔抗大于100%，则额外抵抗部分会反射反而伤害给予施法者
    遇到无视魔抗的伤害时，正魔抗将会失效，如果此时魔抗为负，依然会承受更大的伤害
    当受到魔法伤害混合了其他伤害的情况时，以单位的攻击力占比计算，如物理攻击力100，魔法50，则魔抗只有33.33%的效果(负魔抗无影响)

韧性
    韧性可以直接抵消伤害，包括真实伤害!
    最大只能抵消90%的伤害，无论韧性达到多大
    * 韧性最低为0

回避
    当英雄受到的是“攻击”造成的伤害时会有一定几率闪避抵抗，并且使攻击特效失效
    闪避效果只有当英雄回避属性大于0%时才会开始生效
    回避可以无限堆，达到100%时一般情况下回避所有伤害
    回避率=(回避-命中)（%）
    * 如果该次伤害大于等于目标最大生命的25%，回避失效
    * 如果该次伤害为暴击（物理/魔法）回避效果减少10%
    * 如果该次伤害拥有真实伤害效果，回避效果减少20%
    * 如果该次伤害拥有绝对伤害效果，回避效果减少50%
    * 如果该次伤害为无视回避，则回避失效

命中
    命中直接抵消回避生效的效果值
    回避率=(回避-命中)（%）

硬直
    每个单位默认的硬直为生命值的1/3，英雄附加三围的影响
    硬直扣减量与受到伤害相关
    受到快速多段伤害或高伤害时，将很容易被击破而僵直
    硬直被破坏时会僵直5秒,并重置硬直条，期间受到伤害可能会再次僵直
    硬直的僵直5秒的体现是攻击速度和移动速度被极大地减少
    硬直未被击破时每隔5秒恢复100点
    * 不造成伤害时，不减少硬直
    * 硬直条最低为100

硬直抵抗
    硬直抵抗按百分比减少硬直的减速效果
    硬直抵抗的效果最高只能减少90%
    
白字力量
    影响（物理攻击力、魔法攻击力、生命、韧性、物理暴击、硬直、眩晕抵抗）
    -> 每1点 +0.2物理攻击力
    -> 每1点 +0.2魔法攻击力
    -> 每1点 +5生命
    -> 每1点 +0.2韧性
    -> 每1点 +5物理暴击
    -> 每1点 +2硬直
    -> 每1点 +0.03%眩晕抵抗
    
白字敏捷
    影响（物理攻击力、攻击速度、物理暴击、回避）
    -> 每1点 +0.6物理攻击力
    -> 每1点 +0.05%攻击速度
    -> 每1点 +3物理暴击
    -> 每1点 +0.02%回避

白字智力
    影响（魔法攻击力、魔法、魔法恢复、魔法暴击、技能吸血）
    -> 每1点 +0.6魔法攻击力
    -> 每1点 +5魔法
    -> 每1点 +0.2魔法恢复
    -> 每1点 +10魔法暴击
    -> 每1点 +0.02%技能吸血
    
绿字力量
    影响（物理攻击力、魔法攻击力、生命、韧性、物理暴击、硬直、眩晕抵抗、回避、魔法暴击）
    -> 每1点 +0.1物理攻击力
    -> 每1点 +0.1魔法攻击力
    -> 每1点 +3生命
    -> 每1点 +0.1韧性
    -> 每1点 +3物理暴击
    -> 每1点 +1硬直
    -> 每1点 +0.01%眩晕抵抗
    -> 每1点 -2回避
    -> 每1点 -3魔法暴击
    
绿字敏捷
    影响（物理攻击力、攻击速度、物理暴击、回避、硬直、魔法暴击）
    -> 每1点 +0.3物理攻击力
    -> 每1点 +0.04%攻击速度
    -> 每1点 +1物理暴击
    -> 每1点 +0.01%回避
    -> 每1点 -2硬直
    -> 每1点 -1魔法暴击
    
绿字智力
    影响（魔法攻击力、魔法、魔法恢复、魔法暴击、技能吸血）
    -> 每1点 +0.3魔法攻击力
    -> 每1点 +3魔法
    -> 每1点 +0.1魔法恢复
    -> 每1点 +8魔法暴击
    -> 每1点 +0.01%技能吸血
    
攻击
    在v-hjass下所有单位造成的伤害都视为攻击attack（包括触发技能）
    只有调用v-hjass自定义技能，才被视为真技能skill
    单位进行攻击的能力，一般分为近战或者远程
    每个单位的攻击力由物理攻击力+魔法攻击力组成
    物理攻击力会触发物理暴击
    魔法攻击力会触发魔法暴击
    由于攻击的伤害都是混合型伤害（物理+魔法），所以暴击计算会受到削减
    
攻击波动（附加于攻击之上）
    普通攻击造成伤害时的浮动范围
    攻击波动与生俱来，不随任何影响而变动
    
物理攻击力(白字攻击)
    物理性质的攻击力
    修改范围 -999999999～999999999
    
魔法攻击力(绿字攻击)
    魔法性质的攻击力
    修改范围 -999999999～999999999
    
攻击速度
    攻击一次的间隔
    假设当前攻速增益为 x% ：
    攻击间隔公式：(基本间隔*100) / (100+x) [单位：击/秒]
    修改范围 -80～9999
    
物理暴击
    物理暴击生效必须大于0，并且只对物理伤害生效
    物理暴击几率=数值/300（%）
    物理暴击伤害率=数值x0.05（%）
    物理魔法混合时，以单位的攻击力占比影响暴击，如物理攻击力100，魔法50，则物理暴击只有66.66%的效果
    
魔法暴击
    魔法暴击生效必须大于0，并且只对魔法伤害生效
    魔法暴击几率=数值/200（%）
    魔法暴击伤害率=数值x0.03（%）
    物理魔法混合时，以单位的攻击力占比影响暴击，如物理攻击力100，魔法50，则魔法暴击只有33.33%的效果
    
致命抵抗
    致命抵抗直接抵消物理/魔法暴击生效的效果值
    物理暴击几率=(数值-致命抵抗)/300（%）
    物理暴击伤害率=(数值-致命抵抗)x0.04（%）
    魔法暴击几率=(数值-致命抵抗)/200（%）
    魔法暴击伤害率=(数值-致命抵抗)x0.02（%）
    当致命抵抗大于暴击值时，暴击会完全失效
    
分裂
    分裂只对[攻击方式]造成的伤害生效
    分裂伤害是[特别方式]的无视护甲物理伤害,范围根据属性而变
    以最终造成伤害来计算分裂百分比，可超100%
    * 第一目标不会受到分裂的伤害
    
吸血
    [攻击方式]伤害时触发吸血
    以实际伤害及吸血百分比为计算
    
技能吸血
    [技能方式]造成伤害时(无论伤害是物理魔法真实还是混合等)触发技能吸血
    以实际伤害及吸血百分比为计算
    
眩晕抵抗
    眩晕抵抗同时减少受到眩晕的几率及眩晕时间
    眩晕几率=原眩晕几率%-眩晕抵抗（%）,最小0%即无效
    眩晕时间=原眩晕时间*(100%-眩晕抵抗%)（s）,最小0秒即无效
    
伤害增幅
    增幅属性可以提高所有的伤害（包括真实伤害）
    如增幅100%，则攻击、物品、技能等所有伤害都会提高100%
    伤害增幅在暴击分裂等之前
    
伤害反射
    可反射受到的一切伤害
    默认最低为0%（无反射）最高无限定
    *以最终伤害值计算反射，反射的伤害不会再次成为反射源
    
救助力
    拯救同伴力
    一般只有这个数值能对死亡墓碑生效
    
负重
    负重决定你身上能够佩戴多少物品装备
    英雄初始有10kg容积，每提升1级增加0.25kg
    
治疗
    治疗作用效果一共有 2 种
    第1种为增强主动治疗技能的输出，恢复生命
    第2种为当受到伤害时，可以进行被动恢复的治疗
    默认最低为0%（无治疗）最高无限定
    * 以最终伤害值计算治疗比率，治疗不能使当前生命大于最大生命值
    
运气
    运气在造成伤害时可以触发一些神奇的效果
    如技能刷新、攻击翻倍、攻速翻倍等，一切看天意
    以百分比为计算，最小0%，最大100%
    
无敌
    绝大多数情况下都不会受到攻击和技能伤害
    无敌依然可以受到普通攻击，但不会造成伤害
    * 虽说是无敌的存在，但存在极少数技能甚至可以无视无敌！

```


