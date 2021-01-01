# 部署 Spelako 运行环境
本指南旨在帮助你自行部署并运行 Spelako. 请确保你拥有 PHP 和 Web 的基础知识.

如果你只希望在命令行使用 Spelako, 你可以查看[如何使用 Spelako CLI](##-如何使用-Spelako-CLI); 如果你希望将 Spelako 部署为网络 API 并被其他应用调用, 你可以查看[如何使用 Spelako API](##-如何使用-Spelako-API).

## 如何使用 Spelako CLI
**需求:** PHP 5.6+

要使用 Spelako CLI, 首先需要将 [Spelako/Spelako](https://github.com/Spelako/Spelako) 仓库的所有文件保存至本地.

然后, 请使用代码编辑器打开 `Main.php`, 找到
```php
$apiKey = '[在此输入 Hypixel API Key]';
```
这一行, 在引号内填入你的 Hypixel API Key, 并保存.

最后, 在命令行运行:
```winbatch
php cli.php
```
如果一切正常, 你将成功进入 Spelako CLI. 你可以在其中运行 Spelako 命令, 或按下 `Ctrl + C` 退出.

## 如何使用 Spelako API
**需求:** PHP 5.6+, 已配置 PHP 支持的 Web 服务器

要部署 Spelako API, 首先需要将 [Spelako/Spelako](https://github.com/Spelako/Spelako) 仓库下的所有文件上传至本地或远程 Web 服务器中.

然后, 请使用代码编辑器打开 `Main.php`, 找到
```php
$apiKey = '[在此输入 Hypixel API Key]';
```
这一行, 在引号内填入你的 Hypixel API Key, 并保存.

一切完成之后, 你将可以调用 Spelako API.

### 调用方式
你需要向 `/api.php` 发送 GET 请求, 并附带这些参数:

| 参数名 | 注释 |
| - | - |
| plain | 是否响应纯文本 (`true` 或 `false`) |
| id | 消息发出者, 用于区分不同的用户 |
| msg | 消息内容 |

请求 URL 示例:
```
http://localhost/api.php?plain=trueid=1244050218&msg=/help
http://127.0.0.1/api.php?plain=falseid=user3&msg=/spelako
```

如果请求 URL 无误, 服务器将响应如下 JSON 文本:
| 键名 | 注释 |
| - | - |
| success | 请求是否成功 (`true` 或 `false`) |
| response | 响应文本 |

如果你在请求时使用了 `plain=true`, API 则会直接响应纯文本而不是 JSON.