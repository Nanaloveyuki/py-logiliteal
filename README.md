## 介绍
**特点**
- py-logiliteal 是一个简单的、现代化的、具有色彩的日志记录器
- py-logiliteal 提供了简单的配置、格式化、颜色、前缀等功能
- py-logiliteal 提供了简单的日志等级, 可以自定义日志等级, 日志格式, 日志颜色, 日志前缀等

**允许嵌入**
py-logiliteal 允许嵌入到其他项目中, 并根据需要自定义日志记录器
同时也支持pip安装
```bash
pip install logiliteal
```

**支持高可扩展的样式**
- 支持使用HEX十六进制颜色代码`<#ffffff>text</>`渲染颜色
- 支持使用占位符`{placeholder}`渲染变量(可手动扩展)
- 支持部分Html或Markdown语法(如`<b>text</b>`)
- 支持自定义日志格式和日志颜色

Html语法支持:
- `<b>text</b>` 加粗
- `<i>text</i>` 斜体
- `<u>text</u>` 下划线
- `<s>text</s>` 删除线
- `<c>` 清除颜色
- `<br>` 换行
- `</>` Html万用闭合

> **注意!Html嵌套可能会有问题, 不建议过多嵌套**

Markdown语法支持:
- `**text**` 加粗
- `*text*` 斜体
- `__text__` 下划线
- `~~text~~` 删除线
- `[text](url)` 链接

> **注意!Html和Markdown语法虽然可以同时使用,但是不保证所有语法都能正常工作, 建议只使用其中一种**

> **目前语法解析属于测试阶段,欢迎反馈或者提出Pr**
- 目前支持的Html标签: `<b>`, `<i>`, `<u>`, `<s>`, `<c>`, `<br>`, `</>`
- 目前支持的Markdown语法: `**`, `*`, `__`, `~~`, `[text](url)`
- 目前支持的变量:
    - `{asctime}` 对应日志完整时间(`config.asctime`)
    - `{time}` 对应日志简略时间(`config.time`)
    - `{weekday}` 对应日志星期(`config.weekday`)
    - `{date}` 对应日志日期(`config.date`)

**支持的Python版本**
- Python 3.13.5
- Python 3.13.4
- Python 3.13.3
- Python 3.13.2
- Python 3.13.1
- Python 3.13.0
(低版本未经测试, 不保证兼容性)

## 安装
暂无安装包, 请使用release发布版或直接clone代码到本地/使用pip安装
```bash
pip install logiliteal
```

## 文档
暂无文档, 请查看代码注释

## 示例
```python
# 导入
from logiliteal import logger, Logger
# 或 import logiliteal(不推荐)

# 实例化(不推荐: 会造成多实例问题)
# 推荐直接使用 logger 而不是 Logger()
# logger = Logger()

#使用功能
logger.info("这是一条信息日志")

logger.warn("这是一条带有前缀的警告日志", prefix="114514")

logger.critical("这是一条带有前缀并且日志等级不同的严重错误日志", prefix="114514", level=55)

# 自定义配置
from logiliteal import set_config, get_config
# 读取配置
print(get_config("console_format"))
# 默认会输出时间、日志等级、日志前缀、日志消息
# 时间格式: {asctime}
# 日志等级: {levelname}
# 日志前缀: {prefix}
# 日志消息: {message}
# 输出: "{asctime} {levelname} | {prefix}{message}"

# 更改配置
set_config("console_format", "{asctime} {levelname} | {message}")

# 如果遇到函数名冲突, 可以用别名代替:
log_set_config = set_config
log_set_config("console_format", "{asctime} {levelname} | {message}")
```