# 指令列表
这里列出了 Spelako 一般用户可用的所有指令.

使用 `<` 和 `>` 包围的为必填参数, 使用 `[` 和 `]` 包围的为可选参数.

## /hypixel
描述: 获取指定玩家的 Hypixel 信息<br>
用法: `/hypixel <玩家> [分类]`<br>
示例:
- `/hypixel Peaksol` - 查询 Peaksol 的基本信息
- `/hypixel iTMG sw` - 查询 iTMG 的 Skywars 统计数据
- `/hypixel hypixel g` - 查询 hypixel 的公会信息

?> **分类**可以是下列之一:<br>- bedwars, bw<br>- skywars, sw<br>- uhc<br>- megawalls, mw<br>- blitzsg, bsg, hungergames<br>- guild, g<br>- skyblock, sb

### Skyblock 查询
#### 主指令
描述: 查询玩家所有存档, 及 Skyblock 相关查询指令的用法<br>
用法: `/hypixel <玩家> sb`

#### 查询技能等级
描述: 查询玩家各技能的等级<br>
用法: `/hypixel <玩家> sbs [存档名/序号]`<br>
示例:
- `/hypixel Rikkawww sbs 2` - 查询 Rikkawww 的第 2 个存档的各技能的等级.

#### 查询拍卖物品
描述: 查询玩家正在拍卖的所有物品信息<br>
用法: `/hypixel <玩家> sba [存档名/序号]`<br>
示例:
- `/hypixel Peaksol sba Cucumber` - 查询 Peaksol 所在的名为 Cucumber 的存档中正在拍卖的物品信息.

## /syuu
描述: 获取 SyuuNet 的玩家信息或排行榜<br>
用法: `/syuu user <玩家>` 或 `/syuu lb <排行榜分类>`<br>
示例:
- `/syuu user Reviaol` - 查询 Reviaol 的统计数据
- `/syuu lb s2p2` - 查询 Sharp2Prot2 排行榜

?> **排行榜分类**可以是下列之一:<br>- sharp2prot2, s2p2<br>- mcsg<br>- octc<br>- goldenapple, gapple<br>- archer, bow<br>- nodelay, combo<br>- soup<br>- builduhc, buhc<br>- debuff<br>- sharp4prot3, s4p3<br>- sumo<br>- axe<br>- spleef<br>- finaluhc<br>- bridge

## /mojang
描述: 获取指定玩家的 Mojang 账号信息<br>
用法: `/mojang <玩家/UUID>`<br>
示例:
- `/mojang Peaksol` - 使用 ID 查询 Mojang 账号信息
- `/mojang 2e951afe18f241e1ae021667f39e4f5b` - 使用 UUID 查询 Mojang 账号信息

## /help
描述: 查看此指令列表<br>
用法: `/help`

## /spelako
描述: 显示机器相关信息<br>
用法: `/spelako`