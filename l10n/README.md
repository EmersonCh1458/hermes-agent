# Hermes L10n — CLI/TUI 本地化扩展

本目录包含 Hermes Agent CLI 和 TUI 界面的中文本地化文件。

## 安装

```bash
# 1. 复制翻译文件到用户目录
cp -r locale ~/.hermes/locale

# 2. 设置语言（写入 config.yaml）
hermes config set display.language zh

# 3. 重启 Hermes
hermes
```

## 文件说明

| 文件 | 说明 |
|------|------|
| `locale/zh.yaml` | CLI + Banner 翻译（119 key） |
| `locale/commands_zh.json` | 命令描述翻译（72 内置命令） |
| `locale/tips_zh.txt` | 启动提示翻译（290 条） |

## 源码改动

本功能在 Hermes 核心源码中做了以下微调（不破坏现有功能）：

1. **agent/i18n.py** — 添加 `~/.hermes/locale/` 用户语言包覆盖层
2. **cli.py** — 欢迎语和提示文本走 `_t()` 调用
3. **hermes_cli/banner.py** — 标题/描述走 `_t()` 调用
4. **hermes_cli/tips.py** — 支持外部 `tips_<lang>.txt` 文件
5. **hermes_cli/commands.py** — 自动补全支持外部 `commands_<lang>.json`
6. **hermes_cli/cli_commands_mixin.py** — 新增 `/lang` 命令
