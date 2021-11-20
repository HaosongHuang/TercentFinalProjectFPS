# TercentFinalProjectFPS
此库包含腾讯2021客户端公开课02班选做大作业，亦用于完成每周作业。

姓名：黄号淞

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
