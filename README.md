# memoriass AstrBot 插件源

这是 `memoriass` 的个人 AstrBot 插件源。插件市场数据由本仓库维护的公开仓库清单生成。

## 插件源地址

在 AstrBot WebUI 的插件市场中添加以下自定义插件源：

```text
https://raw.githubusercontent.com/memoriass/astrbot-plugin-source/main/plugins.json
```

AstrBot 会自动读取对应的 MD5 文件：

```text
https://raw.githubusercontent.com/memoriass/astrbot-plugin-source/main/plugins-md5.json
```

## 手动更新

重新生成插件源：

```powershell
python scripts/build_registry.py
```

然后提交并推送：

```powershell
git add plugins.json plugins-md5.json repositories.json
git commit -m "Update plugin registry"
git push
```

## 自动更新

GitHub Actions 每 6 小时刷新一次 `repositories.json` 中列出的插件仓库。

只有 `plugins.json` 或 `plugins-md5.json` 发生变化时，Action 才会自动提交。

也可以在 GitHub 页面手动触发：

```text
Actions -> Update AstrBot Plugin Registry -> Run workflow
```

## 收录插件

生成脚本只会处理 `repositories.json` 中列出的仓库，不会自动扫描账号下的所有公开仓库。

新增插件时，在 `repositories.json` 中添加公开仓库：

```json
{
  "owner": "memoriass",
  "name": "astrbot_plugin_example"
}
```

提交后可以手动运行 workflow，也可以等待下一次定时刷新。

插件仓库需要在根目录提供 AstrBot 可识别的 `metadata.yaml`。
