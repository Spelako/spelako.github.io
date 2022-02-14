# 部署 Spelako
SpelakoOne 是 Spelako 的一个前端, 适用于 OneBot 实现. OneBot 不是一个具体的机器人框架, 而是一个聊天机器人应用接口标准. 理论上, SpelakoOne 可以与任何实现了 OneBot 标准的机器人框架对接.

```
SpelakoCore        聊天平台
     |                |
     |                |
     |                |
 SpelakoOne <---> OneBot 实现
```

## 安装 SpelakoOne
获取 SpelakoOne 的最新 [Release](https://github.com/Spelako/SpelakoOne/releases), 并在 `config.json` 中进行相关配置.

配置完成后, 要启动 SpelakoOne, 只需在终端使用 PHP 运行 `SpelakoOne.php`, 并附带如下启动参数:
- `--core="填写 SpelakoCore.php 的位置"`
- `--config="填写 config.json 的位置"`
- `--host="填写 OneBot 实现的 API 地址"` (此参数在安装完 OneBot 实现后再填写)

你也可以使用当前目录下现成的启动脚本来启动 SpelakoOne. 只需在 Windows 中运行 `start.bat` 或在 GNU/Linux 中运行 `start.sh`.

## 安装一个 OneBot 实现
有许多机器人框架实现了 OneBot 标准, 例如 [go-cqhttp](https://github.com/Mrs4s/go-cqhttp), [onebot-kotlin](https://github.com/yyuueexxiinngg/onebot-kotlin) 和 [oicq](https://github.com/takayama-lily/oicq). 这里以 go-cqhttp 为例, 将 Spelako 对接到 QQ 平台.

获取适用于你的操作系统的 go-cqhttp 的最新 [Release](https://github.com/Mrs4s/go-cqhttp/releases). 在第一次启动时, 选择 HTTP 通信作为通信方式:

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

完成后, 在 go-cqhttp 目录下的 `config.yml` 中配置 QQ 账号和密码:

```yaml
account: # 账号相关
  uin: 2033744775 # QQ账号
  password: '' # 密码为空时使用扫码登录
```

同时, 在此文件的 `servers` 部分, 进行如下配置:

```yaml
servers:
  - http:
    host: 127.0.0.1
    port: 5700
    timeout: 15
    post:
     - url: 'http://127.0.0.1:5701'
```
然后, 再次启动