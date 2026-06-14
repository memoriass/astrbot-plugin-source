# memoriass AstrBot Plugin Source

Personal AstrBot plugin registry generated from selected public GitHub repositories.

## Source URL

After this repository is pushed to GitHub, add this URL in AstrBot WebUI:

```text
https://raw.githubusercontent.com/memoriass/astrbot-plugin-source/main/plugins.json
```

AstrBot will automatically look for the matching MD5 file at:

```text
https://raw.githubusercontent.com/memoriass/astrbot-plugin-source/main/plugins-md5.json
```

## Update

Regenerate the registry:

```powershell
python scripts/build_registry.py
```

Then commit and push:

```powershell
git add plugins.json plugins-md5.json README.md scripts/build_registry.py
git commit -m "Update plugin registry"
git push
```

## Automation

GitHub Actions refreshes the listed repositories every 6 hours and only commits when
`plugins.json` or `plugins-md5.json` changes.

You can also trigger it manually from:

```text
Actions -> Update AstrBot Plugin Registry -> Run workflow
```

## Included Repositories

The generator only includes repositories listed in `repositories.json`.

To add a new plugin, add its public repository to `repositories.json`:

```json
{
  "owner": "memoriass",
  "name": "astrbot_plugin_example"
}
```

Then run the workflow manually or wait for the next scheduled run.
