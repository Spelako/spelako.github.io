!> 此文档已经过期! 该页面仅适用于 Spelako 2.x 版本. 适用于 Spelako 最新版本的此文档还待完成...

# 了解 Spelako 如何工作
本文章旨在帮助你了解 Spelako 的工作原理. 如果你想要对 Spelako 进行二次开发, 此文章会对你有帮助. 请确保你拥有 PHP 的进一步知识.

## 主类 (入口)
要使用 Spelako, 首先需要载入 Spelako 的主类 `Spelako.php`. Spelako 主类是一个静态类, 并且在仅载入主类时不会做任何事 (仅会引用 `utils` 目录下的工具类). 此时使用任何命令是无效的.

要载入所有可用的命令, 需要使用 `Spelako::loadCommands()` 方法. 此方法会引用 `commands` 目录下的所有文件, 此目录下的每个文件都是一个独立的命令 (类). 已经加载的命令的列表可以通过 `Spelako::getCommandList()` 方法获取.

在载入了所有可用的命令后, 使用 `Spelako::execute()` 方法即可执行指定的 Spelako 命令. 由于 Spelako 自带命令冷却功能, 所有带冷却命令的执行记录和冷却判断都会在主类完成. 用户执行带冷却命令的记录列表可以通过 `Spelako::getUserLastExecutions()` 获取.

主类的常量 `Spelako::CONFIG` 和 `Spelako::INFO` 是公开的, 它们分别存储了用户的配置和 Spelako 的相关信息. 它们可以直接在其他类被引用.

在正常初始化 Spelako 后, 项目结构应该是这样:
```
commands/
	HelpCommand.php
	HypixelCommand.php
	MinecraftCommand.php
	SpelakoCommand.php
	SyuuCommand.php
utils/
	FileSystem.php
	SpelakoUtils.php
Spelako.php
```

## Utils
目录 `utils` 下的 `SpelakoUtils.php` 和 `FileSystem.php` 会在 `Spelako.php` 的载入时一起被引用. 以下是这两个类的详细说明.

### SpelakoUtils
`SpelakoUtils` 类提供了在开发 Spelako 命令时可能会很有用的常用的方法, 例如 `SpelakoUtils::getURL()` 和 `SpelakoUtils::buildString()`.

`SpelakoUtils::getURL()` 是一个经过封装的 HTTP 请求发送函数. 此函数自带了缓存功能, 并可以自定义缓存有效期. 以下是它的使用示例:

```php
SpelakoUtils::getURL(
	'https://api.hypixel.net/player', // URL
	['key' => '123456', 'name' => 'Peaksol'], // 请求参数, 可选
	300 // 缓存有效期, 默认为 0 (秒)
);
```

`SpelakoUtils::buildString()` 是一个字符串构造函数. 你可以使用它方便地通过模板构造一个字符串. 以下是它的使用示例:

```php
SpelakoUtils::buildString(
	[ // 参数 1 提供的字符串数组将被使用换行符拼接为字符串
		'%1$s 的空岛战争统计信息:',
		'等级: %2$s | 硬币: %3$d | 助攻: %4$d',
		'击杀: %5$d | 死亡: %6$d | K/D: %7$.3f',
		'胜场: %8$d | 败场: %9$d | W/L: %10$.3f',
	],
	[ // 如果参数 2 指定, 其数组内容将用于替换参数 1 的占位符
		'[MVP+] Peaksol',
		'7⋆',
		169119,
		85,
		694,
		835,
		0.831138,
		59,
		830,
		0.071084
	]
);
```

SpelakoUtils 中的更多方法可以在源码中查看.

### FileSystem
`FileSystem` 类提供与文件系统交互的统一方式. Spelako 项目的所有地方都统一使用此方法来与访问文件系统.

FileSystem 中的所有方法可以在源码中查看.

## 命令
一条 Spelako 命令是一个存储在 `commands` 目录下的文件, 它的结构如下;

```php
class FooCommand {
	const USAGE = '/foo';
	const ALIASES = ['/foobar', '/bar'];
	const DESCRIPTION = '命令描述';
	const COOLDOWN = false;

	public static function execute(array $args, $isStaff) {
		return 'Foo';
	}
}
```

`USAGE` 是此命令在命令列表中显示的用法, 数组 `ALIASES` 用于声明此命令的别名, `DESCRIPTION` 是此命令在命令列表中显示的描述, `COOLDOWN` 用于声明此命令是否带冷却. 静态方法 `execute()` 在命令被使用时会被调用, 返回值为命令执行结果. 此方法可以带有两个可选的参数: 参数 1 为数组, 其第一个元素 (索引 0) 为命令全文, 后面的元素 (1, 2, 3...) 为数组的每个参数; 参数二为布尔型, 表示命令执行者是否为管理员.

### 创建一个命令
我们通过一个例子来说明如何创建一个命令.

现在我们需要一个 `/punishments` 命令, `/bans` 是这条命令的别名. 此命令用于`获取 Hypixel 封禁玩家数`, 并且有冷却时间. 我们将在 Hypixel API 的帮助下完成此功能. 以下是实现代码 (commands/PunishmentsCommand.php):

```php
<?php
class PunishmentsCommand {
	const USAGE = '/punishments';
	const ALIASES = ['/bans'];
	const DESCRIPTION = '获取 Hypixel 封禁玩家数';
	const COOLDOWN = true;

	public static function execute(array $args) {
		$src = SpelakoUtils::getURL('https://api.hypixel.net/punishmentstats', ['key' => Spelako::CONFIG['hypixel_api_key']], 60);
		$decoded = json_decode($src, true);
		switch($args[1]) {
			case 'watchdogs':
			case 'watchdog':
			case 'wd':
				return SpelakoUtils::buildString([
					'Hypixel 看门狗封禁玩家数:',
					'今日: %1$d',
					'总计: %2$d'
				], [
					$decoded['watchdog_rollingDaily'],
					$decoded['watchdog_total']
				]);
			case 'staff':
				return SpelakoUtils::buildString([
					'Hypixel 工作人员封禁玩家数:',
					'今日: %1$d',
					'总计: %2$d'
				], [
					$decoded['staff_rollingDaily'],
					$decoded['staff_total']
				]);
			default:
				return SpelakoUtils::buildString([
					'Hypixel 封禁玩家数:',
					'今日: %1$d',
					'总计: %2$d',
					'使用 /bans wd 或 /bans staff 查看详细信息.'
				], [
					$decoded['watchdog_rollingDaily'] + $decoded['staff_rollingDaily'],
					$decoded['watchdog_total'] + $decoded['staff_total'],
				]);
		}
	}
}
?>
```