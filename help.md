# 命令列表
这里列出了 Spelako 的所有命令. 使用 `<` 和 `>` 包围的为必填参数, 使用 `[` 和 `]` 包围的为可选参数. 所有命令及其参数不区分大小写.

## /hypixel
描述: 获取指定玩家的 Hypixel 统计信息

命令用法: `/hypixel <玩家> [分类]`

<details>
<summary>可选分类</summary>

- guild, g (公会)
- bedwars, bw (起床战争)
- skywars, sw (空岛战争)
- uhc (极限生存冠军)
- mewagalls, mw (超级战墙)
- blitzsg, bsg, hungergames (闪电饥饿游戏)
- skyblock, sb (空岛生存)
- zombies, zb (僵尸末日)

?> 如果留空, 将显示玩家的 Hypixel 基本信息.

</details>

<details>
<summary>使用示例</summary>

- `/hypixel Peaksol` - 查询 <u>Peaksol</u> 的基本信息
- `/hypixel Technoblade g` - 查询 <u>Technoblade</u> 的<u>公会</u>信息
- `/hypixel iTMG sw` - 查询 <u>iTMG</u> 的<u>空岛战争</u>统计数据
- `/hypixel BedlessNoob bedwars` - 查询 <u>BedlessNoob</u> 的<u>起床战争</u>统计数据
- `/hypixel Dual megawalls` - 查询 <u>Dual</u> 的<u>超级战墙</u>统计数据

</details>

?> `/hyp` 是此命令的别名. 你可以直接使用 `/hyp` 来替换 `/hypixel`.

?> **空岛生存**和**僵尸末日**的查询方法在下文有详细说明.

### 空岛生存查询
#### 查询存档列表
描述: 查询玩家存档列表. (用于获取存档名/序号)

用法: `/hypixel <玩家> skyblock`

<details>
<summary>使用示例</summary>

- `/hypixel Minikloon skyblock` - 查询 <u>Minikloon</u> 的<u>存档列表</u>
- `/hypixel Peaksol sb` - 查询 <u>Peaksol</u> 的<u>存档列表</u>

</details>

?> `sb` 是参数 `skyblock` 的别名. 你可以直接使用 `sb` 来替换 `skyblock`.

#### 查询技能等级
描述: 查询玩家存档中各技能的等级

用法: `/hypixel <玩家> skyblock skills [存档名/序号]`

<details>
<summary>使用示例</summary>

- `/hypixel LeaPhant sb skills grape` - 查询 <u>Minikloon</u> 的 <u>Grape</u> 存档的技能信息
- `/hypixel Rikkawww sb s 2` - 查询 <u>Rikkawww</u> 的第 <u>2</u> 个存档的技能信息

?> 如果留空, 将显示玩家的第 1 个存档的技能信息.

</details>

?> `s` 或 `sk` 是参数 `skills` 的别名. 你可以直接使用 `s` 或 `sk` 来替换 `skills`.

#### 查询拍卖物品
描述: 查询玩家存档中正在拍卖的物品信息

用法: `/hypixel <玩家> sb auctions [存档名/序号]`

<details>
<summary>使用示例</summary>

- `/hypixel Shiiyu sb auctions zucchini` - 查询 <u>Shiiyu</u> 的 <u>Zucchini</u> 存档的物品拍卖信息
- `/hypixel YMCatlord sb a 3` - 查询 <u>YMCatlord</u> 的第 <u>3</u> 个存档的物品拍卖信息

?> 如果留空, 将显示玩家的第 1 个存档的物品拍卖信息.

</details>

?> `a` 或 `au` 是参数 `auctions` 的别名. 你可以直接使用 `a` 或 `au` 来替换 `auctions`.

### 僵尸末日查询
描述: 查询玩家在 Hypixel 僵尸末日中的统计信息

用法: `/hypixel <玩家> zb [地图] [难度]`

<details>
<summary>可选地图</summary>

- deadend, de (穷途末路)
- badblood, bb (坏血之宫)
- alienarcadium, aa (外星游乐园)

?> 如果留空, 将显示玩家所有地图的统计数据.

</details>

<details>
<summary>可选难度</summary>

- normal, norm (普通)
- hard (困难)
- rip (安息)

?> 如果留空, 将显示玩家所有难度的统计数据.

</details>

<details>
<summary>使用示例</summary>

- `/hypixel Peaksol zb` - 查询 <u>Peaksol</u> 在<u>全部</u>地图<u>全部</u>难度的统计信息
- `/hypixel Bzake zb aa` - 查询 <u>Bzake</u> 在<u>外星游乐园</u>地图<u>全部</u>难度的统计信息
- `/hypixel Typhoon_Alex zb de norm` - 查询 <u>Typhoon_Alex</u> 在<u>穷途末路</u>地图<u>普通</u>难度的统计信息

</details>

?> `zb` 是参数 `zombies` 的别名. 你可以直接使用 `zb` 来替换 `zombies`.

## /syuu
### 查询玩家排位信息
描述: 获取 SyuuNet 的玩家各模式排位信息

用法: `/syuu player <玩家>`

<details>
<summary>使用示例</summary>

- `/syuu player Distory` - 查询 <u>Distory</u> 的排位信息
- `/syuu user lipchya` - 查询 <u>lipchya</u> 的排位信息

</details>

?> `user` 是参数 `player` 的别名. 你可以直接使用 `user` 来替换 `player`.

### 查询排行榜
描述: 获取 SyuuNet 的 Practice 排行榜

用法: `/syuu leaderboard <分类>`

<details>
<summary>可选分类</summary>

- sharp2prot2, s2p2
- mcsg, sg
- octc
- gapple, goldenapple
- archer, bow
- nodelay, combo
- soup
- builduhc, buhc
- debuff
- sharp4prot3, s4p3
- sumo
- axe
- spleef
- finaluhc
- bridge
- mlgrush, mlg, rush

</details>

<details>
<summary>使用示例</summary>

- `/syuu leaderboard s2p2` - 查询 <u>Sharp2Prot2</u> 模式的排行榜
- `/hypixel lb buhc` - 查询 <u>BuildUHC</u> 模式的排行榜

</details>

?> `lb` 是参数 `leaderboard` 的别名. 你可以直接使用 `lb` 来替换 `leaderboard`.

## /minecraft
描述: 查询指定 ID 或 UUID 的 Minecraft 账户信息

用法: `/minecraft <ID/UUID>`

<details>
<summary>使用示例</summary>

- `/minecraft Peaksol` - 查询 ID 为 <u>Peaksol</u> 的 Minecrat 账户信息
- `/mc 2e951afe18f241e1ae021667f39e4f5b` - 查询 UUID 为 <u>2e951afe18f241e1ae021667f39e4f5b</u> 的 Minecrat 账户信息
- `/mc f7c77d99-9f15-4a66-a87d-c4a51ef30d19` - 查询 UUID 为 <u>f7c77d99-9f15-4a66-a87d-c4a51ef30d19</u> 的 Minecrat 账户信息

</details>

?> `/mc` 是此命令的别名. 你可以直接使用 `/mc` 来替换 `/minecraft`.

## /help
描述: 查看此命令列表

用法: `/help`

## /spelako
描述: 显示机器相关信息

用法: `/spelako`