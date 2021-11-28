# TercentFinalProjectFPS
此库包含腾讯2021客户端公开课02班选做大作业，亦用于完成每周作业。

姓名：黄号淞

-------------------------------------------------------------------------------------------
光子大作业

实现内容
- （完成要求）游戏开启后的UI
- （完成进阶选项）创建局域网房间，成功设置玩家姓名，局域网内创建和加入session。拥有设置房间名和玩家上限的UI但是没有实际使用。加入房间时可以看到局域网内的房间列表，并可以加入房间。如果有多个房间也能显示，演示视频里没有包括。未能按要求创建房间密码
- （要求但缺失）开始游戏后没有增加loading图并隐藏对局。直接十秒后刷怪，没有显示倒计时。固定10s刷5只怪，没有按要求在怪物被杀光后额外刷新。
-  （替换）没有用怪物波次来决定游戏结束，而是以总时长倒计时，更贴近于生存。例如18波则是180秒，最后怪没有清光也会胜利。
-  （完成基本要求）当守护NPC被杀或所有玩家死亡到达5次时游戏结束，弹出记分板并可以退出游戏。
-  （完成基本要求）记分板显示了所有玩家的姓名，击杀数，死亡数
-  （完成基本要求）主角可以空手，可以近战攻击，可以捡起地上的榴弹枪并射击。主角被击杀后可以播放死亡动画（布娃娃系统），三秒后复活，所有人死5次游戏失败。
-  （完成部分基本要求）主角属性面板包括击杀，死亡和血量，没有显示武器和所携带的Buff
-  （未完成要求）没有Buff系统
-  （完成部分要求）枪械仅有榴弹枪，主要原因是最初没有设计武器系统，包含的东西太多了，时间不足以重构，单纯的替换mesh感觉意义不大。
-  （完成要求）榴弹炮产生范围伤害，在击中敌人 或 碰撞一次且速度足够低时爆炸。
-  （完成部分要求）AI追逐并攻击视野内第一个看到的人（而不是要求的守护NPC），仇恨在追逐对象死亡前不会丢失，若没有发现敌人则在一定半径内巡逻。追逐时与对象距离足够近则会进行近战攻击，有时会出现原地攻击不移动的bug。
-  （完成要求）小怪被击杀时按照概率0.3掉落枪械.
-  （额外完成）基本正确的网络同步
-  (额外已知问题)枪械碰撞时会自己消失，记分板退出按钮有点卡可能需要反复点击试错，退出时是强行切换地图而不是退出局域网session。

Mac包和演示视频：https://share.weiyun.com/IdFwu3wC

------------------------------------------------------------------------------------
UMG作业要求：添加角色的个人信息，基础操作按钮，记分显示。选做增加得分排行榜。

UMG作业完成情况：显示角色的姓名（目前无法编辑，为机器名）。因Mac端没有增加操作按钮，仅设置了一个开火按钮和一个没用的装弹按钮来体现我已掌握制作操作按钮需要的技巧。成功显示玩家目前获得的分数。

Mac包与演示视频：https://share.weiyun.com/jSrtrCRE

-------------------------------------------------------------------------------------------
骨骼动画作业要求： 移动功能，俯仰表现，攻击开火表现，动作表现（近战或者扔手雷）,选做Alt自由视角
完成情况：完成基本要求。移动功能来自初学者包自带，俯仰表现与要求一致，攻击时会发射一个球，动作表现为很丑的丢手雷。额外尝试了不持枪Idle和持刀但动画表现不佳就删了。步枪接近对齐但是左手接不上需要微调。枪为了除去bug去除了物理碰撞，因此存在穿模问题。
额外完成：增加了一个下蹲动作，有时间可能会增加趴下的动作。

Mac包和演示视频：https://share.weiyun.com/3RLj7jxH 因为做的比较晚没时间打包，我只录制了虚幻引擎内的演示

-------------------------------------------------------------------------------------------
物理作业要求：捡枪，不同地区的不同脚步声与脚印，抛体枪械/抛体物理/速度衰减爆炸
完成情况：完成基本要求。
- 捡枪暂时为在空中悬浮的枪支，通过触碰捡起，暂时不支持F键交互捡起。
- 构建了四个地区，地板颜色不同，走上去会有不同的脚印和声音。脚印用的未优化的图片，所以本该是透明的边框实际上会显示白色，没有区分左右脚，没有按照人物行走的方向调整脚印贴图的方向。
  声音是按照脚步声的方法实施，即每走一步播放一次音频。因为默认包里只有一些很长的声音，所以可能走起路来有叠加的问题，到7-8秒后声音才会消失，但功能总体上是正确的，只需要更换声音。
- 抛体枪械为榴弹枪，发射一个Projectile motion为基础的球体，并没有使用纯粹的物体模拟。碰撞反弹时会检测physical material并根据不同材质修改自己的速度，为了演示暂时设置的0/1/10/50倍，效果显著。
  在第一次命中后会触发ready to blow事件（更改子弹的变量），使得子弹在每个tick后检测速度是否低于一定值，如果低于则直接爆炸。如果直接命中靶子（敌人角色的替代品）也会爆炸。
  
演示视频： https://share.weiyun.com/Mgyerjvz， 做得晚没有打包，录制的虚幻引擎内的演示

-------------------------------------------------------------------------------------------
网络同步作业要求：多人联机，网络同步， 死亡表现， 重生， 限时游戏， 记分板
完成情况： 完成基本要求
- 进入游戏时主机开创房间，其他玩家连入房间。仅能在局域网联机。有开房间和加入房间功能，暂时没哟等待房间。
- 普通的动画表现和射击表现完成了同步，较难的地方有动画同步，需要用replicated variable来控制。
- 死亡表现（布娃娃）与3秒重生
- 2分钟限时游戏
- 游戏结束时固定记分板并可以点击返回大厅
- 按Tab获取积分版
- 爆炸物范围击伤

现有严重BUG：
- 记分板名字记录不正确，怀疑game state里面有错误修改
- 结束返回时因为时间不足，没有按照正确方式实现退出session

演示视频： https://share.weiyun.com/zPd6F0LE ，做得晚没有打包，录制的虚幻引擎内演示。周天上课的时候估计可以加入打包内容


