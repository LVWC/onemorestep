这里是one more step 的mod说明文档。
## 0、写在前面
    steam库中右键游戏-属性-测试，输入测试密码test123456789解锁测试模式

## 1、所需技能
    您不需要任何编程相关经验
    只需要简单的向Excel表格输入数据即可
    如果你有图片处理经验会使你创造的英雄看起来更协调一些

## 2、所需资源
    一张简单的png图片便可创造一个装备。
    最少一张图便可满足您创造一个英雄的欲望。
    战场人物图片大小最好在100*100像素左右
    人物头像、装备icon大小为64*64
    
## 3、快速开始

    0、所有需要命名的地方，使用英文+数字+下划线方式，不可出现中文。
    1、首先打开游戏目录下resources\app\app\mods 文件夹。
    2、在这里新建一个文件夹，作为你自己的mod物品文件夹(这个文件夹最好以你自己的名字_mod名字,如"name_myMod")
    3、从mod模板（resources\app\app\mods\new文件夹）中复制actor.xlsx到你的新建文件夹。
    4、在新建的文件夹中新建一个res文件夹，作为所有图片，音效等资源的存放目录，内部资源如何整理自己随意    
    5、打开actor.xlsx，里面有三张表格（sheet），分别代表职业、角色、装备，选择任意一个表格，将原有数据删除，仅保留第一行标题。
    6、按照标题描述填写对应的数据，橙色标题为必填项目。



## 4、actorConfig表格字段说明
    id:角色的唯一id，同样的角色，不管多少等级，都是这个id，这个id应该尽量避免与他人重复如:name_myMod_actor_10001;
    name:最好使用英语名称，最好填写，方便非汉语地区的人知道你的角色名。
    name-zh：如果有这个字段，则玩家选择了中文时会使用这个名称。如果你希望使用俄语 则改为name-ru，或者，你可以复制一列数据出来，改成任何你希望的语言
    level：角色等级，如果你的角色有三个等级（星级），这意味着你要写三行数据出来。
    quality：品质
    levelNeed：升星需求，代表几个角色可以升级成一个更高等级的角色。
    occu：职业，你可以自定义职业（查看occuConfig表格字段说明），也可以直接将你的角色纳入官方职业中，目前官方已有职业如下
            official_occu_1001（战士）
            official_occu_1002（牧师）
            official_occu_1003（法师）
            official_occu_1004（追击）
            official_occu_1005（穿刺）
            official_occu_1006（坦克)
            official_occu_1007（野兽)
    atk、def、hp、ap、apDef、avoid:这几项是人物的基础属性
    skills：技能填写规则在大标题7处有统一说明
    skillDescs-zh:自定义的技能描述，用以替换原有文案（可不填）。如有多个技能，中间用“|”分隔，如“攻击附加xxx|血量增加10点” -后面的代表语言 如果你需要英语自定义文案，这里应该增加一列标题“skillDescs-en”
    icon：角色头像的相对路径，如res/actor1/icon.png
    idleAnim：角色站立动画的相对路径，图片应放在同一个子文件夹下，并且命名按照1、2、3进行排序。
                    比如，你在res/actor1/idle/下面有idle1.png,idle2.png,idle3.png三张图片，那么，这里填入res/actor1/idle/idle,3
                    如果你想要调整动画的播放速度，则再加一个字段，否则默认是1
                    最后这个数字越大速度越快，可为浮点数 如，res/actor1/idle/idle,3,1.5
    atkAnim：攻击动画，规则同上
    hurtAnim：受击动画，规则同上
    deathAnim：死亡动画，规则同上，如果没有，放一张空白图也是比较合适的
    atkType：法术攻击方式，1代表走向敌人攻击；2代表子弹攻击，类似游戏中的火球；3代表召唤物攻击，类似美杜莎施放法术召唤的石头。如果这个角色是个物理攻击型的，填1即可
    atkEffect：物理系可不填，规则同人物动画
    audio：攻击时的音效，如res/actor1/attack.mp3 暂时只支持.mp3，没有可不填

## 5、occuConfig表格字段说明
    
    id：职业的唯一id，避免和他人重复，如:name_myMod_occu_1001;
    counts：组成羁绊所需角色个数
    skills：技能填写规则在大标题7处有统一说明
    skillDescs-zh:自定义的技能描述，用以替换原有文案（可不填）。与actor不同的是，这里只有一个字符串，写清楚所有技能描述即可 -后面的代表语言 如果你需要英语自定义文案，这里应该增加一列标题“skillDescs-en”
    name：职业名称
    nameEn：职业英文名称
    itemType：生成敌人规则使用，代表了这个职业会用哪些类别的装备，如有多个，用"|"分隔。
                    如 1|4
                    1：攻击类
                    2：医疗类
                    3：法术类
                    4：防御类


    注意：你必须为每个职业的每个品质至少配置一个英雄出来，否则会找不到高品质英雄导致无法正常生成该职业阵容

## 6、itemsConfig表格字段说明

    id：装备的唯一id，避免和他人重复，如:name_myMod_item_1001;
    name：职业名称
    nameEn：职业英文名称
    skills：技能填写规则在大标题7处有统一说明
    skillDescs-zh:自定义的技能描述，用以替换原有文案（可不填）。如有多个技能，中间用“|”分隔，如“攻击附加xxx|血量增加10点” -后面的代表语言 如果你需要英语自定义文案，这里应该增加一列标题“skillDescs-en”
    icon：物品图片的相对路径，如res/item/icon.png

    以下三项为生成敌人使用，也是必填项目：
    type：生成敌人规则使用，给这个装备指定一个类别。
                    1：攻击类
                    2：医疗类
                    3：法术类
                    4：防御类
    max：代表了敌人最多会携带几件这个装备，比如游戏本体中的刺客面具，这个值为1，因为带多了也没用。

## 7、技能说明
    技能格中可以填写多个技能，用“|”进行分隔。
    如：default,1,0:30001,50|default,1,0:30002,50   代表该角色或装备默认拥有30001及30002两个技能 
    单个技能的规则如下：
        技能由两部分构成：
        1、触发条件
                该部分存在三个字段：条件、值、是否需要怒气显示 （需要用到的资源都可在标题8中找到）
                例如，你现在需要某个技能在受到普通攻击5次之后触发，并且需要显示触发怒气特效：
                写做： underNormalAttackTimes,5,1 
            如果该条件没有数值，则写做1，如：default,1,0 则为默认入场即生效技能，并且不需要触发怒气特效
        2、技能：
            技能由技能id及值构成，现有技能可参照下表。这里先说明如何配置一个技能（需要用到的资源都可在标题8中找到）
        
            最简单的技能：
                21002,50   普通攻击后有{s1}%的概率再次进行一次攻击。      
                20031,1     永远不会受到暴击伤害。  （该技能无数值，则数值填1）
            比较复杂的技能：   60001普通攻击后，有{s1}%的概率给敌人增加一个状态：
            60003,50,buff_1502,3,5
            意味着 有50%的概率立即对敌人造成一个中毒buff，持续3回合，每回合开始失去5%的血量
         
        通过上述的概念，则现在可以明白技能是由两部分组成的，条件和技能以":"隔开，那么一个完整的技能则应该如下：
        default,1:21005,1       默认生效，普通攻击增加一个攻击目标
        everyNormalAttack,1:60003,50,buff_1502,3,5   每普通攻击1次触发一次，有50%的概率立即对敌人造成一个中毒buff，持续3回合，每回合开始失去5%的血量

        一些常用技能举例：
            反击：everyUnderNormalAttack,1:60002,50  每1次受到攻击触发，50%的概率对敌人进行物理攻击。
            反伤：everyUnderNormalAttack,1:60004,50  每1次受到攻击触发，立即对敌人造成伤害量50%的神圣伤害。
            吸血：everyNormalAttack,1:60006,50       每1次物理攻击，立即恢复自身相当于伤害量50%的生命值
            自爆：onDeath,1:60014,50                 死亡时，立即对敌方造成自身最大生命值50%的神圣伤害。
            开矿：perXRoundPre,1:60018,2             每1回合开始时候,立即获得2个金币
        通过条件和技能，可以灵活组合出来各种各样的技能。如果觉得官方文案过于正式，可以通过skillDescs-zh或者其他语言字段自行进行技能说明
        
        组合注意事项：
            技能表格中有需要目标的技能，只可与存在目标的条件形成组合
      
## 8、如何生成到游戏
    当你将Excel文档配置完成之后，进入游戏，点击设置 创意工坊，在出现的界面中输入你的根目录名，点击生成即可。如果发生错误，请按照提示进行修改。
    生成成功后，你的目录下会多出来三个json文件，分别代表职业，角色以及装备的配置
    打开图鉴，查看你创造的物品是否已在图鉴中显示
## 9、如何发布及更新
    当你
    在你的根目录下放入一张图片，命名preview.png，作为其他玩家在创意工坊界面看到的预览图
    新建一个文件 config.json ，复制如下内容
    {
        "name":"mod_test",
        "desc":"mod_desc"
    }
    填入以上字段，分别代表你的mod名称，描述，即可准备上传。
    （如果不想将你的配置暴露，可以将actor.xlsx移出文件夹，这样它就不会参与上传）
    在游戏中创意工坊界面输入你的目录名，点击上传即可。
    （上传时，游戏进程会卡住一段时间，取决于你的网速以及mod包的大小，请耐心等待出现弹框）
    上传成功后config.json中会多出来一个字段published_file_handle，该字段是你的mod的唯一id，请妥善保存，上传时config.json中有这个字段，会认为这是一次mod更新
    如果后期需要换预览图，请自行到steam创意工坊页面进行修改


## 10、现有资源

**触发条件：**

举例 | 效果|目标| 备注
:----------- | :----------- | :-----------
default,1	|	入场生效	|无|	无参数，填1	|
battleWithActor,	|	与{s1}同时上场	|无|	参数为其他角色的id	|
battleWithItem,	|	装备{s1}	|无|	参数为装备的id	|
everyUnderNormalAttack,2	|	每受到2次物理攻击	|最后一次造成伤害的敌方|		|
underNormalAttackTimes,2	|	累计受到2次物理攻击	|最后一次造成伤害的敌方|		|
everyUnderMagicAttack,2	|	每受到2次法术攻击	|	最后一次造成伤害的敌方|	|
underMagicAttackTimes,2	|	累计受到2次法术攻击	|	最后一次造成伤害的敌方|	|
everyUnderAttack,2	|	每受到2次任意攻击	|	最后一次造成伤害的敌方|	|
underAttackTimes,2	|	累计受到2次任意攻击	|	最后一次造成伤害的敌方|	|
perXRoundPre,3	|	每3回合开始时	|	无|	|
perXRoundAfter,3	|	每3回合结束时	|无|		|
roundBegin,3	|	第3回合开始阶段	|	无|	|
roundAfter,3	|	第3回合结束阶段	|	无|	|
lifeBelow,50	|	生命值低于50%时	|	无|	|
avoidTimes,5	|	成功闪避5次后	|	最后一次造成伤害的敌方|	|
everyAvoid,1	|	每成功闪避1次	|	最后一次造成伤害的敌方|	|
everyNormalAttack,2	|	每进行2次物理攻击	|	最后一次造成伤害的敌方|	|
everyMagicAttack,2	|	每进行2次法术攻击	|	最后一次造成伤害的敌方|	|
normalAttackTimes,2	|	2次物理攻击后	|	最后一次造成伤害的敌方|	|
magicAttackTimes,2	|	2次法术攻击后	|	最后一次造成伤害的敌方|	|
everyKillEnemy,2	|	每杀死2个敌人	|	最后一次造成伤害的敌方|	|
killEnemyCount,2	|	杀死2个敌人后	|	最后一次造成伤害的敌方|	|
onDeath,1	|	濒临死亡时	|	最后一次造成伤害的敌方|	|
onFriendDeath,1 |每1个友军濒临死亡时，| 最后一次造成伤害的敌方|
onEveryCure,2	|	每治疗2个单位	|		被治疗目标||
onCureTimes,2	|	累计治疗2个单位	|	被治疗目标|	|

**技能：**
常规技能类：
举例 | 效果 | 需要目标 | 备注
:------------------- | :-------------- | :-------------- | :--------------
10002,2,50,2,40	|	攻击方式变为法术攻击，对2个敌方角色造成法强50%的伤害，并对2个我方角色治疗造成总伤害40%的生命值。	|		|	
10003,3,20	|	攻击方式变为法术攻击，对3个敌方角色进行法术攻击，造成伤害相当于法强的20%。	|		|	
主动类：
举例 | 效果 | 需要目标 | 备注
60001,50,buff_1502,2,5	|	50%的概率立即为自己增加一个状态：中毒：每回合降低最大生命值5%的生命值，持续2回合	|		|	50之后的参数为buff参数，可自行填入任意buff，详情查看buff表
60002,50	|	50%的概率对敌人进行物理攻击。	|	√	|	
60003,50,buff_1502,2,5	|	50%的概率立即为敌人增加一个状态：中毒：每回合降低最大生命值5%的生命值，持续2回合	|	√	|	50之后的参数为buff参数，可自行填入任意buff，详情查看buff表
60004,50	|	立即对敌人造成伤害量50%的神圣伤害。	|	√	|	
60005,50	|	立即恢复周围角色50%的生命值	|		|	
60006,50	|	立即恢复自身相当于伤害量50%的生命值	|		|	
60007,50	|	立即对敌人造成50%最大生命值的神圣伤害	|	√	|	
60008,2,50	|	立即对敌人周围2个单位造成50%伤害量的神圣伤害	|	√	|	
60009,50	|	立即对敌人造成自身攻击力50%的神圣伤害	|	√	|	
60010,50	|	对敌人身后的单位造成伤害量50%的神圣伤害	|	√	|	
60011,50	|	立即对敌人造成自身魔力50%的神圣伤害	|	√	|	
60014,50	|	立即对敌方造成自身最大生命值50%的神圣伤害。	|	√	|	
60015,50	|	失去自身50%的生命值，对敌人造成等量神圣伤害	|	√	|	
60016,50	|	如果敌人生命值低于50%，立即对敌人造成当前剩余生命值的神圣伤害。	|	√	|	
60017,50	|	对敌人的同排角色造成伤害量50%的神圣伤害。	|	√	|	
60018,1	|	立即获得1个金币	|		|	
60019,1	|	立即进行一次额外的物理攻击	|		|	这里指的是一个从索敌开始算起的攻击
60020,2,50	|	立即进行一次额外的法术攻击，对2个敌人造成50%魔力的魔法攻击	|		|	这里指的是一个从索敌开始算起的攻击
60021,1	|	立即清除目标身上的所有负面状态	|	√	|	
60022,1	|	立即清除目标身上的所有正面状态	|	√	|	
被动类：
举例 | 效果 | 需要目标 | 备注
20008,20	|	有50%的概率免疫受到的任何伤害。	|		|	
20011,buff_1501	|	免疫状态:束缚	|		|	20011后面的参数为buff表中的buffId
20021,50  	|	友军死亡时，增加50%的基础攻击力（濒死复活计算一次死亡）。	|		|	
20030,1	|	永远不会受到反伤和反击。	|		|	无参数技能填1，以下不再特殊说明
20031,1	|	永远不会受到暴击伤害。	|		|	
20034,1	|	受到伤害时，由所有在场同职业角色按比例承担此伤害。	|		|	
21005,2	|	普通攻击额外增加2个目标。	|		|	
21010,1	|	普通攻击造成暴击伤害后必定给敌人增加一个束缚状态	|		|	
21014,1	|	进行穿刺攻击时，可同时对敌人身后两格造成伤害。	|		|	
21015,1	|	普通攻击时优先选择生命值最低的敌方单位作为目标。	|		|	
21018,1	|	普通攻击无视敌方护甲。	|		|	
21021,1	|	普通攻击随机选择对方一个敌人进行攻击。	|		|	
21022,1	|	普通攻击时与一个敌人进行决斗，双方只能依次进行普通攻击，直至一方战死为止。决斗不会影响到第三者(穿刺、溅射等无效)。	|		|	
21026,50	|	普通攻击时，攻击力等于自身攻击力加已损失血量的50%	|		|	
22001,3	|	治疗技能额外作用3个目标。	|		|	
22002,20	|	使用治疗技能时，治疗效果增强20%。	|		|	
22004,1	|	使用治疗技能时，可复活场上已死亡单位。	|		|	
22006,20	|	治疗效果20%概率增加一倍。	|		|	
22008,50	|	使用治疗技能时，治疗效果降低50%。	|		|	
22009,1	|	治疗技能作用目标减少1个。	|		|	
23001,2	|	法术攻击额外增加2个目标。	|		|	
23002,1	|	法术攻击目标变为全体。	|		|	
23003,50	|	法术攻击有50%的概率造成法术暴击，造成2倍伤害。	|		|	
23004,50	|	法术伤害效果增强50%。	|		|	
23005,50	|	法术攻击有50%的概率再次进行一次攻击。	|		|	
23008,1	|	法术攻击目标减少1个。	|		|	
23012,1	|	法术攻击目标数固定为1	|		|	
属性类
举例 | 效果 | 需要目标 | 备注
30001,100	|	增加自身攻击力100点。	|		|	
30002,100	|	增加自身魔力100点。	|		|	
30003,500	|	增加自身最大生命值500点。	|		|	
30004,3	|	增加自身护甲3点。	|		|	
30005,3	|	增加自身魔抗3点。	|		|	
30006,50	|	增加自身暴击率50%。	|		|	
30007,50	|	增加自身暴击伤害50%。	|		|	
30008,50	|	增加自身闪避50%。	|		|	
30009,500	|	增加自身当前生命值500	|		|	
30010,50	|	增加自身最大生命值50%的当前生命值	|		|	
30011,50	|	增加自身攻击力50%。	|		|	
30012,50	|	增加自身魔力50%。	|		|	
30013,50	|	增加自身最大生命值50%。	|		|	
30014,50	|	增加自身基础生命值50%的攻击力。	|		|	
30015,1	|	职业技能等级加1。	|		|	
30016,50	|	增加自身我方场上职业个数乘以50%的攻击力。	|		|	
31001,20	|	减少自身攻击力20点。	|		|	
31002,20	|	减少自身魔力20点。	|		|	
31003,20	|	减少自身最大生命值20点。	|		|	
31004,20	|	减少自身护甲20点。	|		|	
31005,20	|	减少自身魔抗20点。	|		|	
31006,50	|	减少自身暴击率50%。	|		|	
31007,50	|	减少自身暴击伤害50%。	|		|	
31008,50	|	减少自身闪避50%。	|		|	
31009,20	|	减少自身当前生命值20	|		|	
31010,50	|	减少自身最大生命值50%的当前生命值	|		|	
31011,50	|	减少自身攻击力50%。	|		|	
31012,50	|	减少自身魔力50%。	|		|	
31013,50	|	减少自身最大生命值50%。	|		|	
32001,20	|	增加敌人攻击力20点。	|	√	|	
32002,20	|	增加敌人魔力20点。	|	√	|	
32003,20	|	增加敌人最大生命值20点。	|	√	|	
32004,5	|	增加敌人护甲5点。	|	√	|	
32005,5	|	增加敌人魔抗5点。	|	√	|	
32006,50	|	增加敌人暴击率50%。	|	√	|	
32007,50	|	增加敌人暴击伤害50%。	|	√	|	
32008,50	|	增加敌人闪避50%。	|	√	|	
32009,500	|	增加敌人当前生命值500	|	√	|	
32010,50	|	增加敌人最大生命值50%的当前生命值	|	√	|	
32011,50	|	增加敌人攻击力50%。	|	√	|	
32012,50	|	增加敌人魔力50%。	|	√	|	
32013,50	|	增加敌人最大生命值50%。	|	√	|	
32014,50	|	增加敌人基础生命值50%的攻击力。	|	√	|	
33001,100	|	减少敌人攻击力100点。	|	√	|	
33002,100	|	减少敌人魔力100点。	|	√	|	
33003,500	|	减少敌人最大生命值500点。	|	√	|	
33004,5	|	减少敌人护甲5点。	|	√	|	
33005,5	|	减少敌人魔抗5点。	|	√	|	
33006,50	|	减少敌人暴击率50%。	|	√	|	
33007,50	|	减少敌人暴击伤害50%。	|	√	|	
33008,50	|	减少敌人闪避50%。	|	√	|	
33009,500	|	减少敌人当前生命值500	|	√	|	
33010,50	|	减少敌人最大生命值50%的当前生命值	|	√	|	
33011,50	|	减少敌人攻击力50%。	|	√	|	
33012,50	|	减少敌人魔力50%。	|	√	|	
33013,50	|	减少敌人最大生命值50%。	|	√	|	
40001,20	|	增加己方所有同职业角色攻击力20点。	|		|	
40002,20	|	增加己方所有同职业角色魔力20点。	|		|	
40003,20	|	增加己方所有同职业角色最大生命值20点。	|		|	
40004,5	|	增加己方所有同职业角色护甲5点。	|		|	
40005,5	|	增加己方所有同职业角色魔抗5点。	|		|	
40006,50	|	增加己方所有同职业角色暴击率50%。	|		|	
40007,50	|	增加己方所有同职业角色暴击伤害50%。	|		|	
40008,50	|	增加己方所有同职业角色闪避50%。	|		|	
40009,500	|	增加己方所有同职业角色当前生命值500	|		|	
40010,50	|	增加己方所有同职业角色最大生命值50%的当前生命值	|		|	
40011,50	|	增加己方所有同职业角色攻击力50%。	|		|	
40012,50	|	增加己方所有同职业角色魔力50%。	|		|	
40013,50	|	增加己方所有同职业角色最大生命值50%。	|		|	
40014,50	|	增加己方所有同职业角色基础生命值50%的攻击力。	|		|	
41001,20	|	减少己方所有同职业角色攻击力20点。	|		|	
41002,20	|	减少己方所有同职业角色魔力20点。	|		|	
41003,20	|	减少己方所有同职业角色最大生命值20点。	|		|	
41004,5	|	减少己方所有同职业角色护甲5点。	|		|	
41005,5	|	减少己方所有同职业角色魔抗5点。	|		|	
41006,50	|	减少己方所有同职业角色暴击率50%。	|		|	
41007,50	|	减少己方所有同职业角色暴击伤害50%。	|		|	
41008,50	|	减少己方所有同职业角色闪避50%。	|		|	
41009,500	|	减少己方所有同职业角色当前生命值500	|		|	
41010,50	|	减少己方所有同职业角色最大生命值50%的当前生命值	|		|	
41011,50	|	减少己方所有同职业角色攻击力50%。	|		|	
41012,50	|	减少己方所有同职业角色魔力50%。	|		|	
41013,50	|	减少己方所有同职业角色最大生命值50%。	|		|	
44001,20	|	增加己方所有角色攻击力20点。	|		|	
44002,20	|	增加己方所有角色魔力20点。	|		|	
44003,20	|	增加己方所有角色最大生命值20点。	|		|	
44004,20	|	增加己方所有角色护甲20点。	|		|	
44005,20	|	增加己方所有角色魔抗20点。	|		|	
44006,50	|	增加己方所有角色暴击率50%。	|		|	
44007,50	|	增加己方所有角色暴击伤害50%。	|		|	
44008,50	|	增加己方所有角色闪避50%。	|		|	
44009,500	|	增加己方所有角色当前生命值500	|		|	
44010,50	|	增加己方所有角色最大生命值50%的当前生命值	|		|	
44011,50	|	增加己方所有角色攻击力50%。	|		|	
44012,50	|	增加己方所有角色魔力50%。	|		|	
44013,50	|	增加己方所有角色最大生命值50%。	|		|	
44014,50	|	增加己方所有角色基础生命值50%的攻击力。	|		|	
45001,20	|	减少己方所有角色攻击力20点。	|		|	
45002,20	|	减少己方所有角色魔力20点。	|		|	
45003,20	|	减少己方所有角色最大生命值20点。	|		|	
45004,20	|	减少己方所有角色护甲20点。	|		|	
45005,20	|	减少己方所有角色魔抗20点。	|		|	
45006,50	|	减少己方所有角色暴击率50%。	|		|	
45007,50	|	减少己方所有角色暴击伤害50%。	|		|	
45008,50	|	减少己方所有角色闪避50%。	|		|	
45009,500	|	减少己方所有角色当前生命值500	|		|	
45010,50	|	减少己方所有角色最大生命值50%的当前生命值	|		|	
45011,50	|	减少己方所有角色攻击力50%。	|		|	
45012,50	|	减少己方所有角色魔力50%。	|		|	
45013,50	|	减少己方所有角色最大生命值50%。	|		|	
46001,20	|	增加敌方所有角色攻击力20点。	|		|	
46002,20	|	增加敌方所有角色魔力20点。	|		|	
46003,500	|	增加敌方所有角色最大生命值500点。	|		|	
46004,5	|	增加敌方所有角色护甲5点。	|		|	
46005,5	|	增加敌方所有角色魔抗5点。	|		|	
46006,50	|	增加敌方所有角色暴击率50%。	|		|	
46007,50	|	增加敌方所有角色暴击伤害50%。	|		|	
46008,50	|	增加敌方所有角色闪避50%。	|		|	
46009,500	|	增加敌方所有角色当前生命值500	|		|	
46010,50	|	增加敌方所有角色最大生命值50%的当前生命值	|		|	
46011,50	|	增加敌方所有角色攻击力50%。	|		|	
46012,50	|	增加敌方所有角色魔力50%。	|		|	
46013,50	|	增加敌方所有角色最大生命值50%。	|		|	
46014,50	|	增加敌方所有角色基础生命值50%的攻击力。	|		|	
47001,20	|	减少敌方所有角色攻击力20点。	|		|	
47002,20	|	减少敌方所有角色魔力20点。	|		|	
47003,20	|	减少敌方所有角色最大生命值20点。	|		|	
47004,20	|	减少敌方所有角色护甲20点。	|		|	
47005,20	|	减少敌方所有角色魔抗20点。	|		|	
47006,50	|	减少敌方所有角色暴击率50%。	|		|	
47007,50	|	减少敌方所有角色暴击伤害50%。	|		|	
47008,50	|	减少敌方所有角色闪避50%。	|		|	
47009,500	|	减少敌方所有角色当前生命值500	|		|	
47010,50	|	减少敌方所有角色最大生命值50%的当前生命值	|		|	
47011,50	|	减少敌方所有角色攻击力50%。	|		|	
47012,50	|	减少敌方所有角色魔力50%。	|		|	
47013,50	|	减少敌方所有角色最大生命值50%。	|		|	


**buff**

举例 | 效果 | 备注
:----------- | :----------- | :-----------
buff_1001,10,3	|	再生：每回合开始时恢复10%的生命值,持续3回合	|		|
buff_1002,10,3	|	鼓舞：物理伤害结果提升10%，持续3回合	|		|
buff_1003,10,3	|	鼓舞：物理伤害结果提升10点，持续3回合	|		|
buff_1004,10,3	|	法力增强：魔法伤害结果提升10%，持续3回合	|		|
buff_1005,10,3	|	法力增强：魔法伤害结果提升10点，持续3回合	|		|
buff_1501,3	|	束缚：无法主动行动，持续3回合	|		|
buff_1502,10,3	|	中毒：每回合降低最大生命值10%的生命值，持续3回合	|		|
buff_1503,10,3	|	易伤：受到的物理伤害加深10%，持续3回合	|		|
buff_1504,10,3	|	虚弱：物理伤害结果降低10%，持续3回合	|		|
buff_1505,10,3	|	虚弱：物理伤害结果降低10点，持续3回合	|		|
buff_1506,3	|	嘲讽：所有敌方单位会优先攻击此目标，持续3回合	|		|
buff_1507,10,3	|	法力空虚：魔法伤害结果降低10%，持续3回合	|		|
buff_1508,10,3	|	法力空虚：魔法伤害结果降低10点，持续3回合	|		|
buff_1509,10,3	|	爆破：buff持续回合结束后对敌方造成10%最大血量的伤害，持续3回合	|		|
buff_1510,10,3	|	爆破：buff持续回合结束后对敌方造成10%点伤害，持续3回合	|		|
buff_1511,10,3	|	法术易伤：受到的魔法伤害加深10%，持续3回合	|		|
