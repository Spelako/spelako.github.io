# 了解 Spelako 运作方式
Spelako 是一个开源的项目, 在开放源代码的同时, 我们也会在这里解释其运作方式.<br>
阅读此文档需要一定的技术含量.

![Spelako项目结构图](https://s1.ax1x.com/2020/07/12/U3mnEV.png)

## Spelako API
由于 Spelako 运行于多个平台, 为了让不同的平台调用同一个接口, Spelako 采用网络请求(GET)作为统一的接口调用方式.

### 部署
Spelako API 使用 PHP 编写, 可部署在本地或远程 Web 服务器中.

要部署 Spelako API, 你需要做的就是把 [Spelako/Spelako](https://github.com/Spelako/Spelako) 仓库下的所有文件上传到 Web 服务器的根目录或任意目录.

上传文件之后, 请使用代码编辑器打开 `Commands.php`, 找到
```php
$apiKey = '[在此输入 Hypixel API Key]';
```
这一行, 并在引号内填入你的 Hypixel API Key , 然后保存.

### 调用
#### 请求
假设 API 被部署在了 Web 服务器的根目录. 你需要向根目录(`/`)发送 GET 请求, 并附带这些参数:

| 参数名 | 注释 |
| - | - |
| msg | 消息内容 |
| fromAccount | 消息发出者(用于区分不同的用户) |

一个正确的请求 URL 可以是这样:
```
http://localhost/?fromAccount=1244050218&msg=/help
```

这表示用户 `1244050218` 向 Spelako 发送了 `/help` 指令.

#### 回应
向 API 发送请求后, API 会直接返回指令运行结果的**纯文本**(而不是 JSON), 如果指令无效, 则返回空.