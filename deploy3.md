?> 此文档适用于最新的 Spelako 3.x 版本 (包括 22w07a, 22w30a). 如果你仍想查看如何部署 Spelako 2.x, 请点击[这里](deploy2).
# 部署 Spelako
Spelako 由后端和前端组成. 后端为 [SpelakoCore](https://github.com/Spelako/SpelakoCore/), 是 Spelako 的核心代码, 包括了 Spelako 所有的命令及命令管理器. 前端可以是 [SpelakoCLI](https://github.com/Spelako/SpelakoCLI/), [SpelakoOne](https://github.com/Spelako/SpelakoOne/) 等, 负责连接后端, 并与不同的用户接口 (QQ 等) 对接.

```
SpelakoCore           用户
     |                  |
     |                  |
     |                  |
Spelako 前端 <-----> 用户接口
```

要部署 Spelako, 你需要:
1. 安装 PHP 8
2. 安装 SpelakoCore
3. 选择并安装一个 Spelako 前端, 并将其连接到 SpelakoCore

下文将详细引导你完成这些步骤.

?> 这里有一个基于本文档的[视频教程](https://www.bilibili.com/video/BV1cb4y1s77m), 可以指导你在 QQ 上搭建本机器人.

## 安装 PHP 8
Spelako 使用 PHP 编写. 你需要安装 PHP 8 才能运行 Spelako 前后端. 你不必为此安装一个完整的 Web 服务器环境.

### Windows 用户
首先, 前往[此处](https://windows.php.net/download)下载最新版本的 PHP 8. 请不要下载源代码 (source code), 而是下载 Zip 文件. 建议下载线程安全 (Thread Safe) 版.

然后, 将下载的 Zip 解压至任意目录, 并前往`控制面板 > 系统 > 高级 > 环境变量`, 选择 `Path`, 点击`编辑`, 并在列表中添加你将 Zip 解压到的目录 (如 `D:\PHP`), 然后应用更改.

接着, 在 `php.exe` 所在目录中 (即 Zip 文件解压到的目录), 将 `php.ini-development` 重命名为 `php.ini`. 并编辑此文件, 在文件底部添加这两行:

```ini
extension_dir="ext"
extension=openssl
```

最后, 打开 Windows PowerShell 或命令指示符, 输入 `php -v`. 如安装没有问题, 则会输出类似以下的内容:

```
PHP 8.1.2 (cli) (built: Jan 19 2022 10:13:52) (NTS Visual C++ 2019 x64)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
```

?> 如果你的 PHP 因为缺少运行时而无法运行, 请前往[此处](https://visualstudio.microsoft.com/zh-hans/downloads/#microsoft-visual-c-redistributable-for-visual-studio-2022)下载 Visual C++ 运行时.


### GNU/Linux 用户
我们认为, 如果你是 GNU/Linux 用户, 那么你已经有了不少的技术操作能力. 请自行通过搜索引擎了解如何使用你的发行版的包管理器安装 PHP 8. 你*可能*还需要安装适用于 PHP 8 的 curl 库.

## 安装 SpelakoCore
要安装 SpelakoCore, 只需从其 [Releases](https://github.com/Spelako/SpelakoCore/releases) 页面获取 SpelakoCore 的最新版本 (当前为 `22w30a`). 将下载的压缩文件解压至任意目录即可.

## 安装 Spelako 前端
Spelako 有不同的前端; 不同的前端用于不同的用户接口. 如果你希望在命令行界面直接使用 Spelako, 请安装 SpelakoCLI. 除此之外, 你也可以使用 SpelakoOne 对接 OneBot, 一个聊天机器人接口标准 (其中有 QQ 机器人框架支持).

### 安装 SpelakoCLI
SpelakoCLI 允许你在命令行界面中使用 Spelako.

要安装 SpelakoCLI, 首先需要从其 [Releases](https://github.com/Spelako/SpelakoCLI/releases) 页面获取 SpelakoCLI 的最新版本, 并将其解压在任意目录 (不一定需要和 SpelakoCore 在同一目录). 在 `config.json` 中修改你可能需要修改的部分 (例如你的 Hypixel API Key).

Windows 的启动脚本为 `start.bat`, GNU/Linux 的启动脚本为 `start.sh`. 请编辑适用于你的操作系统的启动脚本: 在 `--core` 参数填入 SpelakoCore 的路径, 使其指向 `SpelakoCore.php`.

运行 `start.bat` 或 `start.sh` 即可开始在命令行界面使用 Spelako.

### 安装 SpelakoOne
SpelakoOne 是 Spelako 的一个前端, 适用于 [OneBot](https://onebot.dev/) 实现. OneBot 不是一个具体的机器人框架, 而是一个聊天机器人应用接口标准. 理论上, SpelakoOne 可以与任何实现了 OneBot 标准的机器人框架对接.

有许多机器人框架实现了 OneBot 标准, 例如 [go-cqhttp](https://github.com/Mrs4s/go-cqhttp), [onebot-kotlin](https://github.com/yyuueexxiinngg/onebot-kotlin) 和 [oicq](https://github.com/takayama-lily/oicq). 这里以 go-cqhttp 为例, 将 Spelako 对接到 QQ 平台.

首先, 在 SpelakoOne 的 [Releases](https://github.com/Spelako/SpelakoOne/releases) 页面获取 SpelakoOne 的最新版本, 并将其解压在任意目录 (不一定需要和 SpelakoCore 在同一目录). 在 `config.json` 中修改你可能需要修改的部分 (例如你的 Hypixel API Key).

Windows 的启动脚本为 `start.bat`, GNU/Linux 的启动脚本为 `start.sh`. 请编辑适用于你的操作系统的启动脚本: 在 `--core` 参数填入 SpelakoCore 的路径, 使其指向 `SpelakoCore.php`.

然后, 获取适用于你的操作系统的 go-cqhttp 的最新 [Release](https://github.com/Mrs4s/go-cqhttp/releases). 在第一次启动时, 选择 HTTP 通信作为通信方式:

```
未找到配置文件，正在为您生成配置文件中！
请选择你需要的通信方式:
> 0: HTTP通信
> 1: 云函数服务
> 2: 正向 Websocket 通信
> 3: 反向 Websocket 通信
> 4: pprof 性能分析服务器
请输入你需要的编号(0-9)，可输入多个，同一编号也可输入多个(如: 233)
您的选择是:0
```

完成后, 在 go-cqhttp 将自动生成配置文件. 请打开 `config.yml`, 并填写你的 QQ 账号和密码:

```yaml
account: # 账号相关
  uin: 123456789 # QQ账号
  password: '' # 密码为空时使用扫码登录
```

同时, 在此文件的 `servers` 部分, 使用如下配置:

```yaml
servers:
  - http: # HTTP 通信设置
      address: 0.0.0.0:5700
      timeout: 15
      post:
      - url: 'http://127.0.0.1:5701'
```

?> 注意: 此文档撰写时, go-cqhttp 的最新版本为 v1.0.0-rc3. 如果后续版本有向下不兼容的变更, 请参照最新版本的 go-cqhttp 的配置格式来编辑此部分配置.

最后, 重新启动 go-cqhttp, 并在 SpelakoOne 目录运行 `start.bat` 或 `start.sh` 来启动 SpelakoOne, 即可将 Spelako 与此 OneBot 实现对接.
