# 部署
本指南旨在帮助你自行安装并运行 Spelako. 请确保你拥有 PHP 的基础知识.

**注意: 要安装和运行 Spelako, 你至少需要 PHP 8 运行环境.**

## 安装 Spelako
以下简单的步骤将引导你完成 Spelako 的安装:
1. 获取 Spelako 后端的最新 [Release](https://github.com/Spelako/Spelako/releases).
2. 使用代码编辑器打开 `Spelako.php`, 并完成以下配置:

```php
const CONFIG = [
	'hypixel_api_key' => 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx', // Hypixel API Key, 用于 Hypixel 统计信息查询
	'staffs' => ['123456789', '987654321'], // 管理员列表, 使用逗号分隔
	'cooldown' => 5, // 命令冷却, 适用于需要网络请求的命令, 单位为秒
	'timezone_offset' => 28800, // 当前时区相对于 UTC 的偏移时间, 单位为秒
];
```

## 运行 Spelako
要运行 Spelako, 你需要在你的 PHP 项目中引用 `Spelako.php`, 并初始化 Spelako:

```php
require_once('Spelako.php');
Spelako::loadCommands();
```

在这之后, 你将使用此方法来在 Spelako 中运行一条命令:

```php
Spelako::execute(string $command, string $user): string
```

参数 `$command` 为传入的命令, 以 `/` 开头. 参数 `$user` 为执行者的用户 ID, 用于 Spelako 区分不用用户. 方法返回值为执行结果 (字符串).

### 附带的示例
在你获取的 Spelako 后端项目中, 附带了实现上文的简单示例. 以下是关于它们的进一步说明.

#### Spelako CLI
位于此项目中的 `cli.php` 允许你在命令行界面中直接使用 Spelako. 这对于临时的测试可能很有用.

要使用它, 你只需要在你的操作系统的终端运行以下的命令:

```
php cli.php
```

如果一切正常, 你将成功进入 Spelako CLI. 你可以在其中运行 Spelako 命令, 或使用 `^C` 退出.

#### Spelako API
位于此项目中的 `api.php` 允许你以 HTTP API 的形式调用 Spelako. 这对于使用其他语言而不是 PHP 的用户十分方便. 用户可以在自己的程序中通过 HTTP 请求来直接获取 Spelako 的响应.

**要使用它, 你需要先将 Spelako 部署在支持 PHP 的 Web 服务器上.**

然后, 你便可以向 `/api.php` 发送 GET 请求来获取响应. 请求需要附带以下参数:

| 参数名 | 注释 |
| - | - |
| command | 传入的命令, 以 `/` 开头 |
| user | 执行者的用户 ID, 用于 Spelako 区分不用用户 |

请求 URL 示例:
- http://localhost/api.php?command=/help&user=1244050218
- http://127.0.0.1/api.php?command=/spelako&user=guest

如果请求 URL 无误, 服务器将响应如下 JSON 文本:

| 键名 | 注释 |
| - | - |
| success | 请求是否成功 (bool) |
| response | 响应文本 (string 或 null) |