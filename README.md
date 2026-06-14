# memoriass AstrBot 插件源

[![自动更新插件源](https://github.com/memoriass/astrbot-plugin-source/actions/workflows/update-registry.yml/badge.svg)](https://github.com/memoriass/astrbot-plugin-source/actions/workflows/update-registry.yml)

这是 `memoriass` 维护的个人 AstrBot 插件源。插件市场数据由本仓库中的 `repositories.json` 生成，只收录该文件明确列出的公开插件仓库。

## 插件源地址

在 AstrBot WebUI 的插件市场中添加以下自定义插件源：

```text
https://raw.githubusercontent.com/memoriass/astrbot-plugin-source/main/plugins.json
```

对应的 MD5 文件地址为：

```text
https://raw.githubusercontent.com/memoriass/astrbot-plugin-source/main/plugins-md5.json
```

AstrBot 会根据插件源数据读取插件仓库信息，并使用 MD5 文件判断插件源缓存是否需要刷新。

## 已收录插件

当前插件源只从 `repositories.json` 中列出的仓库生成：

```json
[
  {
    "owner": "memoriass",
    "name": "astrbot_plugin_ani_rss"
  },
  {
    "owner": "memoriass",
    "name": "astrbot_plugin_ncqq_manager"
  },
  {
    "owner": "memoriass",
    "name": "astrbot_plugin_bilibili_push"
  },
  {
    "owner": "memoriass",
    "name": "astrbot_plugin_webhook_push"
  }
]
```

本项目不会自动扫描账号下的所有公开仓库，避免无关仓库被误收录。

## 提交新插件

如果希望将插件提交到这个插件源，请确保插件仓库满足以下条件：

- 仓库必须是公开仓库。
- 仓库根目录需要包含 AstrBot 可识别的 `metadata.yaml`。
- 插件仓库地址应长期可访问。
- 插件名称、描述、作者、版本等信息应在 `metadata.yaml` 中维护。

提交方式：

1. Fork 本仓库。
2. 修改 `repositories.json`，新增你的插件仓库：

```json
{
  "owner": "your-github-name",
  "name": "your-astrbot-plugin-repo"
}
```

3. 提交 Pull Request。

合并后，插件源会在下一次 GitHub Actions 运行时自动重新生成。

## 插件更新说明

插件的小版本更新、描述调整、图标或 logo 调整，通常只需要更新插件自己的仓库。

本插件源项目只在以下情况需要改动：

- 新增插件仓库。
- 移除插件仓库。
- 修改已收录插件仓库的 `owner` 或 `name`。
- 调整插件源生成脚本或工作流逻辑。

如果插件仓库中的 `metadata.yaml`、README、logo 等内容发生变化，GitHub Actions 会定期重新生成 `plugins.json` 和 `plugins-md5.json`。也可以由维护者手动触发更新。

## 自动更新

本仓库使用 GitHub Actions 自动更新插件源：

- 每 6 小时运行一次。
- 支持在 GitHub 页面手动触发。
- 只有 `plugins.json` 或 `plugins-md5.json` 发生变化时才会自动提交。

手动触发路径：

```text
Actions -> 自动更新插件源 / Update AstrBot Plugin Registry -> Run workflow
```

工作流页面：

```text
https://github.com/memoriass/astrbot-plugin-source/actions/workflows/update-registry.yml
```

## 本地生成

维护者可以在本地手动重新生成插件源：

```powershell
python scripts/build_registry.py
```

然后提交生成结果：

```powershell
git add plugins.json plugins-md5.json repositories.json
git commit -m "Update plugin registry"
git push
```
