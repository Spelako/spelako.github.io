# 更新日志
此页面包含了 Spelako 的历次更新的内容.

> ### Spelako 1.5.0
更新时间: 2021/2/15
- 修复了 Skyblock 拍卖行查询失败的问题.
- 清除了 /virus 命令移除后的残留.
- 移除了 /server 指令.

> ### Spelako 1.4.0
更新时间: 2021/1/1
- 优化了代码结构.
- 增加了更多查询项于 /syuu lb.
- 移除了 /virus 指令.

> ### Spelako 1.3.1
更新时间: 2020/7/25
- 修复了 Skyblock 物品拍卖查询的一些小问题.

> ### Spelako 1.3.0
更新时间: 2020/7/23
- 新增了 Skyblock 拍卖行查询(指令: /hypixel <玩家> sba)
- 修改了 Skyblock 技能查询方式(指令: /hypixel <玩家> sbs)
- 修改了部分消息格式
- 内部优化(Spelako API)
- 移除了部分从未被使用的功能

> ### Spelako 1.2.0
更新时间: 2020/7/11
- 新增了 Hypixel Skyblock 技能查询功能.<br>指令: /hypixel <玩家> sb

> ### Spelako 1.1.0
更新时间: 2020/6/15
- 新增了 Syuu 相关查询功能, 支持查询决斗排行榜(命令: /syuu lb)以及玩家统计数据(命令: /syuu user).
- 注意: 由于 Syuu.Net 没有公开的 API, 此命令的部分功能是基于网页爬虫来运行的. 这可能导致此命令拥有缓慢的响应速度或未知的漏洞.

> ### Spelako 1.0.0
更新时间: 2020/5/8
- 对代码结构进行大幅优化
- **Spelako 正式开源于 GitHub**

> ### Spelako 1.0.0-pre2
更新时间: 2020/4/18
- 修改了 /hypixel 主指令的消息提示.
- 修复了 pre1 中小几率查询失败的问题.
- 移除了部分调试信息.
- 更新了适用于机器人管理员的存储情况统计.

> ### Spelako 1.0.0-pre1
更新时间: 2020/4/17
- 添加了缓存功能于 Hypixel 信息查询, 以优化获取相同玩家的不同分类下的统计信息时的响应速度, 同时避免了短时间内向 Hypixel API 重复发送相同的请求.
- 修复了特殊 Hypixel Rank 的识别问题.
- 修改了部分消息提示.

> ### Spelako 20w15b
更新时间: 2020/4/12
- 修复了 Hypixel 远古玩家的称号显示为 [NONE] 的问题.
- 修复了 /virus 指令的数据不及时的问题 - API 得到了更换.
- 修复了为普通用户自动补全管理员指令的问题.

> ### Spelako 20w15a
更新时间: 2020/4/6
- 添加了玩家上次退出时间的显示.
- 添加了玩家当前在线状态的显示, 同时会显示在线时长.
- 修复了时差问题 (将时区更正为北京时间, 东八区).
- 修复了显示部分玩家信息时出现的 "致命的错误" (如 hypixel).
- 修复了多余空格的识别问题, 多个空格将识别为一个空格.

?>Spelako 在此之前处于快速流转状态, 没有对更改进行记录.