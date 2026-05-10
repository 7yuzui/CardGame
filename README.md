# CardGame

# 🎮 Examination - Roguelike 卡牌战斗游戏

<p align="center">
  <strong>一款受《杀戮尖塔》(Slay the Spire) 启发的 Unity Roguelike 卡牌战斗游戏</strong>
</p>

---

## 📖 目录

- [🎯 项目简介](#-项目简介)
- [✨ 核心特性](#-核心特性)
- [🛠️ 技术栈](#-技术栈)
- [📁 项目结构](#-项目结构)
- [🎮 游戏系统](#-游戏系统)
  - [卡牌系统](#卡牌系统)
  - [战斗系统](#战斗系统)
  - [地图探索系统](#地图探索系统)
  - [角色与敌人系统](#角色与敌人系统)
  - [遗物（Perk）系统](#遗物perk系统)
  - [商店与经济系统](#商店与经济系统)
  - [账户与存档系统](#账户与存档系统)
- [🎯 游戏流程](#-游戏流程)
- [🗺️ 房间类型](#️-房间类型)
- [🃏 卡牌列表](#-卡牌列表)
- [👾 敌人列表](#-敌人列表)
- [💾 数据持久化](#-数据持久化)
- [🚀 快速开始](#-快速开始)
- [🔧 开发环境配置](#-开发环境配置)
- [📊 系统架构图](#-系统架构图)
- [🎨 UI/UX 设计](#-uiux-设计)
- [🔮 未来计划](#-未来计划)
- [🤝 贡献指南](#-贡献指南)
- [📄 许可证](#-许可证)

---

## 🎯 项目简介

**Examination** 是一款使用 **Unity 6** 引擎开发的 Roguelike 卡牌战斗游戏。玩家将扮演一位英雄，在程序化生成的地图中展开冒险，通过收集卡牌、获取遗物、击败敌人，最终挑战强大的 Boss。

游戏融合了策略卡牌构建（Deck-building）和 Roguelike 随机元素，每次游玩都是独特的体验。玩家需要在战斗中合理运用手牌，管理法力值，并在地图节点间做出关键决策。

### 🌟 游戏亮点

- **程序化地图生成**：每局游戏生成独特的地图布局，确保可重玩性
- **丰富的卡牌机制**：12+ 张独特卡牌，涵盖攻击、防御、法力控制等策略
- **多样的房间类型**：6 种不同类型的房间，提供战斗、探索、交易等多种体验
- **深度的遗物系统**：被动增益效果，可叠加组合创造强大连击
- **完整的账户系统**：支持用户注册登录、存档管理、游戏统计
- **精美的视觉效果**：URP 渲染管线 + DOTween 动画，流畅的战斗体验

---

## ✨ 核心特性

### 🎴 卡牌构建
- ✅ 抽牌/弃牌/消耗牌三堆机制
- ✅ 每回合抽 5 张牌，手牌上限 11 张
- ✅ 弃牌堆洗牌回抽牌堆的循环机制
- ✅ 临时卡牌系统（战斗结束后清除）
- ✅ 卡牌稀有度分级（Common 等）

### ⚔️ 回合制战斗
- ✅ 玩家回合 → 敌人回合交替进行
- ✅ 法力值管理系统（每回合重置）
- ✅ 多种目标选择模式（手动/自动/全体）
- ✅ 状态效果系统（燃烧、火焰护盾等）
- ✅ 敌人 AI 行为树（普通敌/Boss 不同策略）

### 🗺️ Roguelike 地图
- ✅ 自底向上多层级地图结构
- ✅ 节点可达性路径追踪算法
- ✅ 单调不降区间连接规则确保连通性
- ✅ 随机房间类型分配（保证 Boss 在顶层）
- ✅ 地图状态保存与加载（支持继续游戏）

### 💎 遗物与成长
- ✅ 条件触发式遗物效果
- ✅ 计数器机制（满足条件次数后触发）
- ✅ 目标选择灵活性（施法者/自动目标）
- ✅ 宝箱奖励和商店购买两种获取途径

### 👤 账户系统
- ✅ 用户注册/登录（本地 JSON 存储）
- ✅ 游客模式支持（无需登录即可游玩）
- ✅ 存档自动保存（仅登录用户）
- ✅ 游戏统计追踪（胜场/死亡/时长/收集）

---

## 🛠️ 技术栈

| 技术 | 版本 | 用途 |
|------|------|------|
| **Unity Editor** | 6000.2.12f1 | 游戏引擎 |
| **Universal Render Pipeline (URP)** | 17.2.0 | 高性能渲染管线 |
| **C# / .NET** | Latest | 编程语言 |
| **DOTween (Demigiant)** | Latest | 补间动画库 |
| **TextMesh Pro** | Latest | 高质量文本渲染 |
| **Unity Input System** | 1.14.2 | 新输入管理系统 |
| **Unity Timeline** | 1.8.9 | 时间线动画控制 |
| **Unity Splines** | 2.8.2 | 样条曲线工具 |
| **SerializeReferenceEditor** | Latest | ScriptableObject 可视化编辑 |

### 🔧 关键 Unity 包

```json
{
  "com.unity.render-pipelines.universal": "17.2.0",
  "com.unity.inputsystem": "1.14.2",
  "com.unity.timeline": "1.8.9",
  "com.unity.splines": "2.8.2",
  "com.unity.test-framework": "1.6.0",
  "com.unity.ugui": "2.0.0",
  "com.unity.visualscripting": "1.9.9",
  "com.unity.probuilder": "6.0.9"
}
```

---

## 📁 项目结构

```
Examination/
├── Assets/                          # 游戏资源根目录
│   ├── _Scripts/                    # 📜 核心脚本代码
│   │   ├── AI/                      #    敌人 AI 逻辑
│   │   │   ├── BasicEnemyAI.cs      #    基础敌人 AI
│   │   │   ├── BossAI.cs            #    Boss 专用 AI
│   │   │   └── MinionA_AI.cs        #    小怪 A 的 AI
│   │   │
│   │   ├── Creators/                #    对象创建工厂
│   │   │   ├── CardViewCreator.cs   #    卡牌视图创建器
│   │   │   ├── EnemyViewCreator.cs  #    敌人视图创建器
│   │   │   ├── RewardCreator.cs     #    奖励创建器
│   │   │   └── ShopGenerator.cs     #    商店物品生成器
│   │   │
│   │   ├── Data/                    #    数据模型（ScriptableObject）
│   │   │   ├── CardData.cs          #    卡牌数据定义
│   │   │   ├── EnemyData.cs         #    敌人数据定义
│   │   │   ├── HeroData.cs          #    英雄数据定义
│   │   │   ├── MapData.cs           #    地图配置数据
│   │   │   ├── MapNodeData.cs       #    地图节点数据
│   │   │   ├── PerkData.cs          #    遗物数据定义
│   │   │   ├── PotionData.cs        #    药水数据定义
│   │   │   ├── RewardData.cs        #    奖励数据定义
│   │   │   └── ShopItem.cs          #    商店物品数据
│   │   │
│   │   ├── Database/                #    数据库管理器
│   │   │   ├── Database.cs          #    通用数据库基类
│   │   │   ├── CardDatabase.cs      #    卡牌数据库
│   │   │   ├── EnemyDatabase.cs     #    敌人数据库
│   │   │   ├── PerkDatabase.cs      #    遗物数据库
│   │   │   └── PotionDatabase.cs    #    药水数据库
│   │   │
│   │   ├── Enums/                  #    枚举定义
│   │   │   ├── ModuleType.cs       #    模块类型
│   │   │   ├── Rarity.cs           #    稀有度
│   │   │   ├── RewardType.cs       #    奖励类型
│   │   │   ├── RoomType.cs         #    房间类型
│   │   │   └── StatusEffectType.cs #    状态效果类型
│   │   │
│   │   ├── GameActions/            #    游戏动作（命令模式）
│   │   │   ├── DealDamageGA.cs     #    造成伤害动作
│   │   │   ├── DrawCardsGA.cs      #    抽牌动作
│   │   │   ├── HealGA.cs           #    治疗动作
│   │   │   ├── PlayCardGA.cs       #    出牌动作
│   │   │   ├── SpendManaGA.cs      #    消耗法力动作
│   │   │   └── ...                 #    更多动作类型
│   │   │
│   │   ├── Manager/                #    全局管理器（单例）
│   │   │   ├── AccountManager.cs   #    账户管理器
│   │   │   ├── AudioManager.cs     #    音频管理器
│   │   │   ├── BattleManager.cs    #    战斗管理器
│   │   │   ├── EventManager.cs     #    事件管理器
│   │   │   ├── GameFlowManager.cs  #    游戏流程管理器
│   │   │   ├── MapManager.cs       #    地图管理器
│   │   │   └── TooltipManager.cs   #    提示框管理器
│   │   │
│   │   ├── Models/                 #    业务模型
│   │   │   ├── Card.cs             #    卡牌实例
│   │   │   ├── Effect.cs           #    效果基类
│   │   │   ├── Perk.cs             #    遗物实例
│   │   │   ├── Potion.cs           #    药水实例
│   │   │   ├── TargetMode.cs       #    目标模式
│   │   │   └── AutoTargetEffect.cs #    自动目标效果包装
│   │   │
│   │   ├── Systems/                #    核心系统逻辑
│   │   │   ├── BurnSystem.cs       #    燃烧状态系统
│   │   │   ├── CardSystem.cs       #    卡牌管理系统
│   │   │   ├── EffectSystem.cs     #    效果执行系统
│   │   │   ├── EnemySystem.cs      #    敌人行为系统
│   │   │   ├── GoldSystem.cs       #    金币系统
│   │   │   ├── HealthSystem.cs     #    生命值系统
│   │   │   ├── HeroSystem.cs       #    英雄属性系统
│   │   │   ├── MapGenerate.cs      #    地图生成系统
│   │   │   ├── ManaSystem.cs       #    法力值系统
│   │   │   ├── PerkSystem.cs       #    遗物激活系统
│   │   │   ├── PlayerDeck.cs       #    玩家牌组管理
│   │   │   ├── PotionSystem.cs     #    药水使用系统
│   │   │   ├── RewardSystem.cs     #    奖励发放系统
│   │   │   └── StatusEffectSystem.cs # 状态效果系统
│   │   │
│   │   ├── TargetModes/            #    目标选择策略
│   │   │   ├── AllEnemiesTM.cs     #    全体敌人目标
│   │   │   ├── HeroTM.cs           #    英雄自身目标
│   │   │   ├── NoTM.cs             #    无需目标
│   │   │   └── RandomEnemyTM.cs    #    随机敌人目标
│   │   │
│   │   ├── UI/                     #    用户界面组件
│   │   │   ├── Map/MapNode.cs      #    地图节点 UI
│   │   │   ├── BattleRewardPanel.cs # 战斗奖励面板
│   │   │   ├── CardDatabaseUI.cs   #    卡牌收集界面
│   │   │   ├── LoginPanel.cs       #    登录面板
│   │   │   ├── MenuUI.cs           #    主菜单 UI
│   │   │   ├── RegisterPanel.cs    #    注册面板
│   │   │   ├── ShopPanel.cs        #    商店面板
│   │   │   ├── TopBarUI.cs         #    顶部信息栏
│   │   │   └── TutorialPanel.cs    #    新手教程面板
│   │   │
│   │   ├── Views/                  #    视图层（MVC 中的 V）
│   │   │   ├── ArrowView.cs        #    攻击箭头视图
│   │   │   ├── CardView.cs         #    卡牌视图
│   │   │   ├── CombatantView.cs    #    战斗单位基类视图
│   │   │   ├── EnemyView.cs        #    敌人视图
│   │   │   ├── HandView.cs         #    手牌区域视图
│   │   │   └── HeroView.cs         #    英雄视图
│   │   │
│   │   ├── Effects/                #    具体效果实现
│   │   │   ├── DealDamageEffect.cs #    伤害效果
│   │   │   ├── DrawCardsEffect.cs  #    抽牌效果
│   │   │   ├── ExhaustEffect.cs    #    消耗效果
│   │   │   ├── FireShieldEffect.cs #    火焰护盾效果
│   │   │   ├── HealEffect.cs       #    治疗效果
│   │   │   └── RefillManaEffect.cs #    恢复法力效果
│   │   │
│   │   ├── General/                #    通用工具
│   │   │   ├── Singleton.cs        #    单例基类
│   │   │   ├── PersistentSingleton.cs # 持久化单例
│   │   │   ├── ActionSystem/       #    动作系统核心
│   │   │   │   ├── ActionSystem.cs #    动作调度器
│   │   │   │   ├── GameAction.cs   #    动作基类
│   │   │   │   └── ReactionTiming.cs # 反应时机枚举
│   │   │   └── Util/               #    工具类
│   │   │       ├── MouseUtil.cs    #    鼠标工具
│   │   │       └── RandomUtility.cs # 随机数工具
│   │   │
│   │   ├── Handler/                #    交互处理器
│   │   │   ├── BattleRewardHandler.cs  # 战斗奖励处理
│   │   │   └── MapDragHandler.cs       # 地图拖拽处理
│   │   │
│   │   ├── Interfaces/             #    接口定义
│   │   │   └── IHaveCaster.cs      #    施法者接口
│   │   │
│   │   ├── PerkCondition/          #    遗物触发条件
│   │   │   ├── OnTurnEndedCondition.cs  # 回合结束条件
│   │   │   └── OnEnemyAttackCondition.cs # 敌人攻击条件
│   │   │
│   │   └── Extensions/             #    扩展方法
│   │       └── ListExtensions.cs   #    List 扩展
│   │
│   ├── Data/                       # 📊 游戏数据资源
│   │   ├── Cards/                   #    卡牌数据（ScriptableObject）
│   │   │   ├── Normal Attack.asset  #    普通攻击
│   │   │   ├── Fireball.asset       #    火球术
│   │   │   ├── Heal.asset           #    治疗
│   │   │   ├── Armor Up.asset       #    护甲提升
│   │   │   ├── Draw.asset           #    抽牌
│   │   │   ├── One Punch.asset      #    一拳
│   │   │   └── ...                  #    更多卡牌
│   │   ├── Enemies/                 #    敌人数据
│   │   │   ├── Slime.asset          #    史莱姆
│   │   │   ├── Red Slime.asset      #    红色史莱姆
│   │   │   ├── Elite-slime.asset    #    精英史莱姆
│   │   │   ├── Robot A.asset        #    机器人 A
│   │   │   ├── Robot B.asset        #    机器人 B
│   │   │   └── Robot Boss.asset     #    机器人 Boss
│   │   ├── Heroes/                  #    英雄数据
│   │   │   └── DefaultHero.asset    #    默认英雄
│   │   ├── Map/                     #    地图配置
│   │   │   └── DefaultMap.asset     #    默认地图设置
│   │   ├── Perks/                   #    遗物数据
│   │   │   ├── CounterAttack.asset  #    反击遗物
│   │   │   └── ManaWaterFall.asset  #    法力瀑布遗物
│   │   ├── Potion/                  #    药水数据
│   │   │   └── Heal.asset           #    治疗药水
│   │   └── Node.meta                #    节点元数据
│   │
│   ├── Media/                      # 🎨 媒体资源
│   │   ├── *.png                    #    UI 图片素材
│   │   ├── *.jpeg                   #    头像图片
│   │   └── *.mp4                    #    视频（宝箱动画）
│   │
│   ├── Audio/                      # 🔊 音频资源
│   │   ├── Village.mp3             #    村庄背景音乐
│   │   └── Village.mp4             #    村庄视频
│   │
│   ├── Free Pack/                  # 🎵 免费音效包
│   │   ├── *.wav                    #    各种音效文件
│   │   └── (爆炸/射击/撞击等)
│   │
│   ├── Prefabs/                    # 🎭 预制体
│   │   ├── CardView.prefab         #    卡牌预制体
│   │   ├── NodePrefab.prefab       #    地图节点预制体
│   │   ├── Line.prefab             #    连线预制体
│   │   ├── TopBarUI.prefab         #    顶部栏预制体
│   │   └── ...
│   │
│   ├── Scenes/                     # 🎬 场景文件
│   │   ├── MenuScene.unity         #    主菜单场景
│   │   ├── MapScene.unity          #    地图场景
│   │   └── BattleScene.unity       #    战斗场景
│   │
│   ├── Plugins/                    # 🧩 第三方插件
│   │   └── Demigiant/DOTween       #    DOTween 动画库
│   │
│   ├── Shader/                     # 🎨 自定义着色器
│   │   ├── Line.shader             #    连线着色器
│   │   └── UI/UIPanel.shader       #    UI 面板着色器
│   │
│   ├── TextMesh Pro/               # 📝 字体资源
│   │   └── Fonts/                   #    中文字体（微软雅黑）
│   │
│   └── Resources/                  # 📦 运行时资源
│       ├── Databases/              #    数据库资源
│       ├── UI/                     #    UI 预制体
│       └── DefaultHero.asset       #    默认英雄数据
│
├── Packages/                        # 📦 依赖包配置
│   ├── manifest.json                #    包清单
│   └── packages-lock.json           #    包锁定文件
│
├── ProjectSettings/                  # ⚙️ 项目设置
│   ├── ProjectVersion.txt           #    Unity 版本
│   ├── AudioManager.asset          #    音频管理器
│   └── InputManager.asset          #    输入管理器
│
├── Library/                         # 📚 缓存库（不版本控制）
├── UserSettings/                    # 👤 用户偏好设置
└── Logs/                            # 📋 日志文件
```

---

## 🎮 游戏系统

### 🃏 卡牌系统

卡牌是游戏的核心机制，玩家通过打出各种卡牌来攻击敌人、防御或增强自身。

#### 卡牌数据结构

```csharp
public class CardData : ScriptableObject
{
    public string Description;           // 卡牌描述
    public int Mana;                      // 法力消耗
    public Sprite Image;                  // 卡牌图像
    public Rarity Rarity;                 // 稀有度
    public List<Effect> ManualTargetEffects;  // 手动目标效果
    public List<AutoTargetEffect> OtherEffects; // 自动目标效果
}
```

#### 牌堆机制

游戏采用 **四堆式** 牌库设计：

| 牌堆 | 说明 | 特性 |
|------|------|------|
| **Draw Pile (抽牌堆)** | 待抽取的卡牌 | 每回合从这里抽牌 |
| **Hand (手牌)** | 当前可用卡牌 | 上限 11 张 |
| **Discard Pile (弃牌堆)** | 已使用的卡牌 | 回合结束时手牌进入此处 |
| **Exhaust Pile (消耗牌堆)** | 永久移除的卡牌 | 本局不再出现 |

#### 核心流程

1. **回合开始**：从抽牌堆抽取 5 张卡牌
2. **出牌阶段**：消耗法力值打出手牌
3. **回合结束**：所有手牌移入弃牌堆
4. **洗牌机制**：当抽牌堆为空时，弃牌堆洗入抽牌堆

#### 卡牌操作 API

```csharp
// 抽取卡牌
ActionSystem.Instance.AddReaction(new DrawCardsGA(5));

// 打出卡牌（需要指定目标和卡牌）
ActionSystem.Instance.AddReaction(new PlayCardGA(card, target));

// 消耗卡牌（永久移除）
ActionSystem.Instance.AddReaction(new ExhaustGA(card));
```

---

### ⚔️ 战斗系统

采用 **回合制** 战斗模式，玩家与敌人轮流行动。

#### 战斗流程

```
[玩家回合]
  ↓
1. 抽牌阶段 → 抽取 5 张牌
  ↓
2. 出牌阶段 → 消耗法力打出手牌
  ↓
3. 结束回合按钮 → 弃掉所有手牌
  ↓
[敌人回合]
  ↓
1. 敌人 AI 决策
  ↓
2. 执行敌人行动（攻击/技能/召唤）
  ↓
3. 检查战斗结束条件
  ↓
[循环回到玩家回合]
```

#### 法力值系统

- 每回合开始时 **法力值重置为满值**
- 默认最大法力值：**3 点**
- 打出卡牌需要消耗对应法力
- 可通过卡牌或遗物增加法力上限

#### 伤害计算流程

```csharp
// 伤害执行链
DealDamageGA → DamageSystem.ApplyDamage() → EnemyView.TakeDamage()
                                          ↓
                                    检查死亡 → 触发奖励/结算
```

#### 状态效果

| 效果名称 | 类型 | 描述 |
|----------|------|------|
| **Burn (燃烧)** | 负面 | 回合结束时受到持续伤害 |
| **Fire Shield (火焰护盾)** | 正面 | 受到攻击时对攻击者造成反弹伤害 |

---

### 🗺️ 地图探索系统

地图采用 **程序化生成** 技术，每次游戏都产生独特的布局。

#### 地图结构

```
        [Boss]  ← 第 N 层（固定 1 个节点）
        /   \
    [Elite] [Event]  ← 第 N-1 层
    / | \     |
[Enemy] [Shop] [Treasure]  ← 中间层（随机 2-6 个节点）
    \ |     /
  [Rest] [Enemy]  ← 第 2 层
      \   /
      [Start]  ← 第 1 层（4-5 个起始节点）
```

#### 生成算法特点

1. **层数可控**：通过 `MapData` 配置总层数（默认约 10 层）
2. **节点数量变化**：
   - 底层：4-5 个节点
   - 中间层：2-6 个节点（相邻层变化 ±1）
   - 顶层：固定 1 个 Boss 节点
3. **连接规则**：采用 **单调不降区间连接算法**，确保：
   - 所有路径通向 Boss
   - 无孤立节点
   - 合理的分支选择
4. **随机性控制**：使用 `RandomUtility` 统一管理随机种子，保证可复现性

#### 节点状态机

```
[Locked] → [Reachable] → [Visited] → [Current]
   ↑                          ↓
   └──────────────────────────┘ (已访问但未完成)
```

- **Locked**：不可到达（前置节点未访问）
- **Reachable**：可点击进入
- **Visited**：已完成（变灰）
- **Current**：当前所在位置

#### 地图操作

```csharp
// 生成新地图
mapGenerator.GenerateMap();

// 从存档重建
mapGenerator.RebuildMapViewFromData(existingData);

// 更新所有节点状态
mapGenerator.RefreshAllNodes();
```

---

### 👤 角色与敌人系统

#### 英雄属性

```csharp
public class HeroData : ScriptableObject
{
    public int MaxHealth = 100;        // 最大生命值
    public List<CardData> Deck;        // 初始牌组
}
```

英雄拥有以下核心属性：

- **生命值 (HP)**：默认 100 点，归零则失败
- **法力值 (MP)**：每回合重置，用于出牌
- **金币 (Gold)**：用于商店交易
- **牌组 (Deck)**：初始卡牌集合，可通过奖励扩充

#### 敌人类型

| 类型 | 示例 | 特点 |
|------|------|------|
| **普通敌人** | 史莱姆、红色史莱姆 | 基础属性，简单 AI |
| **精英敌人** | 精英史莱姆 | 强化属性，复杂技能 |
| **Boss** | 机器人 Boss | 高血量，特殊机制，召唤小怪 |

#### 敌人 AI 系统

```csharp
// 基础敌人 AI（简单模式）
public class BasicEnemyAI : EnemyAI { }

// Boss AI（复杂模式，可能召唤小怪）
public class BossAI : EnemyAI { }

// 小怪 AI（跟随 Boss 行动）
public class MinionA_AI : EnemyAI { }
```

**AI 决策流程**：
1. 分析战场局势（自身血量、玩家状态）
2. 根据权重表选择行动（攻击/防御/技能）
3. 选择目标（优先低血量目标）
4. 执行行动并播放动画

---

### 💎 遗物（Perk）系统

遗物是 **被动增益效果**，一旦获得即永久生效（除非被移除）。

#### 遗物数据结构

```csharp
public class PerkData : ScriptableObject
{
    public string Description;              // 遗物描述
    public Sprite Image;                     // 图标
    public PerkCondition PerkCondition;      // 触发条件
    public AutoTargetEffect AutoTargetEffect; // 触发效果
    public int RequiredCount;               // 所需触发次数（0=每次触发）
    public bool UseActionCasterAsTarget;     // 是否以施法者为目标
    public bool UseAutoTarget;              // 是否使用自动目标
}
```

#### 触发条件类型

| 条件类名 | 触发时机 | 示例用途 |
|----------|----------|----------|
| `OnTurnEndedCondition` | 每回合结束时 | 回合恢复法力 |
| `OnEnemyAttackCondition` | 敌人攻击时 | 反击伤害 |

#### 工作原理

```
[事件发生] → [检查条件] → [计数器+1] → [达到阈值?] → [执行效果]
                                              ↓ Yes
                                        [重置计数器] → [触发效果]
```

#### 示例：反击遗物

```csharp
// 当敌人攻击时，有 30% 概率反击 10 点伤害
CounterAttack:
  Condition: OnEnemyAttackCondition
  RequiredCount: 0 (每次触发)
  Effect: DealDamage(10, 30% chance to attacker)
```

---

### 🏪 商店与经济系统

#### 金币获取途径

- 击败敌人奖励
- 宝箱房间偶尔包含金币
- 完成特殊事件

#### 商店功能

商店房间允许玩家花费金币购买物品：

```csharp
// 生成商店物品（3-5 个商品）
List<ShopItem> shopItems = ShopGenerator.GenerateShopItems(3, 5);

// 显示商店界面
shopPanel.ShowShop(shopItems);
```

**商品类型**：
- 🃏 **卡牌**：加入永久牌组
- 💊 **药水**：即时效果物品
- 💰 **移除卡牌**：精简牌组（提高抽牌一致性）

#### 药水系统

药水是 **一次性消耗品**，可在战斗中使用或立即生效：

| 药水 | 效果 |
|------|------|
| **治疗药水** | 立即恢复 30% 最大生命值 |

---

### 👤 账户与存档系统

#### 账户功能

```csharp
public class AccountManager : PersistentSingleton<AccountManager>
{
    // 注册新账户
    public void Register(string username, string password, ...);

    // 登录验证
    public bool Login(string username, string password);

    // 当前登录用户
    public AccountData CurrentAccount { get; }
}
```

**支持的账号信息**：
- 用户名 / 密码
- QQ 或邮箱
- 手机号码
- 自定义头像（本地图片路径）

#### 存档机制

- **存储格式**：JSON 文件
- **存储位置**：本地 persistentDataPath
- **自动保存时机**：
  - 战斗结束返回地图时
  - 进入新节点前
  - 应用退出时
  - 每隔一段时间（防止崩溃丢失）

#### 游戏统计

系统会记录以下统计数据（仅登录用户）：

```csharp
public class AccountData
{
    public int cardsCollected;      // 收集的卡牌总数
    public int nodesVisited;        // 访问的节点数
    public float totalPlayTimeHours; // 总游戏时长（小时）
    public int wins;                // 获胜次数
    public int deaths;              // 死亡次数
}
```

**游客模式**：
- 未登录用户可以正常游戏
- 但无法保存进度
- 退出后进度丢失

---

## 🎯 游戏流程

### 完整游戏循环

```
┌─────────────────────────────────────────────────────┐
│                    🎮 主菜单                        │
│  [开始新游戏]  [继续游戏]  [设置]  [退出]           │
└───────────────────────┬─────────────────────────────┘
                        ↓ 开始新游戏
┌─────────────────────────────────────────────────────┐
│                   🗺️ 地图场景                       │
│                                                     │
│   ┌───┬───┬───┐                                     │
│   │ ? │ ⚔️ │ ♦️ │  ← 点击节点进入不同房间           │
│   └─┼─┼─┼─┘                                       │
│   ┌───┼───┐                                        │
│   │ 🏪 │ ❤️ │  ← 商店 / 休息                       │
│   └───┴───┘                                        │
│                                                     │
│   当前: ❤️ 100/100 | 💰 50 | 🃏 12 张              │
└───────────────────────┬─────────────────────────────┘
                        ↓ 选择节点
              ┌─────────┼─────────┐
              ↓         ↓         ↓
        ┌──────────┐ ┌──────┐ ┌──────────┐
        │  ⚔️ 战斗  │ │ 💎宝箱│ │  🏪 商店 │
        └────┬─────┘ └──┬───┘ └────┬─────┘
             ↓          ↓          ↓
    ┌────────────────┐  │    ┌──────────┐
    │  ⚔️ 战斗场景   │  │    │ 购买物品 │
    │                │  │    └────┬─────┘
    │  [抽牌]→[出牌] │  │         ↓
    │  →[结束回合]   │  │    返回地图
    │       ↓        │  │
    │  [胜利/失败]   │  │
    └───────┬────────┘  │
            ↓           │
    ┌────────────────┐  │
    │  🎁 奖励选择   │  │
    │  (卡牌/遗物/金) │  │
    └───────┬────────┘  │
            ↓           │
      返回地图 ←────────┘
            ↓
      [继续探索] 或 [挑战 Boss]
            ↓
    ┌────────────────┐
    │  👑 最终胜利！  │
    │  或 💀 死亡...  │
    └────────────────┘
```

### 场景切换流程

```csharp
// GameFlowManager 场景管理
MenuScene → MapScene → BattleScene → MapScene → ... → BossBattle → Victory/Defeat
```

**关键方法**：

```csharp
// 开始新游戏（重置所有系统状态）
GameFlowManager.Instance.StartNewGame();

// 继续上次进度
GameFlowManager.Instance.ContinueGame();

// 节点点击处理
GameFlowManager.Instance.OnNodeClicked(node);

// 返回地图
GameFlowManager.Instance.ReturnToMap(battleWon);
```

---

## 🗺️ 房间类型

地图上共有 **6 种** 不同类型的房间，每种提供独特的体验：

| 图标 | 类型 | 名称 | 描述 | 发生事件 |
|------|------|------|------|----------|
| ⚔️ | `Enemy` | 普通敌人 | 与 1-3 个普通敌人战斗 | 战斗 → 奖励 |
| 👑 | `Elite` | 精英敌人 | 与强化版敌人战斗（更难） | 战斗 → 丰厚奖励 |
| 😈 | `Boss` | Boss 战 | 与 Boss 及其手下战斗 | 终极挑战 → 大量奖励 |
| 💎 | `Treasure` | 宝藏房间 | 从 3 个遗物中选择 1 个 | 直接获得遗物 |
| 🏪 | `Shop` | 商店房间 | 使用金币购买卡牌/药水 | 交易界面 |
| ❤️ | `Rest` | 休息营地 | 恢复生命值或升级卡牌 | 二选一选项 |
| ❓ | `Event` | 随机事件 | 50% 概率战斗或休息 | 随机结果 |

### 房间分布规则

- **Boss 固定在最顶层**（1 个节点）
- **Elite 通常出现在倒数第 2-3 层**
- **普通敌人占大多数（~40%）**
- **Rest/Shop/Treasure/Event 均匀分布**

---

## 🃏 卡牌列表

游戏目前包含 **12 张** 卡牌，分为多个类别：

### ⚔️ 攻击卡牌

| 卡牌名称 | 法力消耗 | 效果 | 目标 | 描述 |
|----------|----------|------|------|------|
| **Normal Attack** | 1 | 造成 6 点伤害 | 单个敌人 | 基础攻击手段 |
| **Fireball** | 2 | 造成 12 点伤害 | 单个敌人 | 高伤害法术 |
| **One Punch** | 3 | 造成 25 点伤害 | 单个敌人 | 一击必杀（高费） |
| **Arrow Rain** | 1 | 造成 5 点伤害 | 全体敌人 | 范围攻击 |
| **Sword Fire** | 1 | 造成 8 点伤害 + 2 燃烧 | 单个敌人 | 带附加效果的攻击 |
| **Slime** | 1 | 召唤友方史莱姆 | 自身 | 召唤物辅助 |

### 🛡️ 防御/功能卡牌

| 卡牌名称 | 法力消耗 | 效果 | 目标 | 描述 |
|----------|----------|------|------|------|
| **Armor Up** | 1 | 获得 8 点护甲 | 自身 | 提升生存能力 |
| **Fire Shield** | 2 | 获得火焰护盾 | 自身 | 反弹伤害给攻击者 |
| **Heal** | 1 | 恢复 15 点生命 | 自身 | 即时治疗 |

### 📚 资源卡牌

| 卡牌名称 | 法力消耗 | 效果 | 目标 | 描述 |
|----------|----------|------|------|------|
| **Draw** | 0 | 抽 2 张牌 | 自身 | 过牌加速 |
| **Refill Mana** | 0 | 恢复 2 点法力 | 自身 | 资源回收 |
| **Burn Amplify** | 1 | 双倍燃烧效果 | 单个敌人 | 状态效果增强 |

### 卡牌使用示例

```csharp
// 创建一张火球术卡牌
CardData fireballData = Resources.Load<CardData>("Cards/Fireball");
Card fireball = new Card(fireballData);

// 打出火球术（指定目标敌人）
PlayCardGA playCardAction = new PlayCardGA(fireball, enemyTarget);
ActionSystem.Instance.AddReaction(playCardAction);
```

---

## 👾 敌人列表

游戏中共有 **6 种** 敌人单位：

### 普通敌人

| 敌人名称 | 生命值 | 攻击力 | 特殊能力 | 描述 |
|----------|--------|--------|----------|------|
| **Slime (史莱姆)** | 20 | 5 | 基础移动 | 最基础的敌人，适合新手练习 |
| **Red Slime (红色史莱姆)** | 30 | 8 | 高攻击力 | 强化版史莱姆，更具威胁 |

### 机器人系列

| 敌人名称 | 生命值 | 攻击力 | 特殊能力 | 描述 |
|----------|--------|--------|----------|------|
| **Robot A (机器人 A)** | 40 | 10 | 机械护甲 | 中期常见敌人 |
| **Robot B (机器人 B)** | 35 | 12 | 快速攻击 | 高攻速变种 |

### 精英 & Boss

| 敌人名称 | 生命值 | 攻击力 | 特殊能力 | 描述 |
|----------|--------|--------|----------|------|
| **Elite Slime (精英史莱姆)** | 80 | 15 | 分裂/强化 | 区域 Boss 级别敌人 |
| **Robot Boss (机器人 Boss)** | 200 | 25 | 召唤小怪 | 最终 Boss，极高难度 |

### 敌人配置示例

```csharp
// 在地图节点中配置敌人组合
MapNodeData nodeData = new MapNodeData();
nodeData.roomType = RoomType.Enemy;
nodeData.enemyDataList = new List<EnemyData>
{
    enemyDatabase.GetEnemy("Slime"),
    enemyDatabase.GetEnemy("Red Slime")
};
// 该节点将同时遭遇 2 个敌人
```

---

## 💾 数据持久化

### 存储架构

```
Application.persistentDataPath/
├── accounts.json          # 账户数据库
├── map_save_<username>.json  # 地图存档（按用户）
└── settings.json          # 游戏设置（可选）
```

### 序列化格式

**账户数据 (accounts.json)**：
```json
{
  "accounts": [
    {
      "username": "Player1",
      "password": "hashed_password",
      "qqEmail": "player@example.com",
      "cardsCollected": 25,
      "nodesVisited": 50,
      "totalPlayTimeHours": 12.5,
      "wins": 3,
      "deaths": 7,
      "creationDate": "2026-01-01T00:00:00"
    }
  ]
}
```

**地图存档 (map_save_xxx.json)**：
```json
{
  "currentLayer": 5,
  "currentRow": 2,
  "nodesVisited": ["0_1", "1_2", "2_0", "3_1", "4_2"],
  "heroHealth": 75,
  "gold": 120,
  "deck": ["Normal Attack", "Fireball", "Heal", "..."],
  "perks": ["CounterAttack"]
}
```

### 自动保存策略

```csharp
// 1. 战斗结束后立即保存
public void ReturnToMap(bool battleWon)
{
    if (AccountManager.Instance.CurrentAccount != null)
    {
        MapManager.Instance.SaveMapToDisk(); // 立即保存
    }
}

// 2. 定期防丢失（每分钟）
void Update()
{
    if (Time.frameCount % 3600 == 0)
        SaveAccounts();
}

// 3. 应用退出时
private void OnApplicationQuit()
{
    if (AccountManager.Instance.CurrentAccount != null)
        MapManager.Instance.SaveMapToDisk();
}
```

---

## 🚀 快速开始

### 环境要求

- **操作系统**：Windows 10/11 (64-bit)
- **Unity Editor**：6000.2.12f1 或更高版本
- **磁盘空间**：≥ 5 GB（含项目依赖）
- **内存**：≥ 8 GB RAM
- **显卡**：支持 DirectX 11 或 OpenGL 4.5

### 安装步骤

1. **克隆项目**
   ```bash
   git clone <repository-url>
   cd Examination
   ```

2. **用 Unity Hub 打开**
   - 打开 Unity Hub
   - 点击 "Add" 添加项目路径
   - 选择项目打开（Unity 会自动识别版本）

3. **等待依赖导入**
   - 首次打开时，Unity 会导入包和编译脚本
   - 预计等待时间：2-5 分钟（取决于机器性能）
   - 控制台无报错即表示成功

4. **运行游戏**
   - 在 Project 窗口中找到 `Assets/Scenes/MenuScene.unity`
   - 双击打开场景
   - 点击 Unity 编辑器顶部的 ▶️ (Play) 按钮
   - 享受游戏！

### 快捷键（运行时）

| 按键 | 功能 |
|------|------|
| **鼠标左键** | 选择/确认 |
| **鼠标右键** | 取消 |
| **ESC** | 暂停/返回 |

---

## 🔧 开发环境配置

### 推荐工具

- **IDE**: JetBrains Rider 2024.x（已集成）
- **版本控制**: Git + GitHub/GitLab
- **.gitignore 配置**：已排除 `Library/`, `Logs/`, `Temp/`, `obj/`, `.vs/`

### 项目规范

#### 命名约定

```csharp
// 类名：PascalCase
public class CardSystem : MonoBehaviour { }

// 公有方法/属性：PascalCase
public void StartNewGame() { }
public int Health { get; private set; }

// 私有字段：_camelCase
private List<Card> _drawPile;
private bool _isBattleOver;

// 常量：UPPER_SNAKE_CASE
private const int HAND_LIMIT = 11;
private const int DRAW_CARDS_PER_TURN = 5;

// ScriptableObject 文件名：PascalCase + .asset
Normal Attack.asset
Fire Shield.asset
```

#### 代码组织原则

1. **单一职责**：每个类只做一件事
2. **依赖注入**：通过 SerializeField 引用外部组件
3. **事件驱动**：使用 ActionSystem 解耦模块通信
4. **单例模式**：全局管理器使用 PersistentSingleton<T>

#### 调试技巧

```csharp
// 使用 Debug.Log 输出关键信息
Debug.Log($"[CardSystem] 抽牌完成，手牌数量：{hand.Count}");

// 使用条件断点排查问题
if (card == null)
{
    Debug.LogError("严重错误：卡牌对象为空！");
    yield break;
}

// 使用 #region 分区折叠代码
#region 初始化地图
// ... 初始化代码
#endregion
```

---

## 📊 系统架构图

### 整体架构（三层架构）

```
┌─────────────────────────────────────────────────────┐
│                   表现层 (Presentation)              │
│  ┌──────────┬──────────┬──────────┬──────────────┐  │
│  │  Views/  │   UI/    │ Effects/ │  Animations  │  │
│  │ (MVC-V)  │ (Canvas) │ (VFX)    │  (DOTween)   │  │
│  └────┬─────┴────┬─────┴────┬─────┴──────┬───────┘  │
│       │          │          │              │          │
├───────┼──────────┼──────────┼──────────────┼──────────┤
│                   业务逻辑层 (Business Logic)          │
│  ┌────┴────┐ ┌────┴────┐ ┌─┴────────┐ ┌───┴────────┐ │
│  │Systems/ │ │ Manager │ │  Models  │ │ GameActions│ │
│  │(Core)   │ │(Control)│ │ (Domain) │ │  (Command) │ │
│  └────┬────┘ └────┬────┘ └────┬─────┘ └─────┬──────┘ │
│       │          │          │              │          │
├───────┼──────────┼──────────┼──────────────┼──────────┤
│                     数据层 (Data)                    │
│  ┌────┴────┐ ┌────┴────┐ ┌──┴────────┐ ┌───┴───────┐ │
│  │ Data/   │ │Database │ │  Enums/   │ │ Interfaces│ │
│  │(SO)     │ │(Loader) │ │ (Consts)  │ │ (Contract)│ │
│  └─────────┘ └─────────┘ └───────────┘ └───────────┘ │
└─────────────────────────────────────────────────────┘
```

### 核心通信机制：ActionSystem

```
[触发源] ──AddReaction()──→ [ActionSystem 队列] ──Perform()──→ [执行者]
                                                    ↓
                                              [协程/异步处理]
                                                    ↓
                                              [完成回调]
```

**优势**：
- ✅ 松耦合：模块间无需直接引用
- ✅ 可扩展：轻松添加新动作类型
- ✅ 可调试：完整的动作日志
- ✅ 有序执行：避免竞态条件

### 关键设计模式应用

| 模式 | 应用位置 | 用途 |
|------|----------|------|
| **单例模式** | Manager/*System | 全局访问点 |
| **观察者模式** | ActionSystem | 事件驱动通信 |
| **命令模式** | GameActions | 封装操作请求 |
| **工厂模式** | *Creator | 对象创建封装 |
| **策略模式** | TargetModes | 目标选择算法 |
| **MVC 模式** | Views/Systems/UI | 关注点分离 |
| **ScriptableObject** | Data/* | 数据驱动设计 |

---

## 🎨 UI/UX 设计

### 界面层次结构

```
Screen Space Overlay Canvas
├── TopBarCanvas (排序层: 100)
│   ├── TopBarUI (生命值/金币/层数显示)
│   ├── TooltipManager (悬浮提示框)
│   └── Dynamic Panels (宝藏/商店/休息面板)
│
├── MainCanvas (排序层: 0)
│   ├── MenuUI (主菜单)
│   ├── LoginPanel / RegisterPanel (登录注册)
│   └── TutorialPanel (新手引导)
│
└── BattleCanvas (战斗场景专用)
    ├── HandView (手牌区域)
    ├── EnemyBoardView (敌人区域)
    ├── HeroView (英雄状态)
    ├── DrawPileUI / DiscardPileUI / ExhaustPileUI (牌堆)
    ├── EndTurnButtonUI (结束回合按钮)
    ├── ManaUI (法力值显示)
    └── StatusEffectsUI (状态效果图标)
```

### 动画系统 (DOTween)

```csharp
// 卡牌抽出动画
CardView cardView = CreateCardView(card, drawPilePosition);
yield return handView.AddCard(cardView); // 滑入手牌

// 弃牌动画
cardView.transform.DOScale(Vector3.zero, 0.15f); // 缩小
cardView.transform.DOMove(discardPilePosition, 0.15f); // 移动
yield return tween.WaitForCompletion(); // 等待完成
Destroy(cardView.gameObject); // 销毁
```

### 视觉反馈

- **悬停效果**：卡牌放大 + 高亮边框
- **选中效果**：卡牌上浮 + 发光
- **出牌效果**：飞向目标 + 特效粒子
- **伤害数字**：飘字动画（-XX）
- **治疗数字**：绿色飘字 (+XX)

---

## 🔮 未来计划

### 🚧 开发路线图

#### v1.0 - 基础完善（当前阶段）
- [x] 核心卡牌战斗系统
- [x] 程序化地图生成
- [x] 基础敌人 AI
- [x] 账户与存档系统
- [ ] ~~更多卡牌种类~~（目标：30+）
- [ ] ~~更多敌人种类~~（目标：20+）
- [ ] 平衡性调整

#### v1.1 - 内容扩展
- [ ] 新增 2-3 位可选英雄（不同起始牌组）
- [ ] 新增 10+ 张卡牌
- [ ] 新增 5+ 种遗物
- [ ] 成就系统
- [ ] 每日挑战模式

#### v1.2 - 深度优化
- [ ] 难度选择（简单/普通/困难）
- [ ] 无尽模式
- [ ] 自定义模组支持
- [ ] 统计数据可视化
- [ ] 回放系统

#### v2.0 - 多平台与社交
- [ ] 移动端适配 (Android/iOS)
- [ ] 云存档同步
- [ ] 排行榜系统
- [ ] 多人对战模式
- [ ] Steam 集成

### 🐛 已知问题

1. **性能优化**：大量卡牌时帧率略有下降（需对象池）
2. **存档安全**：本地 JSON 可被篡改（后续加密）
3. **内存管理**：长时间游戏可能导致内存增长（需定期清理）

---
