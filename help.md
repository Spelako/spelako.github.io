# 指令列表
这里列出了 Spelako 一般用户可用的所有指令.

使用 `<` 和 `>` 包围的为必填参数, 使用 `[` 和 `]` 包围的为可选参数.

## /hypixel
描述: 获取指定玩家的 Hypixel 信息<br>
用法: `/hypixel <玩家> [分类]`<br>
示例:
- `/hypixel Peaksol` - 查询 Peaksol 的基本信息
- `/hypixel iTMG sw` - 查询 iTMG 的 Skywars 统计数据
- `/hypixel 9gh sb` - 查询 9gh 的 SkyBlock 技能信息
- `/hypixel hypixel g` - 查询 hypixel 的公会信息

?> **分类**可以是下列之一:<br>- bedwars, bw<br>- skywars, sw<br>- uhc<br>- megawalls, mw<br>- blitzsg, bsg, hungergames<br>- guild, g<br>- skyblock, sb

## /syuu
描述: 获取 SyuuNet 的玩家信息或排行榜<br>
用法: `/syuu user <玩家>` 或 `/syuu lb <排行榜分类>`<br>
示例:
- `/syuu user Reviaol` - 查询 Reviaol 的统计数据
- `/syuu lb s2p2` - 查询 Sharp2Prot2 排行榜

?> **排行榜分类**可以是下列之一:<br>- sharp2prot2, s2p2<br>- archer, bow<br>- nodelay, combo<br>- builduhc, buhc<br>- sumo<br>- spleef

## /mojang
描述: 获取指定玩家的 Mojang 账号信息<br>
用法: `/mojang <玩家/UUID>`<br>
示例:
- `/mojang Peaksol` - 使用 ID 查询 Mojang 账号信息
- `/mojang 2e951afe18f241e1ae021667f39e4f5b` - 使用 UUID 查询 Mojang 账号信息

## /virus
描述: 查询新型肺炎的实时动态<br>
用法: `/virus [省份]`<br>
示例:
- `/virus 湖北` - 查询湖北省疫情
- `/virus 美国` - 查询美国疫情

## /server
?> 此命令将在未来可能会被移除

描述: 获取指定地址的 Minecraft 服务器信息<br>
用法: `/server <地址> [端口]`<br>
示例:
- `/server mc.hypixel.net` - 查询 mc.hypixel.net 服务器状态
- `/server 11.22.33.44 25566` - 查询 11.22.33.44:25565 服务器状态

## /help
描述: 查看此指令列表<br>
用法: `/help`

## /spelako
描述: 显示机器相关信息<br>
用法: `/spelako`