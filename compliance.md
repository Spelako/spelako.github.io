# Spelako 再分发合规性指南
Spelako 是以 GNU AGPLv3 发布的软件. 因此, 在向他方分发其副本或将其部署为网络服务以供他方使用时, 需遵循 AGPLv3 许可证的条款.

考虑到许多用户难以理解 AGPL 的原文, 我们编写了此指南, 以指导你合规地使用和分发 Spelako 软件 (下称 "本软件").

## 个人使用
在本软件仅为你个人所用时, 你可以自由地使用和修改本软件而不受任何限制. "仅为你个人所用" 是指以任何方式与本软件交互的用户只有你本人.

如果你将本软件或其修改版分发至他方, 或者将本软件或其修改版部署为网络服务以供他方使用, 那么你还须遵循以下的规定.

## 分发未修改版
如果你有一份未修改过的本软件, 那么在向他方分发本软件 (或允许他方与之交互) 时, 你必须确保本软件的版权信息和许可证声明未被抹除或篡改. 具体而言, 你必须确保用户可以正常通过 `/spelako` 命令来获取本软件正确的相关信息.

## 分发已修改版
若你有一份经过修改的本软件, 那么在向他方分发本软件 (或允许他方与之交互) 时, 你必须同样以 AGPLv3 授权本软件, 并以上节所述的方式确保本软件的版权信息和许可证声明未被抹除或篡改.

除此之外, 你还必须提供一种尽可能简单的方式, 使该修改版的用户可以免费获取该版本的源代码. 一种建议的方式是, 将该版本的源代码上传至一个代码托管平台或文件分享平台以供下载.

你可以为你所做的修改添加作者信息. 在用户界面层面, 我们建议你在 `/spelako` 命令的原有输出之后添加你的修改版的信息, 并将你的修改版的名称 (如果存在) 添加为 `/spelako` 命令的别名 (见示例 A). 另一个可选的方案是, 新建一个命令, 使其输出你的修改版的信息, 并指出可使用 `/spelako` 命令来获取上游信息 (见示例 B).

| 示例 A | 示例 B |
| - | - |
| <div class=chat-box><div class=chat-title>聊天记录</div><div class=chat-contents><div class=chat-msg-sent><div>/foobar</div></div><div class=chat-msg-recv>SpelakoCore 22w30a (2022/7/30)<br>本程序是自由软件, 以 AGPLv3 许可证发布.<br>欲获取帮助文档, 源代码, 作者及版权信息等,<br>请访问 &lt;https://spelako.github.io&gt;.<br><br>FooBar Bot 1.0.0 (2022/9/1)<br>本修改版由 Coder34 以 AGPLv3 发布.<br>源代码: https://github.com/coder34/foobar</div><div class=chat-msg-sent><div>/spelako</div></div><div class=chat-msg-recv>SpelakoCore 22w30a (2022/7/30)<br>本程序是自由软件, 以 AGPLv3 许可证发布.<br>欲获取帮助文档, 源代码, 作者及版权信息等,<br>请访问 &lt;https://spelako.github.io&gt;.<br><br>FooBar Bot 1.0.0 (2022/9/1)<br>本修改版由 Coder34 以 AGPLv3 发布.<br>源代码: https://github.com/coder34/foobar</div></div></div> | <div class=chat-box><div class=chat-title>聊天记录</div><div class=chat-contents><div class=chat-msg-sent><div>/foobar</div></div><div class=chat-msg-recv>FooBar Bot 1.0.0 (2022/9/1)<br>本程序由 Coder34 以 AGPLv3 发布.<br>源代码: https://github.com/coder34/foobar<br>本程序基于 Spelako. 使用 /spelako 以获取上游信息.</div><div class=chat-msg-sent><div>/spelako</div></div><div class=chat-msg-recv>SpelakoCore 22w30a (2022/7/30)<br>本程序是自由软件, 以 AGPLv3 许可证发布.<br>欲获取帮助文档, 源代码, 作者及版权信息等,<br>请访问 &lt;https://spelako.github.io&gt;.</div></div></div> |
		

在源代码层面, 建议你在你修改过的文件的顶部注释处添加你的版权信息 (见示例 C). 你还须确保修改版的源代码中包含了一份 AGPLv3 的副本 (位于 LICENSE 文件), 并在 README 中说明本修改版以 AGPLv3 发布. 如果你不确定如何这么做, 请参考 SpelakoCore 源代码中的 LICENSE 文件和 README.md 文件中的 "许可证" 声明.

```diff
/*
 * Copyright (C) 2020-2022 Spelako Project
+ * Copyright (C) 2022 Coder34
 * 
 * This file is part of SpelakoCore.
 * Permission is granted to use, modify and/or distribute this program 
 * under the terms of the GNU Affero General Public License version 3.
 * You should have received a copy of the license along with this program.
 * If not, see <https://www.gnu.org/licenses/agpl-3.0.html>.
 * 
 * 此文件是 SpelakoCore 的一部分.
 * 在 GNU Affero 通用公共许可证第三版的约束下,
 * 你有权使用, 修改, 复制和/或传播该软件.
 * 你理当随同本程序获得了此许可证的副本.
 * 如果没有, 请查阅 <https://www.gnu.org/licenses/agpl-3.0.html>.
 * 
 */
 ```